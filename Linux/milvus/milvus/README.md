# installation

```bash
# 下载配置文件
wget https://raw.githubusercontent.com/milvus-io/milvus/v2.2.13/configs/milvus.yaml

# 开启鉴权 修改 milvus.yaml
common.security.authorizationEnabled: true

# 下载docker-compose安装文件
wget https://github.com/milvus-io/milvus/releases/download/v2.2.8/milvus-standalone-docker-compose.yml -O milvus-docker-compose.yml

```

```bash
# 具体安装方法
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
},{
    "Q": "客户端连接不上",
    "A": "milvus 服务器和客户端版本要一致，否则无法访问。建议在docker-compose中集成web attu" 
}]
```
