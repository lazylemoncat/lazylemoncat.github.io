## 生成密钥

```bash
# 1. 生成密钥对（全程回车保持默认）
ssh-keygen -t rsa -b 4096

# 预期输出：
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): [直接回车]
Enter passphrase (empty for no passphrase): [直接回车]
Enter same passphrase again: [直接回车]

# 2. 验证生成结果
ls -lah ~/.ssh/id_rsa*  # 应看到id_rsa和id_rsa.pub

# 3. 将公钥添加到授权列表
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys

# 4. 设置权限（关键步骤！）
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
chmod 600 ~/.ssh/id_rsa
```



## 验证密钥是否生效

```bash
ssh -o StrictHostKeyChecking=no root@localhost
```

## 查看私钥内容

```bash
cat /root/.ssh/id_rsa
```

