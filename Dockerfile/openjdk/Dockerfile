# 基础镜像
FROM  openjdk:8-jre
# author
MAINTAINER aep

# 解决时差8小时问题
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone


# 挂载目录
VOLUME /home/aep
# 创建目录
RUN mkdir -p /home/aep
# 指定路径
WORKDIR /home/aep

# 复制文件及启动服务，通过外部命令实现