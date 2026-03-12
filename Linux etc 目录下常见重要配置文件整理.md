# Linux /etc 目录下常见重要配置文件整理

`/etc` 目录是 Linux 系统中存放系统配置文件的核心位置，几乎所有系统级和服务级的配置都集中在此。对于运维工作和面试来说，熟悉 `/etc` 下的文件和目录至关重要。以下是按功能分类的常见配置项及其简要说明。

------

## 1. 网络配置

| 文件/目录                               | 说明                                                        |
| :-------------------------------------- | :---------------------------------------------------------- |
| `/etc/hosts`                            | 静态主机名解析表，用于本地 DNS 解析。                       |
| `/etc/hostname`                         | 系统主机名。                                                |
| `/etc/resolv.conf`                      | DNS 解析器配置，指定 nameserver、搜索域等。                 |
| `/etc/nsswitch.conf`                    | 系统数据库（如 passwd、hosts）的查找顺序配置。              |
| `/etc/network/interfaces`               | Debian/Ubuntu 系统的网络接口配置文件。                      |
| `/etc/sysconfig/network-scripts/`       | RHEL/CentOS 6 及更早版本的网络脚本目录（如 `ifcfg-eth0`）。 |
| `/etc/NetworkManager/`                  | NetworkManager 配置目录（部分发行版）。                     |
| `/etc/hosts.allow` 和 `/etc/hosts.deny` | TCP wrappers 访问控制配置（已逐渐被防火墙替代，但仍存在）。 |

------

## 2. 系统基本信息

| 文件/目录         | 说明                                         |
| :---------------- | :------------------------------------------- |
| `/etc/os-release` | 操作系统发行版信息（ID、版本、名称等）。     |
| `/etc/issue`      | 登录前显示的欢迎信息。                       |
| `/etc/issue.net`  | 远程登录（如 telnet）显示的欢迎信息。        |
| `/etc/motd`       | 登录后显示的每日消息（Message Of The Day）。 |

------

## 3. 用户和认证

| 文件/目录                   | 说明                                              |
| :-------------------------- | :------------------------------------------------ |
| `/etc/passwd`               | 用户账户信息（用户名、UID、GID、家目录、shell）。 |
| `/etc/shadow`               | 用户加密密码及密码策略信息（仅 root 可读）。      |
| `/etc/group`                | 用户组信息。                                      |
| `/etc/gshadow`              | 用户组加密密码信息。                              |
| `/etc/sudoers`              | sudo 权限配置（必须用 `visudo` 编辑）。           |
| `/etc/sudoers.d/`           | 存放独立的 sudo 规则文件。                        |
| `/etc/login.defs`           | 登录参数定义，如密码过期、UID 范围等。            |
| `/etc/pam.d/`               | PAM（可插拔认证模块）配置文件目录。               |
| `/etc/security/limits.conf` | 用户资源限制（如打开文件数、进程数）。            |
| `/etc/security/limits.d/`   | 独立的资源限制配置。                              |

------

## 4. 系统启动与计划任务

| 文件/目录                                                    | 说明                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| `/etc/fstab`                                                 | 文件系统挂载表，定义开机自动挂载的分区/设备。                |
| `/etc/inittab`                                               | 早期 SysV init 的默认运行级别配置（现代系统多改用 systemd）。 |
| `/etc/init.d/`                                               | SysV 风格服务脚本目录。                                      |
| `/etc/systemd/`                                              | systemd 服务配置目录（包含 `system/`、`user/` 等子目录）。   |
| `/etc/systemd/system/`                                       | 用户自定义或覆盖的 systemd 单元文件。                        |
| `/etc/crontab`                                               | 系统级 crontab 文件。                                        |
| `/etc/cron.d/`                                               | 存放独立的 cron 任务文件。                                   |
| `/etc/cron.daily/`、`/etc/cron.hourly/`、`/etc/cron.weekly/`、`/etc/cron.monthly/` | 按时间周期执行的脚本目录。                                   |
| `/etc/at.allow` 和 `/etc/at.deny`                            | 控制哪些用户可以使用 `at` 命令。                             |
| `/etc/anacrontab`                                            | anacron 配置文件（处理非 7x24 小时运行系统的定时任务）。     |

------

## 5. 服务与应用配置

| 文件/目录                                                   | 说明                                       |
| :---------------------------------------------------------- | :----------------------------------------- |
| `/etc/services`                                             | 网络服务名称与端口号映射表。               |
| `/etc/protocols`                                            | 协议名称与协议号映射表。                   |
| `/etc/ssh/sshd_config`                                      | SSH 服务端配置文件。                       |
| `/etc/ssh/ssh_config`                                       | SSH 客户端全局配置文件。                   |
| `/etc/nginx/nginx.conf`                                     | Nginx 主配置文件（目录为 `/etc/nginx/`）。 |
| `/etc/httpd/conf/httpd.conf` 或 `/etc/apache2/apache2.conf` | Apache HTTP 服务器配置文件。               |
| `/etc/mysql/my.cnf` 或 `/etc/my.cnf`                        | MySQL/MariaDB 配置文件。                   |
| `/etc/redis/redis.conf`                                     | Redis 配置文件。                           |
| `/etc/postfix/main.cf`                                      | Postfix 邮件服务主配置文件。               |
| `/etc/samba/smb.conf`                                       | Samba 配置文件。                           |
| `/etc/dhcp/dhcpd.conf`                                      | DHCP 服务端配置文件（如果安装）。          |

------

## 6. 软件包管理

| 文件/目录           | 说明                                                       |
| :------------------ | :--------------------------------------------------------- |
| `/etc/apt/`         | Debian/Ubuntu 的 APT 包管理配置目录（如 `sources.list`）。 |
| `/etc/yum.conf`     | CentOS/RHEL 6/7 的 YUM 配置文件。                          |
| `/etc/yum.repos.d/` | YUM 仓库源配置文件目录。                                   |
| `/etc/dnf/dnf.conf` | CentOS/RHEL 8+ 的 DNF 配置文件。                           |
| `/etc/zypp/`        | openSUSE 的 Zypper 包管理配置目录。                        |

------

## 7. 日志与审计

| 文件/目录             | 说明                         |
| :-------------------- | :--------------------------- |
| `/etc/rsyslog.conf`   | rsyslog 日志服务主配置文件。 |
| `/etc/rsyslog.d/`     | rsyslog 附加配置目录。       |
| `/etc/logrotate.conf` | logrotate 日志轮转主配置。   |
| `/etc/logrotate.d/`   | 各应用的日志轮转规则文件。   |

------

## 8. 时间同步

| 文件/目录          | 说明                                             |
| :----------------- | :----------------------------------------------- |
| `/etc/ntp.conf`    | NTP 客户端/服务器配置文件（传统）。              |
| `/etc/chrony.conf` | Chrony 时间同步服务配置文件（现代系统常用）。    |
| `/etc/timezone`    | 系统时区（Debian/Ubuntu）。                      |
| `/etc/localtime`   | 符号链接到 `/usr/share/zoneinfo/` 下的时区文件。 |

------

## 9. 内核与模块

| 文件/目录              | 说明                                          |
| :--------------------- | :-------------------------------------------- |
| `/etc/sysctl.conf`     | 内核参数配置文件（`sysctl`）。                |
| `/etc/sysctl.d/`       | 独立的 sysctl 配置文件。                      |
| `/etc/modprobe.d/`     | 内核模块参数配置目录（如黑名单、别名）。      |
| `/etc/modules`         | 开机自动加载的内核模块列表（Debian/Ubuntu）。 |
| `/etc/modules-load.d/` | systemd 管理的内核模块加载配置。              |

------

## 10. Shell 与环境变量

| 文件/目录                           | 说明                                        |
| :---------------------------------- | :------------------------------------------ |
| `/etc/profile`                      | 全局环境变量和启动脚本（登录 shell 执行）。 |
| `/etc/bashrc` 或 `/etc/bash.bashrc` | 全局 bash 配置（交互式非登录 shell 执行）。 |
| `/etc/environment`                  | 系统范围的环境变量定义（某些发行版）。      |
| `/etc/skel/`                        | 新用户家目录的模板文件（如 `.bashrc` 等）。 |
| `/etc/inputrc`                      | 全局 readline 配置（键盘映射等）。          |
| `/etc/shells`                       | 系统可用的合法 shell 列表。                 |

------

## 11. 存储与文件系统

| 文件/目录                           | 说明                                                         |
| :---------------------------------- | :----------------------------------------------------------- |
| `/etc/fstab`                        | 已在上文提及，但再次强调其重要性。                           |
| `/etc/mtab`                         | 当前挂载的文件系统列表（通常为 `/proc/mounts` 的符号链接）。 |
| `/etc/exports`                      | NFS 服务导出的文件系统配置。                                 |
| `/etc/auto.master` 和 `/etc/auto.*` | autofs 自动挂载配置。                                        |

------

## 12. 安全与防火墙

| 文件/目录             | 说明                                      |
| :-------------------- | :---------------------------------------- |
| `/etc/selinux/`       | SELinux 配置文件目录（如 `config`）。     |
| `/etc/selinux/config` | SELinux 主配置文件（启用模式等）。        |
| `/etc/firewalld/`     | firewalld 防火墙配置目录。                |
| `/etc/iptables/`      | iptables 规则保存文件目录（部分发行版）。 |
| `/etc/nftables/`      | nftables 配置文件目录。                   |

------

## 13. 其他常用文件

| 文件/目录       | 说明                                            |
| :-------------- | :---------------------------------------------- |
| `/etc/aliases`  | 本地邮件别名配置文件（用于 sendmail/postfix）。 |
| `/etc/mail/`    | Sendmail 或 Postfix 的邮件配置目录。            |
| `/etc/printcap` | 打印机配置（较老系统）。                        |
| `/etc/opt/`     | 第三方软件包配置文件存放目录（遵循 FHS）。      |
| `/etc/X11/`     | X Window 系统配置文件目录（如 `xorg.conf`）。   |

------

## 总结

- **运维面试常考**：`passwd`、`shadow`、`group`、`fstab`、`hosts`、`resolv.conf`、`sudoers`、`crontab`、`sysctl.conf`、`sshd_config`、`ntp.conf`、`rsyslog.conf`、`logrotate.conf` 等。
- **日常工作高频**：`/etc/nginx/`、`/etc/httpd/`、`/etc/my.cnf`、`/etc/ssh/sshd_config`、`/etc/sysconfig/network-scripts/`（CentOS）或 `/etc/network/interfaces`（Debian）、`/etc/apt/sources.list`、`/etc/yum.repos.d/` 等。