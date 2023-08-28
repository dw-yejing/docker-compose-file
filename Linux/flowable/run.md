### Flowable - 业务流程引擎

```shell
docker-compose -f docker-compose-flowable.yml -p flowable up -d
```

可视化界面访问地址：[`http://ip地址:9004/flowable-ui`](http://www.zhengqingya.com:9004/flowable-ui)
默认登录账号密码：`admin/test`

```
flowable-ui:
	url: http://host:ip/flowable-ui
	username: admin
	password: test
flowable-rest:
	url: http://host:ip/flowable-ui
	username: rest-admin
	password: test
```
