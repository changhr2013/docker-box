FROM debian:12

# 设置默认时区
ENV TZ=Asia/Shanghai

# 配置国内镜像源
# 安装 OpenSSH 服务器和 locales 本地化语言环境
# 设置语言环境为 zh_CN.UTF-8
# 创建 SSH 密钥
# 设置 root 用户密码
# 允许 root 用户远程登录
RUN sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list.d/debian.sources && \
    mkdir /run/sshd && \
    chmod 755 /run/sshd && \
    apt-get update && \
    apt-get install -y --no-install-recommends openssh-server locales && \
    localedef -i zh_CN -c -f UTF-8 -A /usr/share/locale/locale.alias zh_CN.UTF-8 && \
    ssh-keygen -A && \
    echo "root:!QAZ2wsx" | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ENV LANG=zh_CN.UTF-8

# 开放 SSH 端口
EXPOSE 22

# 启动 SSH 服务
ENTRYPOINT ["/usr/sbin/sshd", "-D"]