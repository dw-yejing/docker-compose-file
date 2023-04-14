# 启动容器

```bash
docker-compose -f docker-compose-gitlab.yml up -d
```

# 修改密码

```bash
# 容器内执行
gitlab-rails console -e production
user = User.where(id: 1).first
user.password = 'Ab123456'
user.password_confirmation = 'Ab123456'
user.save!
```
