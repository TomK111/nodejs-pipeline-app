## Node.js App

This app shows a simple user profile app set up using 
- Vanilla JavaScript and CSS
- Node.js backend with Express module
- MongoDB for data storage

All components are docker-based

<hr/>

### Starting App with Docker

<i>Step 1: Create docker network</i>

    docker network create mongo-network

<i>Step 2: start mongodb</i>

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

<i>Step 3: start mongo-express</i>
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

NOTE: creating docker-network in optional. You can start both containers in a default network. In this case, just emit `--net` flag in `docker run` command_

<i>Step 4: open mongo-express from browser</i>

    http://localhost:8081

<i>Step 5: create `user-account` _db_ and `users` _collection_ in mongo-express</i>

<i>Step 6: Start your nodejs application locally - go to `app` directory of project</i> 

    cd app
    npm install 
    node server.js
    
<i>Step 7: Access you nodejs application UI from browser</i>

    http://localhost:3000
    
<hr/>

### Starting App with Docker-Compose

<i>Step 1: start mongodb and mongo-express</i>

    docker-compose -f docker-compose.yaml up
    
You can access the mongo-express under localhost:8080 from your browser
    
<i>Step 2: in mongo-express UI - create a new database "my-db"</i>

<i>Step 3: in mongo-express UI - create a new collection "users" in the database "my-db"</i>       
    
<i>Step 4: start node server</i> 

    cd app
    npm install
    node server.js
    
<i>Step 5: access the nodejs application from browser</i> 

    http://localhost:3000

#### To build a docker image from the application

    docker build -t my-app:1.0 .       
    
The dot "." at the end of the command denotes location of the Dockerfile.
