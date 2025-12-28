## installation openGauss Server on a Single Node

```shell
$ cat /etc/os-release
openEuler 24.03 LTS SP2
```

```shell
$ python3 --version
```

```shell
timedatectl
ls -l /etc/localtime
localectl
```

```shell
dnf update -y
dnf install -y wget nano vim
```

```shell
groupadd dbgroup
useradd -g dbgroup omm
passwd Super@123
```

```shell
wget https://opengauss.obs.cn-south-1.myhuaweicloud.com/6.0.2/openEuler22.03/x86/openGauss-All-6.0.2-openEuler22.03-x86_64.tar.gz

mkdir -p /opt/openGauss

tar -xf openGauss-*.tar.gz -C /opt/openGauss

cd /opt/openGauss/simpleInstall
sh install.sh -w 'Admin@123'
```

```shell
su - omm
ps -ef | grep gaussdb
gs_ctl query -D ~/gaussdb/data/single_node
```

```shell
gsql -d postgres -p 5432
```

> omm — Database Super Admin  
```shell
CREATE USER omm WITH PASSWORD 'Super@123';
ALTER USER omm SYSADMIN;

\du
```

> admin — Database Admin  
```shell
CREATE USER admin WITH PASSWORD 'Admin@123';
ALTER USER admin CREATEROLE CREATEDB;
```

> user1 — Application User  
```shell
CREATE USER user1 WITH PASSWORD 'User@123';
GRANT CONNECT ON DATABASE demo_db TO user1;
```
