ARG alpine_image=alpine:latest
#FROM openjdk:8-jdk-alpine  <--- don't use this you might get java $PATH not found.
FROM ${alpine_image}
RUN  apk update &&  apk fetch openjdk8 && apk add openjdk8
RUN apk update && apk search curl && apk add curl && curl --version
ENV JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk
ENV PATH=${JAVA_HOME}/bin:${PATH}
RUN java -version 
RUN mkdir -p /alpine/ekart-app && adduser -D alpine  -h /home/alpine -s bin/bash
COPY target/shopping-cart-0.0.1-SNAPSHOT.jar  /alpine/ekart-app/shopping-cart-0.0.1-SNAPSHOT.jar
WORKDIR /alpine/ekart-app
RUN chown -R alpine:alpine shopping-cart-0.0.1-SNAPSHOT.jar && ls -all
USER alpine
RUN hostname
ENTRYPOINT [ "java","-jar","shopping-cart-0.0.1-SNAPSHOT.jar" ]
EXPOSE 8070

#How to tackle if java $PATH not found better install java from below alpine method.
#-------------------------------------------------------------------------------
# RUN apk update
# RUN apk fetch openjdk8
# RUN apk add openjdk8
# ENV JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk
# ENV PATH="$JAVA_HOME/bin:${PATH}"
# RUN java -version
#-------------------------------------------------------------------------------
