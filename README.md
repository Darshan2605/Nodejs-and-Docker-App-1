## NodeJs and Docker App 1


    

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
