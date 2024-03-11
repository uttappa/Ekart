# FROM openjdk:8u151-jdk-alpine3.7

# EXPOSE 8070

# ENV APP_HOME /usr/src/app

# COPY target/shopping-cart-0.0.1-SNAPSHOT.jar $APP_HOME/app.jar

# WORKDIR $APP_HOME

# ENTRYPOINT exec java -jar app.jar


ARG alpine_image=alpine:latest
FROM openjdk:8-jdk-alpine
FROM ${alpine_image}
ENV Home_dir=/home/alpine/ekart-app
COPY target/shopping-cart-0.0.1-SNAPSHOT.jar ${Home_dir}/shopping-cart-0.0.1-SNAPSHOT.jar
RUN adduser -D alpine  -h /home/alpine -s bin/bash 
WORKDIR ${Home_dir}
RUN chown -R alpine:alpine shopping-cart-0.0.1-SNAPSHOT.jar
USER alpine
ENTRYPOINT [ "java","-jar","shopping-cart-0.0.1-SNAPSHOT.jar" ]
EXPOSE 8070
