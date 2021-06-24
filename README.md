# openGauss-tools-ora2og

#### 介绍
ora2og是一个将Oracle数据库迁移至openGauss的工具，主要编程语言为perl，通过perl DBI模块连接Oracle数据库，自动扫描并提取其中的对象结构及数据，产生SQL脚本，通过手动或自动的方式应用到openGauss。此外，工具还提供丰富配置项，用户可以自定义迁移行为。

ora2og初始代码源自ora2pg，版本为release v21.1：https://github.com/darold/ora2pg/tree/v21.1。

#### 优秀特性
* 支持导出数据库绝大多数对象类型，包括表、视图、序列、索引、外键、约束、函数、存储过程等。

* 提供PL/SQL到PL/PGSQL语法的自动转换，一定程度避免了人工修正。

* 可生成迁移报告，包括迁移难度评估、人天估算。

* 可选对导出数据进行压缩，节约磁盘开销。

* 配置选项丰富，可自定义迁移行为。


#### 安装教程

1. 安装依赖
由于编程语言为perl，需要安装所需perl模块。此外，还需要DBI、DBD::Pg、DBD::Oracle连接源和目标数据库。请在root用户下执行。
```shell
yum install -y perl-ExtUtils-CBuilder perl-ExtUtils-MakeMaker
yum install perl-CPAN
perl -MCPAN -e 'install DBI'
perl -MCPAN -e 'install DBD::Pg'
```
安装DBD::Oracle，需要先安装Oracle Instant Client或者本地已安装Oracle数据库。
```shell
# 从Oracle官方下载并安装Oracle Instant Client(x86版本,ARM环境下请下载对应的RPM包)
rpm -ivh oracle-instantclient19.11-basic-19.11.0.0.0-1.x86_64.rpm
rpm -ivh oracle-instantclient19.11-devel-19.11.0.0.0-1.x86_64.rpm
rpm -ivh oracle-instantclient19.11-jdbc-19.11.0.0.0-1.x86_64.rpm
rpm -ivh oracle-instantclient19.11-sqlplus-19.11.0.0.0-1.x86_64.rpm
# 设置环境变量ORACLE_HOME
export ORACLE_HOME=/usr/lib/oracle/19.11/client64/
# 或者本地已安装有Oracle数据库
ORACLE_HOME如下设置
export ORACLE_HOME=/opt/oracle/product/19c/dbhome_1
export LD_LIBRARY_PATH=$ORACLE_HOME/lib
# 安装DBD:Oracle
perl -MCPAN -e 'install DBD::Oracle'
```
2. 安装Ora2Pg
<you_install_dir>为目标安装路径，<source_code_dir>为下载的代码路径。
```shell
# 进到代码目录下
perl Makefile.PL PREFIX=<your_install_dir>
make && make install
# 设置环境变量，查看是否安装成功
export PERL5LIB=<source_code_dir>/lib
export PATH=$PATH:<your_install_dir>/usr/local/bin
ora2pg --help
```

#### 使用说明

1. 如该文章所示：https://mp.weixin.qq.com/s/hMqaSes0hQvzmJw0kmXDtg

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request
