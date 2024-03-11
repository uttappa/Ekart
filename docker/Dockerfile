# FROM openjdk:8u151-jdk-alpine3.7

# EXPOSE 8070

# ENV APP_HOME /usr/src/app

# COPY target/shopping-cart-0.0.1-SNAPSHOT.jar $APP_HOME/app.jar

# WORKDIR $APP_HOME

# ENTRYPOINT exec java -jar app.jar


ARG alpine_image=alpine:latest
#FROM openjdk:8-jdk-alpine
FROM ${alpine_image}
RUN  apk update &&  apk fetch openjdk8 && apk add openjdk8
ENV JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk
ENV PATH=${JAVA_HOME}/bin:${PATH}
RUN java --version 
RUN mkdir -p /alpine/ekart-app && adduser -D alpine  -h /home/alpine -s bin/bash
COPY target/shopping-cart-0.0.1-SNAPSHOT.jar  /alpine/ekart-app/shopping-cart-0.0.1-SNAPSHOT.jar
WORKDIR /alpine/ekart-app
RUN chown -R alpine:alpine shopping-cart-0.0.1-SNAPSHOT.jar
USER alpine
RUN hostname
ENTRYPOINT [ "java","-jar","shopping-cart-0.0.1-SNAPSHOT.jar" ]
EXPOSE 8070
