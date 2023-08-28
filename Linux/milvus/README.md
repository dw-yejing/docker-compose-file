# installation

## 1 下载配置文件

```bash
wget https://raw.githubusercontent.com/milvus-io/milvus/v2.2.13/configs/milvus.yaml
```

- 开启鉴权

  ```yml
  common:
  	security:
  		authorizationEnabled: true
  ```

## 2 下载docker-compose安装文件

```bash
wget https://github.com/milvus-io/milvus/releases/download/v2.2.8/milvus-standalone-docker-compose.yml -O milvus-docker-compose.yml
```

- 增加配置文件数据卷映射

  ```yml
   volumes:
        - /home/docker/app/milvus/milvus.yaml:/milvus/configs/milvus.yaml
  ```

## 3 运行docker-compose

```bash
docker-compose -f milvus-docker-compose.yml up -d
```

# client

## 安装Attu客户端

```
wget https://github.com/zilliztech/attu/releases/download/v2.2.8/attu-Setup-2.2.8.exe
```

初始密码为 `root`/`Milvus`,首次登录后需要更新密码