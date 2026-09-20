FROM maven:3.9.11 AS builder
WORKDIR /opt/server
COPY src ./src
COPY pom.xml .


FROM maven:3.9.11
WORKDIR /opt/server
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=builder --chown=roboshop:roboshop /opt/server/ /opt/server/
RUN mvn clean package
RUN mv target/shipping-1.0.jar shipping.jar
LABEL project="roboshop" \
    maintainer="vamsi" \
    component="shipping"
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
USER roboshop
ENTRYPOINT [ "java" ]
CMD [ "-jar","shipping.jar" ]


# FROM maven:3.9.11
# WORKDIR /opt/server
# COPY src ./src
# COPY pom.xml .
# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD [ "java","-jar","shipping.jar" ]