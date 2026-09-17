# docker commands
docker build -t catalogue:v1 .
docker run -d --name catalogue --network roboshop catalogue:v1
docker exec -it catalogue bash

# health check
- *http://localhost:8080/health*