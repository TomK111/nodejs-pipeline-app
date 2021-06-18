# commands

## create docker network
sudo docker network create mongo-network

## start mongodb
sudo docker run -d \
-p 27017:27017 \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=password \
--net mongo-network \
--name mongodb \
mongo

## start mongo-express
sudo docker run -d \
-p 8081:8081 \
-e ME_CONFIG_MONGODB_ROOT_USERNAME=admin \
-e ME_CONFIG_MONGODB_ROOT_PASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongodb
--net mongo-network \
--name mongo-express \
mongo-express