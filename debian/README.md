## Debian 包管理

### apt（推荐用于命令行）
`apt update`: 更新软件包档案库元数据
`apt install foo`: 安装“foo”软件包的候选版本以及它的依赖
`apt upgrade`: 安装已安装的软件包的候选版本并且不移除任何其他软件包
`apt full-upgrade`: 安装已安装的软件包的候选版本，并且需要的话会移除其它的软件包
`apt remove foo`: 移除“foo”软件包，但留下配置文件
`apt autoremove`: 移除不再需要的自动安装的软件包
`apt purge foo`: 清除“foo”软件包的配置文件
`apt clean`: 完全清除本地仓库的软件包检索文件
`apt autoclean`: 清除本地仓库中过时软件包的软件包检索文件
`apt show foo`: 显示“foo”软件包的详细信息
`apt search 正则表达式`: 搜索匹配 regex 的软件包

### apt-get（推荐用于 shell 脚本）

> 大部分命令与 `apt` 保持一致，此处只列举不一致的命令。

`apt-get dist-upgrade`: 安装已安装的软件包的候选版本，并且需要的话会移除其它的软件包
`apt-cache show foo`: 显示“foo”软件包的详细信息
`apt-cache search regex`: 搜索匹配 regex 的软件包
`apt-mark showmanual`: 列出手动安装的软件包

### aptitude（交互式命令行）

> 大部分命令与 `apt` 保持一致，此处只列举不一致的命令。

`aptitude safe-upgrade`: 安装已安装的软件包的候选版本并且不移除任何其它的软件包
`aptitude full-upgrade`: 安装已安装的软件包的候选版本，并且需要的话会移除其它的软件包
`aptitude why regex`: 解释匹配 regex 的软件包必须被安装的原因
`aptitude why-not regex`: 解释匹配 regex 的软件包不必安装的原因
`aptitude search '~i!~M'`: 列出手动安装的软件包