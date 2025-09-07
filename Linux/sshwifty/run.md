# Introduction
Web ssh 客户端

# 设置 sshwifty 密码

可以通过指定环境变量设置密码，eg. SSHWIFTY_SHAREDKEY=Admin.ssh#2025

# 低浏览器兼容

报错提示：got error "TypeError: Cannot read property 'importKey' of undefined"

解决方案：该错误表明Sshwifty的通信协议依赖WebCrypt API加密功能，旧版浏览器可能不支持此API，或新版浏览器在非安全上下文（非HTTPS环境）会禁用该API。建议通过反向代理或直接配置HTTPS服务，确保以https://形式访问Sshwifty即可解决此问题，此举在局域网环境中同样具备安全性优势。

```bash
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 3650 -nodes

docker run --rm -itd \
  -p 8182:8182 \
  -e SSHWIFTY_SHAREDKEY=123456 \
  -e SSHWIFTY_DOCKER_TLSCERT="$(cat cert.pem)" \
  -e SSHWIFTY_DOCKER_TLSCERTKEY="$(cat key.pem)" \
  --name sshwifty \
  niruix/sshwifty:latest

```

# Build
```bash
docker-compose -f sshwifty-docker-compoose.yml up -d
```

# Visit

http://localhost:8182
