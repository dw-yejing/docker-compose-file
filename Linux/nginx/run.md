### Nginx

```shell
# 运行
docker-compose -f nginx-docker-compose.yml -p nginx up -d

# 进入容器
docker exec -it nginx /bin/bash

# nginx修改配置后重载
nginx -s reload
```

访问地址：[`ip地址:80`](http://www.zhengqingya.com:80)
