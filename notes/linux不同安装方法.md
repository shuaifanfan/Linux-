- [RPM](#rpm)
  - [默认安装路径](#默认安装路径)
  - [查询 默认安装路径](#查询-默认安装路径)
  - [改变默认安装路径【不推荐】](#改变默认安装路径不推荐)
- [源码安装](#源码安装)
  - [从源码解压，配置，编译，安装，一个程序](#从源码解压配置编译安装一个程序)
  - [Linux源码包卸载](#linux源码包卸载)
- [npm安装](#npm安装)
- [Linux环境变量配置](#linux环境变量配置)
  - [Linux读取环境变量](#linux读取环境变量)
    - [Linux环境变量配置方法一：`export PATH`](#linux环境变量配置方法一export-path)
    - [Linux环境变量配置方法二：`vim ~/.bashrc`](#linux环境变量配置方法二vim-bashrc)
    - [Linux环境变量配置方法三：`vim ~/.bash_profile`](#linux环境变量配置方法三vim-bash_profile)
    - [Linux环境变量配置方法四：`vim /etc/bashrc`](#linux环境变量配置方法四vim-etcbashrc)
    - [Linux环境变量配置方法五：`vim /etc/profile`](#linux环境变量配置方法五vim-etcprofile)
    - [Linux环境变量配置方法六：`vim /etc/environment`](#linux环境变量配置方法六vim-etcenvironment)
  - [Linux环境变量加载原理解析](#linux环境变量加载原理解析)
    - [环境变量的分类](#环境变量的分类)
    - [测试Linux环境变量加载顺序的方法](#测试linux环境变量加载顺序的方法)
    - [Linux环境变量文件加载详解](#linux环境变量文件加载详解)
    - [一些小技巧](#一些小技巧)

>  链接：https://juejin.cn/post/7017730484520091655

# RPM

> rpm命令只能安装本地的rpm包，而yum可以在线获取社区的rpm包

## 默认安装路径

通常，RPM 包采用系统默认的安装路径。安装文件会按照类别分别安装到不同的目录，如下所示：

| RPM 包默认安装路径 | 含 义                           |
| ------------------ | ------------------------------- |
| /etc/              | 配置文件安装目录，如/etc/my.cfg |
| /usr/bin/          | 可执行的命令安装目录            |
| /usr/lib/          | 程序所使用的函数库保存位置      |
| /usr/share/doc/    | 基本的软件使用手册保存位置      |
| /usr/share/man/    | 帮助文件(man page文件)保存位置  |

RPM 包还可以手动指定安装路径（不推荐）。

## 查询 默认安装路径

rpm包文件中会记录相关的配置参数，并且会对照Linux系统的环境，在安装时生成对应的信息，比如安装路径、配置路径等。

**查询一个包的默认安装路径等信息，可以使用 `rpm -qpl <package_name>`。**

- `-q|--query` 表示执行rpm查询。单独使用表示查询安装的包 —— 是否安装，及安装的包名（获得某个软件包的全名）。
- `-p|--package` 表示查询指定的软件包（尤其是未安装的包）。如果一个包未安装，不指定 `-p` 将会提示未安装。
- `-l|--list`：表示列出软件包中包含的所有文件及各自安装路径。

比如，查询一个在线的MySQL包的信息，包括默认安装路径：【可以安装MySQL的安装涉及到的路径远比平时认识到的多的多】

```sh
# rpm -qpl https://mirrors.tuna.tsinghua.edu.cn/mysql/yum/mysql-8.0-community-el7-x86_64/mysql-community-server-8.0.26-1.el7.x86_64.rpm
/etc/logrotate.d/mysql
/etc/my.cnf
/etc/my.cnf.d
/usr/bin/ibd2sdi
/usr/bin/innochecksum
/usr/bin/lz4_decompress
/usr/bin/my_print_defaults
/usr/bin/myisam_ftdump
/usr/bin/myisamchk
/usr/bin/myisamlog
/usr/bin/myisampack
/usr/bin/mysql_secure_installation
/usr/bin/mysql_ssl_rsa_setup
/usr/bin/mysql_tzinfo_to_sql
/usr/bin/mysql_upgrade
/usr/bin/mysqld_pre_systemd
/usr/bin/mysqldumpslow
/usr/bin/perror
/usr/bin/zlib_decompress
/usr/lib/systemd/system/mysqld.service
/usr/lib/systemd/system/mysqld@.service
/usr/lib/tmpfiles.d/mysql.conf
/usr/lib64/mysql/mecab
/usr/lib64/mysql/mecab/dic
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/char.bin
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/dicrc
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/left-id.def
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/matrix.bin
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/pos-id.def
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/rewrite.def
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/right-id.def
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/sys.dic
/usr/lib64/mysql/mecab/dic/ipadic_euc-jp/unk.dic
/usr/lib64/mysql/mecab/dic/ipadic_sjis
/usr/lib64/mysql/mecab/dic/ipadic_sjis/char.bin
/usr/lib64/mysql/mecab/dic/ipadic_sjis/dicrc
/usr/lib64/mysql/mecab/dic/ipadic_sjis/left-id.def
/usr/lib64/mysql/mecab/dic/ipadic_sjis/matrix.bin
/usr/lib64/mysql/mecab/dic/ipadic_sjis/pos-id.def
/usr/lib64/mysql/mecab/dic/ipadic_sjis/rewrite.def
/usr/lib64/mysql/mecab/dic/ipadic_sjis/right-id.def
/usr/lib64/mysql/mecab/dic/ipadic_sjis/sys.dic
/usr/lib64/mysql/mecab/dic/ipadic_sjis/unk.dic
/usr/lib64/mysql/mecab/dic/ipadic_utf-8
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/char.bin
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/dicrc
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/left-id.def
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/matrix.bin
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/pos-id.def
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/rewrite.def
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/right-id.def
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/sys.dic
/usr/lib64/mysql/mecab/dic/ipadic_utf-8/unk.dic
/usr/lib64/mysql/mecab/etc
/usr/lib64/mysql/mecab/etc/mecabrc
/usr/lib64/mysql/plugin
/usr/lib64/mysql/plugin/adt_null.so
/usr/lib64/mysql/plugin/auth_socket.so
/usr/lib64/mysql/plugin/component_audit_api_message_emit.so
/usr/lib64/mysql/plugin/component_keyring_file.so
/usr/lib64/mysql/plugin/component_log_filter_dragnet.so
/usr/lib64/mysql/plugin/component_log_sink_json.so
/usr/lib64/mysql/plugin/component_log_sink_syseventlog.so
/usr/lib64/mysql/plugin/component_mysqlbackup.so
/usr/lib64/mysql/plugin/component_query_attributes.so
/usr/lib64/mysql/plugin/component_reference_cache.so
/usr/lib64/mysql/plugin/component_validate_password.so
/usr/lib64/mysql/plugin/connection_control.so
/usr/lib64/mysql/plugin/ddl_rewriter.so
/usr/lib64/mysql/plugin/debug
/usr/lib64/mysql/plugin/debug/adt_null.so
/usr/lib64/mysql/plugin/debug/auth_socket.so
/usr/lib64/mysql/plugin/debug/component_audit_api_message_emit.so
/usr/lib64/mysql/plugin/debug/component_keyring_file.so
/usr/lib64/mysql/plugin/debug/component_log_filter_dragnet.so
/usr/lib64/mysql/plugin/debug/component_log_sink_json.so
/usr/lib64/mysql/plugin/debug/component_log_sink_syseventlog.so
/usr/lib64/mysql/plugin/debug/component_mysqlbackup.so
/usr/lib64/mysql/plugin/debug/component_query_attributes.so
/usr/lib64/mysql/plugin/debug/component_reference_cache.so
/usr/lib64/mysql/plugin/debug/component_validate_password.so
/usr/lib64/mysql/plugin/debug/connection_control.so
/usr/lib64/mysql/plugin/debug/ddl_rewriter.so
/usr/lib64/mysql/plugin/debug/group_replication.so
/usr/lib64/mysql/plugin/debug/ha_example.so
/usr/lib64/mysql/plugin/debug/ha_mock.so
/usr/lib64/mysql/plugin/debug/innodb_engine.so
/usr/lib64/mysql/plugin/debug/keyring_file.so
/usr/lib64/mysql/plugin/debug/keyring_udf.so
/usr/lib64/mysql/plugin/debug/libmemcached.so
/usr/lib64/mysql/plugin/debug/libpluginmecab.so
/usr/lib64/mysql/plugin/debug/locking_service.so
/usr/lib64/mysql/plugin/debug/mypluglib.so
/usr/lib64/mysql/plugin/debug/mysql_clone.so
/usr/lib64/mysql/plugin/debug/mysql_no_login.so
/usr/lib64/mysql/plugin/debug/rewrite_example.so
/usr/lib64/mysql/plugin/debug/rewriter.so
/usr/lib64/mysql/plugin/debug/semisync_master.so
/usr/lib64/mysql/plugin/debug/semisync_replica.so
/usr/lib64/mysql/plugin/debug/semisync_slave.so
/usr/lib64/mysql/plugin/debug/semisync_source.so
/usr/lib64/mysql/plugin/debug/validate_password.so
/usr/lib64/mysql/plugin/debug/version_token.so
/usr/lib64/mysql/plugin/group_replication.so
/usr/lib64/mysql/plugin/ha_example.so
/usr/lib64/mysql/plugin/ha_mock.so
/usr/lib64/mysql/plugin/innodb_engine.so
/usr/lib64/mysql/plugin/keyring_file.so
/usr/lib64/mysql/plugin/keyring_udf.so
/usr/lib64/mysql/plugin/libmemcached.so
/usr/lib64/mysql/plugin/libpluginmecab.so
/usr/lib64/mysql/plugin/locking_service.so
/usr/lib64/mysql/plugin/mypluglib.so
/usr/lib64/mysql/plugin/mysql_clone.so
/usr/lib64/mysql/plugin/mysql_no_login.so
/usr/lib64/mysql/plugin/rewrite_example.so
/usr/lib64/mysql/plugin/rewriter.so
/usr/lib64/mysql/plugin/semisync_master.so
/usr/lib64/mysql/plugin/semisync_replica.so
/usr/lib64/mysql/plugin/semisync_slave.so
/usr/lib64/mysql/plugin/semisync_source.so
/usr/lib64/mysql/plugin/validate_password.so
/usr/lib64/mysql/plugin/version_token.so
/usr/lib64/mysql/private
/usr/lib64/mysql/private/libprotobuf-lite.so.3.11.4
/usr/lib64/mysql/private/libprotobuf.so.3.11.4
/usr/sbin/mysqld
/usr/sbin/mysqld-debug
/usr/share/doc/mysql-community-server-8.0.26
/usr/share/doc/mysql-community-server-8.0.26/INFO_BIN
/usr/share/doc/mysql-community-server-8.0.26/INFO_SRC
/usr/share/doc/mysql-community-server-8.0.26/LICENSE
/usr/share/doc/mysql-community-server-8.0.26/README
/usr/share/man/man1/ibd2sdi.1.gz
/usr/share/man/man1/innochecksum.1.gz
/usr/share/man/man1/lz4_decompress.1.gz
/usr/share/man/man1/my_print_defaults.1.gz
/usr/share/man/man1/myisam_ftdump.1.gz
/usr/share/man/man1/myisamchk.1.gz
/usr/share/man/man1/myisamlog.1.gz
/usr/share/man/man1/myisampack.1.gz
/usr/share/man/man1/mysql_secure_installation.1.gz
/usr/share/man/man1/mysql_ssl_rsa_setup.1.gz
/usr/share/man/man1/mysql_tzinfo_to_sql.1.gz
/usr/share/man/man1/mysql_upgrade.1.gz
/usr/share/man/man1/mysqldumpslow.1.gz
/usr/share/man/man1/mysqlman.1.gz
/usr/share/man/man1/perror.1.gz
/usr/share/man/man1/zlib_decompress.1.gz
/usr/share/man/man8/mysqld.8.gz
/usr/share/mysql-8.0/dictionary.txt
/usr/share/mysql-8.0/innodb_memcached_config.sql
/usr/share/mysql-8.0/install_rewriter.sql
/usr/share/mysql-8.0/mysql-log-rotate
/usr/share/mysql-8.0/uninstall_rewriter.sql
/var/lib/mysql
/var/lib/mysql-files
/var/lib/mysql-keyring
/var/run/mysqld
复制代码
```

可以看到，列出了mysql安装的所有目录【真多！】

> 如果查询未安装的软件包，且未指定 `-p` 参数，会报错` is not installed`：
>
> ```sh
> # rpm -ql https://mirrors.tuna.tsinghua.edu.cn/mysql/yum/mysql-8.0-community-el7-x86_64/mysql-community-server-8.0.26-1.el7.x86_64.rpm
> package https://mirrors.tuna.tsinghua.edu.cn/mysql/yum/mysql-8.0-community-el7-x86_64/mysql-community-server-8.0.26-1.el7.x86_64.rpm is not installed
> 复制代码
> ```

## 改变默认安装路径【不推荐】

`rpm -qpl`命令可以查看软件包默认的安装目录。在安装软件包时，通过`--relocate`参数，可以修改安装中涉及到的默认路径。

如下所示，

```sh
rpm -ivh --relocate /usr/bin=/home/user_test/bin --relocate /usr/share/doc=/home/user_test/share/doc xxxxxx.rpm
复制代码
```

再一次声明：极其非常特别不推荐修改rpm包的默认安装路径。 有可能导致软件运行异常、管理问题等。



>  http://c.biancheng.net/view/2952.html

# 源码安装

> **从源码安装后，需要配置环境变量才能在任意位置使用命令**

## 从源码解压，配置，编译，安装，一个程序

本节仍然以安装 apache 为例，安装过程分为如下几步：

1. 下载 apache 源码包。该软件的源码包可通过官方网站 http://httpd.apache.org/download.cgi#apache24 下载，得到的源码包格式为压缩包（ ".tar.gz" 或 ".tar.bz2" ）。

   将各种文件分门别类保存在对应的目录中，应该成为合格 Linux 管理员约定俗成的习惯。Linux 系统中用于保存源代码的位置主要有 2 个，分别是 "/usr/src" 和 "/usr/local/src"，其中 "/usr/src" 用来保存内核源代码，"/usr/local/src" 用来保存用户下载的源代码。

2. 将源码包进行解压缩，使用命令如下：

   [root@localhost ~]#tar -zxvf httpd-2.2.9.tar.gz|more

3. 进入解压目录，执行如下命令：

   [root@localhost ~]# ls
   anaconda-ks.cfg httpd-2.2.9 httpd-2.2.9.tar.gz install.log install.log.syslog
   [root@localhost ~]# cd httpd-2.2.9

4. ./configure 软件配置与检查。这一步主要完成以下 3 项任务：

   - 检测系统环境是否符合安装要求。

   - 定义需要的功能选项。通过 "./configure--prefix=安装路径" 可以指定安装路径。注意，configure 不是系统命令，而是源码包软件自带的一个脚本程序，所以必须采用 "./configure" 方式执行（"./" 代表在当前目录下）。

     "./configure" 支持的功能选项较多，可执行 "./configure--help" 命令查询其支持的功能，例如：

     [root@localhost httpd-2.2.9]#./configure --help|more
     \#查询apache支持的选项功能（不是必需步骤）

   - 把系统环境的检测结果和定义好的功能选项写入 Makefile 文件，因为后续的编译和安装需要依赖这个文件的内容。

   此步具体执行代码如下：

   [root@localhost httpd-2.2.9]# ./configure --prefix=/usr/local/apache2
   checking for chosen layout...Apache
   checking for working mkdir -p…yes
   checking build system type...i686-pc-linux-gnu
   checking host system type...i686-pc-linux-gnu
   checking target system typa...i686-pc-linux-gnu
   …省略部分输出…

   --prefix 选项的含义为指定安装目录。

   此命令没有加载其他功能，只是指定安装目录。需要说明的是，"/usr/local/apache2" 目录不需要手工建立，安装完成后会自动建立（这个目录是否生成也是检测软件是否正确安装的重要标志）。

5. make 编译。make 会调用 gcc 编译器，并读取 Makefile 文件中的信息进行系统软件编译。编译的目的就是把源码程序转变为能被 Linux 识别的可执行文件，这些可执行文件保存在当前目录下。

   执行的编译命令如下：

   [root@localhost httpd-2.2.9]# make

   编程过程较为耗时，需要有足够的耐心。

6. 正式开始安装软件，这里通常会写清程序的安装位置，如果没有，则建议读者把安装的执行过程保存下来，以备将来删除软件时使用。安装指令如下：

   [root@localhost httpd-2.2.9]# make install

   整个过程不报错，即为安装成功。

   安装源码包过程中，如果出现“error”（或“warning”）且安装过程停止，表示安装失败；反之，如果仅出现警告信息，但安装过程还在继续，这并不是安装失败，顶多使软件部分功能无法使用。

注意，如果在 "./configure" 或 "make" 编译中报错，则在重新执行命令前一定要执行 `make clean` 命令，它会清空 Makefile 文件或编译产生的 ".o" 头文件。

## Linux源码包卸载



通过源码包方式安装的各个软件，其安装文件独自保存在 /usr/local/ 目录下的各子目录中。例如，apache 所有的安装文件都保存在 /usr/local/apache2 目录下。这就为源码包的卸载提供了便利。

源码包的卸载，只需要找到软件的安装位置，直接删除所在目录即可，不会遗留任何垃圾文件。需要读者注意的是，在删除软件之前，应先将软件停止服务。

以删除 apache 为例，只需关闭 apache 服务后执行如下命令即可：

[root@localhost ~]# rm -rf /usr/local/apache2/



> 原文链接：https://blog.csdn.net/xinluke/article/details/52330867

# npm安装

> 这个和linux没关系，是node.js的包管理工具npm，在写一个node.js项目时，需要在线安装【包】是，需要注意的

npm的包安装分为本地安装（local）、全局安装（global）两种

npm install grunt # 本地安装
npm install -g grunt-cli # 全局安装

这两种安装方式的区别

本地安装
将安装包放在 ./node_modules 下（运行npm时所在的目录）
可以通过 require() 来引入本地安装的包

全局安装
模块将被下载安装到全局目录中，即Node的安装目录下的node_modules下
可以直接在命令行里使用
通过全局安装的插件不可以通过require() 来引入





>  https://www.cnblogs.com/youyoui/p/10680329.html


# Linux环境变量配置

在自定义安装软件的时候，经常需要配置环境变量，下面列举出各种对环境变量的配置方法。

下面所有例子的环境说明如下：

- 系统：Ubuntu 14.0
- 用户名：uusama
- 需要配置MySQL环境变量路径：/home/uusama/mysql/bin

## Linux读取环境变量

读取环境变量的方法：

- `export`命令显示当前系统定义的所有环境变量
- `echo $PATH`命令输出当前的`PATH`环境变量的值

这两个命令执行的效果如下

```shell
uusama@ubuntu:~$ export
declare -x HOME="/home/uusama"
declare -x LANG="en_US.UTF-8"
declare -x LANGUAGE="en_US:"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="uusama"
declare -x MAIL="/var/mail/uusama"
declare -x PATH="/home/uusama/bin:/home/uusama/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
declare -x SSH_TTY="/dev/pts/0"
declare -x TERM="xterm"
declare -x USER="uusama"

uusama@ubuntu:~$ echo $PATH
/home/uusama/bin:/home/uusama/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

其中`PATH`变量定义了运行命令的查找路径，以冒号`:`分割不同的路径，使用`export`定义的时候可加双引号也可不加。

### Linux环境变量配置方法一：`export PATH`

使用`export`命令直接修改`PATH`的值，配置MySQL进入环境变量的方法:

```shell
export PATH=/home/uusama/mysql/bin:$PATH

# 或者把PATH放在前面
export PATH=$PATH:/home/uusama/mysql/bin
```

注意事项：

- 生效时间：立即生效
- 生效期限：当前终端有效，窗口关闭后无效
- 生效范围：仅对当前用户有效
- 配置的环境变量中不要忘了加上原来的配置，即`$PATH`部分，避免覆盖原来配置

### Linux环境变量配置方法二：`vim ~/.bashrc`

通过修改用户目录下的`~/.bashrc`文件进行配置：

```shell
vim ~/.bashrc

# 在最后一行加上
export PATH=$PATH:/home/uusama/mysql/bin
```

注意事项：

- 生效时间：使用相同的用户打开新的终端时生效，或者手动`source ~/.bashrc`生效
- 生效期限：永久有效
- 生效范围：仅对当前用户有效
- 如果有后续的环境变量加载文件覆盖了`PATH`定义，则可能不生效

### Linux环境变量配置方法三：`vim ~/.bash_profile`

和修改`~/.bashrc`文件类似，也是要在文件最后加上新的路径即可：

```shell
vim ~/.bash_profile

# 在最后一行加上
export PATH=$PATH:/home/uusama/mysql/bin
```

注意事项：

- 生效时间：使用相同的用户打开新的终端时生效，或者手动`source ~/.bash_profile`生效
- 生效期限：永久有效
- 生效范围：仅对当前用户有效
- 如果没有`~/.bash_profile`文件，则可以编辑`~/.profile`文件或者新建一个

### Linux环境变量配置方法四：`vim /etc/bashrc`

该方法是修改系统配置，需要管理员权限（如root）或者对该文件的写入权限：

```shell
# 如果/etc/bashrc文件不可编辑，需要修改为可编辑
chmod -v u+w /etc/bashrc

vim /etc/bashrc

# 在最后一行加上
export PATH=$PATH:/home/uusama/mysql/bin
```

注意事项：

- 生效时间：新开终端生效，或者手动`source /etc/bashrc`生效
- 生效期限：永久有效
- 生效范围：对所有用户有效

### Linux环境变量配置方法五：`vim /etc/profile`

该方法修改系统配置，需要管理员权限或者对该文件的写入权限，和`vim /etc/bashrc`类似：

```shell
# 如果/etc/profile文件不可编辑，需要修改为可编辑
chmod -v u+w /etc/profile

vim /etc/profile

# 在最后一行加上
export PATH=$PATH:/home/uusama/mysql/bin
```

注意事项：

- 生效时间：新开终端生效，或者手动`source /etc/profile`生效
- 生效期限：永久有效
- 生效范围：对所有用户有效

### Linux环境变量配置方法六：`vim /etc/environment`

该方法是修改系统环境配置文件，需要管理员权限或者对该文件的写入权限：

```shell
# 如果/etc/bashrc文件不可编辑，需要修改为可编辑
chmod -v u+w /etc/environment

vim /etc/profile

# 在最后一行加上
export PATH=$PATH:/home/uusama/mysql/bin
```

注意事项：

- 生效时间：新开终端生效，或者手动`source /etc/environment`生效
- 生效期限：永久有效
- 生效范围：对所有用户有效

## Linux环境变量加载原理解析

上面列出了环境变量的各种配置方法，那么Linux是如何加载这些配置的呢？是以什么样的顺序加载的呢？

特定的加载顺序会导致相同名称的环境变量定义被覆盖或者不生效。

### 环境变量的分类

环境变量可以简单的分成用户自定义的环境变量以及系统级别的环境变量。

- 用户级别环境变量定义文件：`~/.bashrc`、`~/.profile`（部分系统为：`~/.bash_profile`）
- 系统级别环境变量定义文件：`/etc/bashrc`、`/etc/profile`(部分系统为：`/etc/bash_profile`）、`/etc/environment`

另外在用户环境变量中，系统会首先读取`~/.bash_profile`（或者`~/.profile`）文件，如果没有该文件则读取`~/.bash_login`，根据这些文件中内容再去读取`~/.bashrc`。

### 测试Linux环境变量加载顺序的方法

为了测试各个不同文件的环境变量加载顺序，我们在每个环境变量定义文件中的第一行都定义相同的环境变量`UU_ORDER`，该变量的值为本身的值连接上当前文件名称。

需要修改的文件如下：

- `/etc/environment`
- `/etc/profile`
- `/etc/profile.d/test.sh`，新建文件，没有文件夹可略过
- `/etc/bashrc`，或者`/etc/bash.bashrc`
- `~/.bash_profile`，或者`~/.profile`
- `~/.bashrc`

在每个文件中的第一行都加上下面这句代码，并相应的把冒号后的内容修改为当前文件的绝对文件名。

```
export UU_ORDER="$UU_ORDER:~/.bash_profile"
```

修改完之后保存，新开一个窗口，然后`echo $UU_ORDER`观察变量的值：

```shell
uusama@ubuntu:~$ echo $UU_ORDER
$UU_ORDER:/etc/environment:/etc/profile:/etc/bash.bashrc:/etc/profile.d/test.sh:~/.profile:~/.bashrc
```

可以推测出Linux加载环境变量的顺序如下：

1. `/etc/environment`
2. `/etc/profile`
3. `/etc/bash.bashrc`
4. `/etc/profile.d/test.sh`
5. `~/.profile`
6. `~/.bashrc`

### Linux环境变量文件加载详解

由上面的测试可容易得出Linux加载环境变量的顺序如下，：

系统环境变量 -> 用户自定义环境变量
`/etc/environment` -> `/etc/profile` -> `~/.profile`

打开`/etc/profile`文件你会发现，该文件的代码中会加载`/etc/bash.bashrc`文件，然后检查`/etc/profile.d/`目录下的`.sh`文件并加载。

```shell
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi
```

其次再打开`~/.profile`文件，会发现该文件中加载了`~/.bashrc`文件。

```shell
# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin directories
PATH="$HOME/bin:$HOME/.local/bin:$PATH"
```

从`~/.profile`文件中代码不难发现，`/.profile`文件**只在用户登录的时候读取一次**，而`/.bashrc`会在每次运行`Shell`脚本的时候读取一次。

### 一些小技巧

可以自定义一个环境变量文件，比如在某个项目下定义`uusama.profile`，在这个文件中使用`export`定义一系列变量，然后在`~/.profile`文件后面加上：`sourc uusama.profile`，这样你每次登陆都可以在Shell脚本中使用自己定义的一系列变量。

也可以使用`alias`命令定义一些命令的别名，比如`alias rm="rm -i"`（双引号必须），并把这个代码加入到`~/.profile`中，这样你每次使用`rm`命令的时候，都相当于使用`rm -i`命令，非常方便。
