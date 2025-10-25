# Vercel 自定义域名配置指南

## 添加自定义域名到Vercel项目

1. 登录您的Vercel账户 (https://vercel.com)
2. 进入您的项目 "fljy-website"
3. 点击 "Settings" (设置) 标签
4. 在左侧菜单中选择 "Domains" (域名)
5. 点击 "Add" (添加) 按钮
6. 输入您的域名: `www.fljytrain.cn`
7. 点击 "Add" 确认添加

## DNS配置

添加域名后，Vercel会提供DNS配置指导。通常有两种方式：

### 方式一：使用CNAME记录（推荐）

如果您希望使用子域名（如 www.fljytrain.cn）:

1. 登录您的DNS提供商管理面板（通常是您的域名注册商提供的）
2. 添加一条CNAME记录：
   - Name: `www`
   - Value: `cname.vercel-dns.com`
   - TTL: 保持默认或设置为3600秒

### 方式二：使用A记录

如果您希望直接使用根域名（fljytrain.cn）:

1. 登录您的DNS提供商管理面板
2. 添加两条A记录：
   - Name: `@` (或留空，取决于提供商)
   - Values: 
     - `76.76.21.21`
     - `76.76.21.22`
   - TTL: 保持默认或设置为3600秒

## 验证配置

1. 在Vercel域名设置页面，等待DNS配置生效（可能需要几分钟到几小时）
2. 当状态变为 "Valid Configuration" 时，表示配置成功
3. 您可以通过访问 `www.fljytrain.cn` 来测试域名是否正常工作

## HTTPS证书

Vercel会自动为您的自定义域名配置SSL证书，您无需额外操作。

## 故障排除

如果域名配置遇到问题：

1. 检查DNS记录是否正确配置
2. 确认DNS更改已在全球范围内传播（可以使用 `nslookup` 或 `dig` 命令检查）
3. 在Vercel控制台查看域名状态和错误信息
4. 确保没有其他服务占用了相同的域名配置

## 注意事项

- DNS更改可能需要几分钟到48小时才能在全球范围内生效
- 如果您同时配置了根域名和www子域名，建议设置重定向规则
- Vercel会自动处理HTTPS证书的申请和续期

---
配置完成后，您的网站将可以通过 www.fljytrain.cn 访问。