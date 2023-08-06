FROM debian:12-slim

# 配置国内镜像源
# 安装 OpenSSH 服务器
# 创建 SSH 密钥
# 设置 root 用户密码
# 允许 root 用户远程登录
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/debian/ buster main contrib non-free" > /etc/apt/sources.list && \
    echo "deb http://mirrors.tuna.tsinghua.edu.cn/debian/ buster-updates main contrib non-free" >> /etc/apt/sources.list && \
    echo "deb http://mirrors.tuna.tsinghua.edu.cn/debian/ buster-backports main contrib non-free" >> /etc/apt/sources.list && \
    echo "deb http://mirrors.tuna.tsinghua.edu.cn/debian-security buster/updates main contrib non-free" >> /etc/apt/sources.list && \
    mkdir /run/sshd && \
    chmod 755 /run/sshd && \
    apt-get update && \
    apt-get install -y --no-install-recommends openssh-server && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    ssh-keygen -A && \
    echo "root:!QAZ2wsx" | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# 开放 SSH 端口
EXPOSE 22

# 启动 SSH 服务
ENTRYPOINT ["/usr/sbin/sshd", "-D"]