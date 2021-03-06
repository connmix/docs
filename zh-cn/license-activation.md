# 激活授权

线上部署需要先在 `https://connmix.com` 获的许可证授权。

1. 注册账号
2. 创建应用
3. 免费获取激活码
4. 将激活码输入到 `conf/connmix.yaml` 配置文件中
5. 启动引擎就会激活许可证，并且绑定`IP`，所以请不要在开发环境(动态IP)中激活。

```yaml
licenses:
  activation_code: ***
  server: https://connmix.com
```

## 授权高可用

- 授权成功后，许可证授权信息会保存在本地，通常有效期为 `14` 天，因此即便 `https://connmix.com` 被攻击依然不会影响到服务的执行。
- 即便攻击超过 `14` 天，我们也会提供备用站点激活。
