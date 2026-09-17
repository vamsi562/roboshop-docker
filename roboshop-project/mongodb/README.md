# docker commands
docker build -t mongo:v1 .
docker run -d --name mongo mongo:v1
docker exec -it mongo bash

# mongodb commands
- mongosh
- show dbs
- use catalogue
- show collections
- db.products.find()