---
title: macOS 中管理 MySQL 服务的常用命令 
date: 2016-11-23 14:30:11
tags: [macOS, MySQL]
categories:

---

命令用法:  
> mysql.server  {start | stop | restart | reload | force-reload | status}


```bash
# 启动
$ /usr/local/mysql/support-files/mysql.server start

# 停止
$ /usr/local/mysql/support-files/mysql.server stop

# 重启
$ /usr/local/mysql/support-files/mysql.server restart

# 重新加载
$ /usr/local/mysql/support-files/mysql.server reload

# 强制重新加载
$ /usr/local/mysql/support-files/mysql.server force-reload

# 查看状态
$ /usr/local/mysql/support-files/mysql.server status
```

<!-- more -->

<br/>

可使用 `alias` 来简化以上命令操作. 在 `~/.bash_aliases` 文件中添加以下命令:

```bash
alias mysql-start='/usr/local/mysql/support-files/mysql.server start'
alias mysql-stop='/usr/local/mysql/support-files/mysql.server stop'
alias mysql-restart='/usr/local/mysql/support-files/mysql.server restart'
alias mysql-reload='/usr/local/mysql/support-files/mysql.server reload'
alias mysql-force-reload='/usr/local/mysql/support-files/mysql.server force-reload'
alias mysql-status='/usr/local/mysql/support-files/mysql.server status'
```

> 若还没有 `.bash_aliases` 文件, 需自行创建一个.

然后, 在 `~/.bash_profile` 文件的末尾添加以下代码:

```bash
if [[ -f ~/.bash_aliases ]]; then
    . ~/.bash_aliases
fi
```

最后, 使设置生效:

```bash
$ source ~/.bash_profile
```

这时, 若想启动 MySQL 服务, 只需运行以下命令:

```bash
$ mysql-start
```