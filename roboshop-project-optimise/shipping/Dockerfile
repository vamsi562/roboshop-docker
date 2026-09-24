FROM maven:3.9.11 AS builder
WORKDIR /opt/server
COPY src ./src
COPY pom.xml .
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar

FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
COPY --from=builder --chown=roboshop:roboshop /opt/server/shipping.jar .
USER roboshop
ENTRYPOINT ["java", "-jar", "shipping.jar"]


# FROM maven:3.9.11
# WORKDIR /opt/server
# COPY src ./src
# COPY pom.xml .
# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD [ "java","-jar","shipping.jar" ]