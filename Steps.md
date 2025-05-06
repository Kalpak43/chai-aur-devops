### Setup network:

```
docker network create -d bridge chai-fullstack-net
```

### Run Redis:

``` 
docker run -d -p 6379:6379 --rm -v redis:/data --network chai-fullstack-net --name chai-fullstack-redis redis --requirepass "Test#123" 
```

### Run Mongodb:

```
docker run -d --rm -p 27017:27017 -v mongodb:/data/db --name chai-fullstack-mongodb --network chai-fullstack-net -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=admin123 mongo
```

### Create Dockerfile for server

### Build the image -> Run the container:

```
docker run -d --rm -p 8080:8080 --name chai-fullstack-server --network chai-fullstack-net -v $(pwd)/backend:/app chai-fullstack-server-image
```

### Create Dockerfile for client

### Build the image -> Run the container:

```
docker run -d --rm -p 5173:5173 --name chai-fullstack-client --network chai-fullstack-net -v $(pwd)/frontend:/app chai-fullstack-client-image
```