# docker commands
docker build -t cart:v1 .
docker run -d --name cart --network roboshop cart:v1
docker exec -it cart bash

# health check
- *curl http://localhost:8080/health*