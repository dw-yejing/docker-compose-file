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



