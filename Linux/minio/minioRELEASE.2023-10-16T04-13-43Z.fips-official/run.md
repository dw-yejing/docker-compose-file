### MinIO

```shell
docker-compose -f docker-compose-minio.yml up -d
```

访问地址：[`ip地址:9001/minio`](http://www.zhengqingya.com:9001/minio)
登录账号密码：`root/password`

默认api端口 9000；console端口（web端口）随机生成，所以需要手动指定。

minio  访问 http://ip:<api_port>/<bucket_name>/<file_name>
