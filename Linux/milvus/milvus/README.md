# installation

```bash
# 下载docker-compose安装文件
wget https://github.com/milvus-io/milvus/releases/download/v2.2.8/milvus-standalone-docker-compose.yml -O milvus-docker-compose.yml

# 启动容器
docker-compose up -d

# 开启鉴权 修改 milvus.yaml
common.security.authorizationEnabled: true

```


```bash
# 具体安装方法 参考: https://github.com/zilliztech/attu/blob/main/docker-compose.yml
1. 修改端口，配置数据卷，修改minio密码和milvus配置
2. 创建容器
```

# 运行

```bash
docker-compose -f milvus_docker_compose.yml up -d
```

# client

## 安装Attu客户端

```
wget https://github.com/zilliztech/attu/releases/download/v2.2.8/attu-Setup-2.2.8.exe
```

访问 http://ip:19530

初始密码为 `root`/`Milvus`,首次登录后需要更新密码

# 常见问题

```json
[{
    "Q": "心跳检查端口配置",
    "A": "容器内端口"
},{
    "Q": "milvus 无法启动",
    "A": "建议检查minio的端口、账密等信息"
},{
    "Q": "关于minio端口问题",
    "A": "除了minio容器端口映射需要容器外端口，其他都是容器内API端口 9000"
}]
```
