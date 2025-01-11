## NodeJs and Docker App 1



### With Docker

#### To start the application

Step 1: Create docker network

    docker network create mongo-network 

Step 2: start mongodb 

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

Step 3: start mongo-express
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

_NOTE: creating docker-network in optional. You can start both containers in a default network. In this case, just emit `--net` flag in `docker run` command_

Step 4: open mongo-express from browser

    http://localhost:8081
![Screenshot 2025-01-11 233242](https://github.com/user-attachments/assets/3af6a723-3daa-4c87-996a-69ad2e41e66b)

Step 5: create `user-account` _db_ and `users` _collection_ in mongo-express
![Screenshot 2025-01-11 233254](https://github.com/user-attachments/assets/2807a90c-5079-4cc0-9b13-bf296caba984)
![Screenshot 2025-01-11 233308](https://github.com/user-attachments/assets/0e2ac16a-d8be-4bd0-906b-4511665bf236)

Step 6: Start your nodejs application locally - go to `app` directory of project 

    npm install 
    node server.js
    
Step 7: Access you nodejs application UI from browser

    http://localhost:3000
![Screenshot 2025-01-11 233029](https://github.com/user-attachments/assets/101db60a-1601-49a2-9bab-61cf44f230f7)


    

### With Docker Compose

#### To start the application

Step 1: start mongodb and mongo-express

    docker-compose -f docker-compose.yaml up
    
_You can access the mongo-express under localhost:8080 from your browser_

![Screenshot 2025-01-11 233228](https://github.com/user-attachments/assets/334bd3a3-7ee8-4865-b5a8-a8e33c15d373)

Step 2: in mongo-express UI - create a new database "my-db"
![Screenshot 2025-01-11 233242](https://github.com/user-attachments/assets/dd0c6b65-ce02-462e-9119-f360d239a87b)

Step 3: in mongo-express UI - create a new collection "users" in the database "my-db"       
    ![Screenshot 2025-01-11 233254](https://github.com/user-attachments/assets/8618de99-a3c0-453b-b0da-32206d651da6)
![Screenshot 2025-01-11 233308](https://github.com/user-attachments/assets/38fbca51-63d2-4f38-976e-c3854c0152ce)

Step 4: start node server 

    npm install
    node server.js
    
Step 5: access the nodejs application from browser 

    http://localhost:3000
![Screenshot 2025-01-11 233029](https://github.com/user-attachments/assets/101db60a-1601-49a2-9bab-61cf44f230f7)

#### To build a docker image from the application

    docker build -t my-app:1.0 .       
    
The dot "." at the end of the command denotes location of the Dockerfile.
