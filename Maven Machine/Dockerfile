FROM maven:3-jdk-8

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
WORKDIR /root/.m2

ONBUILD ADD . /usr/src/app

ONBUILD RUN mvn clean && mvn install