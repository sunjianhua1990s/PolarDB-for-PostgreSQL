# 快速上手

仅需单台计算机，同时满足以下要求，就可以快速开启您的 PolarDB 之旅：

- CPU 架构为 AMD64 / ARM64
- 可用内存 4GB 以上
- 已安装 [Docker](https://www.docker.com/)
  - Ubuntu：[在 Ubuntu 上安装 Docker Engine](https://docs.docker.com/engine/install/ubuntu/)
  - Debian：[在 Debian 上安装 Docker Engine](https://docs.docker.com/engine/install/debian/)
  - CentOS：[在 CentOS 上安装 Docker Engine](https://docs.docker.com/engine/install/centos/)
  - RHEL：[在 RHEL 上安装 Docker Engine](https://docs.docker.com/engine/install/rhel/)
  - Fedora：[在 Fedora 上安装 Docker Engine](https://docs.docker.com/engine/install/fedora/)
  - macOS（支持 M1 芯片）：[在 Mac 上安装 Docker Desktop](https://docs.docker.com/desktop/mac/install/)，并建议将内存调整为 4GB

从 DockerHub 上拉取 PolarDB for PostgreSQL 的 [开发镜像](https://hub.docker.com/r/polardb/polardb_pg_devel/tags)，创建、运行并进入容器：

```bash
# 拉取 PolarDB 开发镜像
docker pull polardb/polardb_pg_devel
# 创建、运行并进入容器
docker run -it \
    --cap-add=SYS_PTRACE --privileged=true \
    --name polardb_pg \
    polardb/polardb_pg_devel bash
```

进入容器后，从 GitHub 拉取最新的稳定代码，快速编译部署最简单的 PolarDB 实例并进行验证：

```bash
# 代码拉取
git clone -b POLARDB_11_STABLE https://github.com/ApsaraDB/PolarDB-for-PostgreSQL.git
cd PolarDB-for-PostgreSQL
# 编译部署
./polardb_build.sh
# 验证
psql -h 127.0.0.1 -c 'select version();'
            version
--------------------------------
 PostgreSQL 11.9 (POLARDB 11.9)
(1 row)
```
