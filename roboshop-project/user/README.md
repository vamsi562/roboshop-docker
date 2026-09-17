# docker commands
docker build -t user:v1 .
docker run -d --name catalogue --network roboshop user:v1
docker exec -it user bash

# health check
- *curl http://localhost:8080/health*