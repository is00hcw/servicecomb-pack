FROM openjdk:8

# 时区设置
RUN echo "Asia/shanghai" > /etc/timezone && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

ADD target/saga/alpha-server-0.4.0-exec.jar /app.jar

EXPOSE 8080
VOLUME /tmp

ENV DB_PASSWORD=""

ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-Dspring.profiles.active=mysql","-Dspring.datasource.password=${DB_PASSWORD}", "-Dspring.datasource.url=jdbc:mysql://mysql-db:3306/saga?useSSL=false&allowPublicKeyRetrieval=true","-Dspring.datasource.username=root","-jar","/app.jar"]

