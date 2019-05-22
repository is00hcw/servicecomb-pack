FROM openjdk:8

# 时区设置
RUN echo "Asia/shanghai" > /etc/timezone && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

ADD target/alpha-server-0.4.0-exec.jar /app.jar

EXPOSE 8080
VOLUME /tmp


ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]

