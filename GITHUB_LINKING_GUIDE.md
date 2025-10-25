# GitHub 仓库链接指南

## 当前状况
您的本地项目已经是一个Git仓库，并且已经连接到远程仓库 `https://github.com/FLJY-2025/FLJY.git`。
但是推送时出现权限问题，需要重新配置访问凭证。

## 解决方案一：使用 HTTPS 和个人访问令牌（推荐）

1. 在 GitHub 上生成个人访问令牌：
   - 登录 GitHub 账户
   - 点击右上角头像，选择 "Settings"
   - 在左侧菜单选择 "Developer settings"
   - 选择 "Personal access tokens" → "Tokens (classic)"
   - 点击 "Generate new token" → "Generate new token (classic)"
   - 设置令牌名称（如："FLJY-repo-access"）
   - 选择适当的权限（至少需要 repo 权限）
   - 点击 "Generate token"
   - 复制生成的令牌（请妥善保存，只显示一次）

2. 更新远程仓库URL以包含您的凭据：
   ```bash
   git remote set-url origin https://<your-username>:<your-token>@github.com/FLJY-2025/FLJY.git
   ```

3. 推送更改：
   ```bash
   git push origin main
   ```

## 解决方案二：使用 SSH 密钥（更安全）

1. 生成 SSH 密钥对（如果还没有）：
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

2. 启动 ssh-agent 并添加密钥：
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   ```

3. 复制公钥内容：
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

4. 在 GitHub 上添加 SSH 密钥：
   - 登录 GitHub 账户
   - 点击右上角头像，选择 "Settings"
   - 在左侧菜单选择 "SSH and GPG keys"
   - 点击 "New SSH key"
   - 粘贴公钥内容并保存

5. 更改远程仓库URL为SSH格式：
   ```bash
   git remote set-url origin git@github.com:FLJY-2025/FLJY.git
   ```

6. 推送更改：
   ```bash
   git push origin main
   ```

## 常用Git命令

- 查看当前状态：`git status`
- 添加更改：`git add .`
- 提交更改：`git commit -m "提交信息"`
- 推送更改：`git push origin main`
- 拉取最新更改：`git pull origin main`

如有任何问题，请联系技术支持。