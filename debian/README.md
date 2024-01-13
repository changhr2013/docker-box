## Debian 包管理

### apt（推荐用于命令行）

- `apt update`: 更新软件包档案库元数据
- `apt install foo`: 安装“foo”软件包的候选版本以及它的依赖
- `apt upgrade`: 安装已安装的软件包的候选版本并且不移除任何其他软件包
- `apt full-upgrade`: 安装已安装的软件包的候选版本，并且需要的话会移除其它的软件包
- `apt remove foo`: 移除“foo”软件包，但留下配置文件
- `apt autoremove`: 移除不再需要的自动安装的软件包
- `apt purge foo`: 清除“foo”软件包的配置文件
- `apt clean`: 完全清除本地仓库的软件包检索文件
- `apt autoclean`: 清除本地仓库中过时软件包的软件包检索文件
- `apt show foo`: 显示“foo”软件包的详细信息
- `apt search 正则表达式`: 搜索匹配 regex 的软件包

#### --no-install-recommends: 

`apt` 命令中的 `--no-install-recommends` 参数用于控制在安装软件包时是否安装“推荐 (recommended)”的附加包。

在 `Debian` 和基于 `Debian` 的系统中，软件包可以有三种类型的依赖关系：

依赖（Depends）：这是必需的依赖，用于确保软件包正常工作。在安装软件包时，其依赖的包也会自动被安装。

推荐（Recommends）：这些是建议安装的依赖，用于提供更完整的功能，但不是软件包运行的必需条件。在默认情况下，使用 apt 安装软件包时，推荐的包也会被安装。

建议（Suggests）：这些是可选的依赖，通常是增强或补充软件包功能的额外软件。这些包在使用 apt 安装时不会被自动安装。

使用 `--no-install-recommends` 参数时，`apt` 只会安装软件包的必需依赖（Depends），而不会安装推荐的包。这对于节省磁盘空间和减少非必需软件的安装非常有用，尤其是在资源有限的环境（如容器或低资源服务器）中。


### apt-get（推荐用于 shell 脚本）

> 大部分命令与 `apt` 保持一致，此处只列举不一致的命令。

- `apt-get dist-upgrade`: 安装已安装的软件包的候选版本，并且需要的话会移除其它的软件包
- `apt-cache show foo`: 显示“foo”软件包的详细信息
- `apt-cache search regex`: 搜索匹配 regex 的软件包
- `apt-mark showmanual`: 列出手动安装的软件包

### aptitude（交互式命令行）

> 大部分命令与 `apt` 保持一致，此处只列举不一致的命令。

- `aptitude safe-upgrade`: 安装已安装的软件包的候选版本并且不移除任何其它的软件包
- `aptitude full-upgrade`: 安装已安装的软件包的候选版本，并且需要的话会移除其它的软件包
- `aptitude why regex`: 解释匹配 regex 的软件包必须被安装的原因
- `aptitude why-not regex`: 解释匹配 regex 的软件包不必安装的原因
- `aptitude search '~i!~M'`: 列出手动安装的软件包

### dpkg (低级包管理工具)

> 注意：`dpkg` 本身不处理依赖关系问题。如果使用 `dpkg` 安装包，并且出现了依赖关系问题，可以使用 `sudo apt-get install -f` 命令来修复。这个命令会安装任何缺失的依赖项，并完成 `dpkg` 未能完成的安装。

- `dpkg -i <package_file.deb>`: 安装一个软件包
- `dpkg -l`: 列出已安装的软件包
- `dpkg -s <package_name>`: 查询特定软件包信息
- `dpkg -r <package_name>`: 移除软件包但保留配置文件
- `dpkg -P <package_name>`: 完全删除软件包及其配置文件
- `dpkg -L <package_name>`: 列出软件包的内容
- `dpkg -S <file_path>`: 查询文件的所属包
- `dpkg-reconfigure <package_name>`: 重新配置已安装的软件包
- `dpkg --configure -a`: 尝试修复因中断的安装或更新而损坏的软件包

### 常用命令所在的包名

- `net-tools`: `netstat`, `ifconfig`
- `iputils-ping`: `ping`
- `gawk`: `awk`
- `openssh-client`: `ssh`, `scp`