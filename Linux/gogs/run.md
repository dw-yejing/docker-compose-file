# Gogs

- https://github.com/gogs/gogs
- https://gogs.io

一款极易搭建的自助 Git 服务。
Gogs 的目标是打造一个最简单、最快速和最轻松的方式搭建自助 Git 服务。
使用 Go 语言开发使得 Gogs 能够通过独立的二进制分发，并且支持 Go 语言支持的 所有平台，包括 Linux、Mac OS X、Windows 以及 ARM 平台。

### 部署

```shell
docker-compose -f docker-compose.yml -p gogs up -d
```

访问地址：[`http://ip地址:10880`](http://127.0.0.1:10880)

自动配置
![img_1.png](images/gogs-01.png)

![img.png](images/gogs-02.png)

# 备份 & 迁移

## 1. 备份代码仓库

```bash
tar -zcvf gogs-repositories.tar.gz gogs-repositories
```

## 2. 备份数据库

```bash
sudo mysqldump -h localhost -u gogs -P 3306 --no-tablespaces -p gogs> /home/tgubuntu/gogs.sql
```

## 3. 恢复

```bash
# 还原代码仓库，将gogs压缩包解压，放到对应位置
...
# 还原数据库
mysql --default-character-set=utf8mb4 -u$USER -p$PASS $DATABASE <gitea-db.sql
# 重启docker容器
```

## 4. 常见问题

```bash
# 迁移后会出现不能push的现象，报错pre-receive找不到，使用Gogs管理员账号登录Gogs，刷新hooks
  管理面板->控制面板->管理员操作->重新同步所有仓库的pre-receive、update和post-receive钩子->执行

```

