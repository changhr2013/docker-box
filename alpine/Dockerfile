FROM alpine:3.18

# 配置清华镜像源
# 升级 apk-tools
# 安装 openssh 并配置 hostkey
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories && \
    apk upgrade --no-cache apk-tools && \
    apk add --no-cache openssh && \ 
    ssh-keygen -A && \
    echo "root:!QAZ2wsx" | chpasswd && \
    sed -i "s/#PermitRootLogin.*/PermitRootLogin yes/g" /etc/ssh/sshd_config

# 暴露 22 端口
EXPOSE 22

# 启动ssh服务
ENTRYPOINT [ "/usr/sbin/sshd", "-D"]