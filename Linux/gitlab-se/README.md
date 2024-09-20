# 备份&还原

```bash
# 创建备份，默认备份路径:/var/opt/gitlab/backups
docker exec -t <container name> gitlab-backup create

# 进行还原
docker exec -it <name of container> gitlab-ctl stop puma
docker exec -it <name of container> gitlab-ctl stop sidekiq

# Verify that the processes are all down before continuing
docker exec -it <name of container> gitlab-ctl status

# Run the restore. NOTE: "_gitlab_backup.tar" is omitted from the name
docker exec -it <name of container> chmod 777 /var/opt/gitlab/backups/11493107454_2018_04_25_10.6.4-ce
docker exec -it <name of container> gitlab-backup restore BACKUP=11493107454_2018_04_25_10.6.4-ce

# Restart the GitLab container
docker restart <name of container>

# Check GitLab
docker exec -it <name of container> gitlab-rake gitlab:check SANITIZE=true
```

# 常见问题及解决方法

- 端口无法访问
  ```
  version: '3'
  services:
    gitlab:
      image: 'gitlab/gitlab-ce:latest'
      restart: always
      privileged: true
      container_name: gitlab
      environment:
        GITLAB_OMNIBUS_CONFIG: |
          external_url 'http://192.168.113.48:9010' 
          gitlab_rails['gitlab_shell_ssh_port'] = 9011
      ports:
        - '9010:9010' # 注意宿主机和容器内部的端口要一致，否则external_url无法访问
        - '9011:22'
  ```

这里`external_url 'http://192.168.113.48:9010'`和 - '9010:9010' 和容器内外的端口要一致，否则external_url无法访问



- Docker安装gitlab 运行一段时间后报500/502

  ```yml
  原因: 共享内存溢出
  查看日志: tail -fn 100 /var/log/gitlab/gitlab-rails/production.log
  解决方法: 配置shm_size
  ```

  ```yml
  version: '3'
  services:
    gitlab:
      image: 'gitlab/gitlab-ce:latest'
      restart: always
      shm_size: 20G
  
  ```

  
