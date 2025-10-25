# GitHub 推送配置指南

## 创建个人访问令牌 (Personal Access Token)

1. 登录您的GitHub账户 (https://github.com)
   - 邮箱：327830972@qq.com
   - 用户名：FLJY-2025
2. 点击右上角头像，选择"Settings" (设置)
3. 在左侧菜单中选择"Developer settings" (开发者设置)
4. 选择"Personal access tokens" (个人访问令牌)
5. 点击"Generate new token" (生成新令牌)
6. 在"Note"字段中输入描述性名称，例如"FLJY-website-deploy"
7. 设置过期时间（可选）
8. 在权限部分，至少勾选以下权限：
   - `repo` - 完全控制私人和公共仓库
9. 点击页面底部的"Generate token" (生成令牌)
10. 复制生成的令牌并妥善保管（这是唯一能看到令牌的机会）

## 配置Git使用个人访问令牌

有两种方式配置Git使用个人访问令牌：

### 方法一：使用凭证助手（推荐）

```bash
# 全局配置凭证助手
git config --global credential.helper store

# 推送代码时会提示输入用户名和密码
# 用户名：FLJY-2025
# 密码：您刚刚创建的个人访问令牌
git push -u origin main
```

### 方法二：在URL中直接包含令牌（不太安全）

```bash
# 替换YOUR_TOKEN为实际的令牌
git remote set-url origin https://YOUR_TOKEN@github.com/FLJY-2025/FLJY.git

# 然后正常推送
git push -u origin main
```

## Git用户信息配置

为了确保提交历史显示正确的作者信息，我们已经为您配置了Git用户信息：

```bash
git config --global user.name "FLJY-2025"
git config --global user.email "327830972@qq.com"
```

您可以通过以下命令验证配置：

```bash
git config --list | grep user
```

## 验证配置

推送成功后，您应该能在GitHub仓库中看到最新的代码提交。

## 故障排除

如果仍然遇到问题：

1. 检查您的GitHub账户是否已被添加为仓库协作者
2. 确认个人访问令牌具有足够的权限
3. 验证仓库URL是否正确：
   ```bash
   git remote -v
   ```
4. 如果需要重置凭证：
   ```bash
   # 清除存储的凭证
   git config --global --unset credential.helper
   # 重新设置
   git config --global credential.helper store
   ```

---
注意：请确保保护好您的个人访问令牌，不要将其提交到代码仓库中。