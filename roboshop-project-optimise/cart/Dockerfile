FROM node:20-alpine3.22 AS builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20-alpine3.22
WORKDIR /opt/server
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=builder --chown=roboshop:roboshop /opt/server/ /opt/server/
LABEL project="roboshop" \
    maintainer="vamsi" \
    component="cart"
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
CMD [ "server.js" ]
ENTRYPOINT [ "node" ]


# FROM node:20
# WORKDIR /opt/server
# EXPOSE 8080
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
# CMD [ "node", "server.js" ]