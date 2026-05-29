# openGauss-tools-ora2og

#### Introduction
ora2og is a tool for migrating data from Oracle to openGauss. It uses Perl as its main programming language and connects to Oracle through the Perl DBI module. It automatically scans and extracts object structures and data from Oracle, generates SQL scripts, and applies the scripts to openGauss manually or automatically. In addition, it provides various configuration options for you to customize migration.

The initial code of ora2og is derived from ora2pg and the version release is v21.1: https://github.com/darold/ora2pg/tree/v21.1.

#### Excellent Features
* Supports exporting most types of database objects, including tables, views, sequences, indexes, foreign keys, constraints, functions, stored procedures, and others.

* Automatically converts the PL/SQL syntax to the PL/pgSQL syntax, avoiding manual modification to some extent.

* Generates migration reports, containing migration difficulty evaluation and person-day estimation.

* Compresses exported data to reduce disk overhead as required.

* Provides various configuration items, allowing you to customize migration operations.


#### Installation

1. Install dependencies.
The programming language is Perl. Therefore, you need to install the required Perl module. You also need to install DBI, DBD::Pg, and DBD::Oracle to connect to the source and target databases. Run the command as the root user.
```shell
yum install -y perl-ExtUtils-CBuilder perl-ExtUtils-MakeMaker
yum install perl-CPAN
perl -MCPAN -e 'install DBI'
perl -MCPAN -e 'install DBD::Pg'
```
Before installing DBD::Oracle, ensure that Oracle Instant Client has been installed or the Oracle database has been installed locally.
```shell
# Download Oracle Instant Client from the Oracle official website and install it. (For the x86 ARM, download the RPM package)
rpm -ivh oracle-instantclient19.11-basic-19.11.0.0.0-1.x86_64.rpm
rpm -ivh oracle-instantclient19.11-devel-19.11.0.0.0-1.x86_64.rpm
rpm -ivh oracle-instantclient19.11-jdbc-19.11.0.0.0-1.x86_64.rpm
rpm -ivh oracle-instantclient19.11-sqlplus-19.11.0.0.0-1.x86_64.rpm
# Set the environment variable ORACLE_HOME.
export ORACLE_HOME=/usr/lib/oracle/19.11/client64/
# The Oracle database has been installed on the local host.
Set ORACLE_HOME as follows:
export ORACLE_HOME=/opt/oracle/product/19c/dbhome_1
export LD_LIBRARY_PATH=$ORACLE_HOME/lib
# Install DBD:Oracle.
perl -MCPAN -e 'install DBD::Oracle'
```
2. Installing Ora2Pg
<you_install_dir> indicates the target installation path, and <source_code_dir> indicates the code download path.
```shell
# Go to the code directory.
perl Makefile.PL PREFIX=<your_install_dir>
make && make install
# Configure environment variables and check whether the installation is successful.
export PERL5LIB=<source_code_dir>/lib
export PATH=$PATH:<your_install_dir>/usr/local/bin
ora2pg --help
```

#### Instruction

1. As shown in the article: https://mp.weixin.qq.com/s/hMqaSes0hQvzmJw0kmXDtg

#### Contributions

1.  Fork this repository.
2.  Create a Feat_xxx branch.
3.  Commit code.
4.  Create a pull request (PR).
