FROM openjdk:8

# 时区设置
RUN echo "Asia/shanghai" > /etc/timezone && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

ADD target/saga/alpha-server-0.4.0-exec.jar /app.jar
ADD target/classes/application.yaml /application.yaml

EXPOSE 8080
VOLUME /tmp

ENV DB_PASSWORD=""

## "-Dspring.datasource.password=${DB_PASSWORD}",

ENTRYPOINT ["java","-XX:+UnlockExperimentalVMOptions","-XX:+UseCGroupMemoryLimitForHeap","-XX:MaxRAMFraction=1","-XshowSettings:vm","-Djava.security.egd=file:/dev/./urandom", "-Dspring.config.location=file:/application.yaml", "-Dspring.profiles.active=mysql", "-Dspring.datasource.url=jdbc:mysql://mysql-db:3306/saga?useSSL=false&allowPublicKeyRetrieval=true","-Dspring.datasource.username=root","-jar","/app.jar"]

