#基础镜像：仓库是java，标签用8
FROM java:8

#通过 VOLUME 指令创建的挂载点，无法指定主机上对应的目录，是自动生成的
VOLUME ["/opt/app/myLogs"]

#系统日志所在文件夹
ENV logdir /opt/app/myLogs

#将打包好的spring程序拷贝到容器中的指定位置
COPY grpc-server-1.0-SNAPSHOT.jar /opt/app/app.jar

#修复时区
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' >/etc/timezone

#容器对外暴露端口
EXPOSE 9898

WORKDIR /opt/app

#ENV JAVA_OPTS=""
#ENTRYPOINT exec java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar app.jar
CMD java -jar app.jar