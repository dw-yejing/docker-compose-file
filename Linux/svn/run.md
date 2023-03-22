# 启动容器

```bash
docker-compose -f docker-compose-svn.yml up -d
docker exec -t svn-server htpasswd -cb /etc/subversion/passwd admin admin123
```

# # 创建svn挂载目录并授权

```bash
touch /home/docker/docker-config/svn/conf/subversion-access-control
chmod 777 -R /home/docker/docker-config/svn/conf
chmod 777 -R /home/docker/docker-config/svn/repo
```

# 访问服务

```bash
ip:port/svnadmin
```

# 服务配置

```bash
Subversion authorization file： /etc/subversion/subversion-access-control
User authentication file (SVNUserFile)：/etc/subversion/passwd
Parent directory of the repositories (SVNParentPath)：/home/svn
Subversion client executable：/usr/bin/svn
Subversion admin executable：/usr/bin/svnadmin
```
