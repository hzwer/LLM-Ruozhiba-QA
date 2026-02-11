# 部署指南

## 📦 将项目部署到 GitHub Pages

### 步骤 1: 在 GitHub 上创建仓库

1. 登录 GitHub
2. 点击右上角的 `+` → `New repository`
3. 仓库名填写：`LLM-Ruozhiba-QA`（推荐）或你喜欢的名字
4. 选择 `Public`（GitHub Pages 免费版需要公开仓库）
5. **不要**勾选 "Initialize this repository with a README"（因为本地已有代码）
6. 点击 `Create repository`

### 步骤 2: 推送代码到 GitHub

在项目目录下执行：

```bash
# 如果还没有初始化 git（已经初始化了可以跳过）
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit: LLM 弱智题收集库"

# 重命名分支为 main（如果还没有）
git branch -M main

# 添加远程仓库（替换成你的 GitHub 用户名）
git remote add origin https://github.com/你的用户名/LLM-Ruozhiba-QA.git

# 推送代码
git push -u origin main
```

### 步骤 3: 启用 GitHub Pages

#### 方法一：使用 GitHub Actions（推荐，已自动配置）

1. 进入你的 GitHub 仓库页面
2. 点击 `Settings`（设置）
3. 在左侧菜单找到 `Pages`
4. 在 `Source` 部分，选择 `GitHub Actions`
5. 保存设置

之后每次推送到 `main` 分支，GitHub Actions 会自动部署。

#### 方法二：使用分支部署

1. 进入 `Settings` → `Pages`
2. 在 `Source` 中选择 `Deploy from a branch`
3. 选择：
   - Branch: `main`
   - Folder: `/ (root)`
4. 点击 `Save`

### 步骤 4: 访问你的网站

部署完成后（通常需要 1-2 分钟），访问：

```
https://你的用户名.github.io/LLM-Ruozhiba-QA/
```

例如，如果你的 GitHub 用户名是 `zhangsan`，访问地址就是：
```
https://zhangsan.github.io/LLM-Ruozhiba-QA/
```

### 步骤 5: 更新内容

以后每次更新题目，只需要：

```bash
# 修改 questions.json 或其他文件
git add .
git commit -m "添加新题目"
git push
```

GitHub Actions 会自动重新部署（方法一），或者 GitHub Pages 会自动更新（方法二）。

## 🔧 本地预览

在推送到 GitHub 之前，可以在本地预览：

```bash
# 使用 Python 3
python3 -m http.server 8000

# 或者使用 Node.js 的 http-server
npx http-server -p 8000
```

然后在浏览器访问：`http://localhost:8000`

## ❓ 常见问题

### Q: 为什么访问 404？

A: 
- 检查 GitHub Pages 是否已启用
- 确认仓库是 Public（免费版需要）
- 等待 1-2 分钟让部署完成
- 检查 URL 是否正确（注意大小写）

### Q: 为什么页面显示但数据加载失败？

A: 
- 检查浏览器控制台是否有 CORS 错误
- 确认 `questions.json` 文件已正确提交
- 检查文件路径是否正确

### Q: 如何自定义域名？

A: 
1. 在仓库根目录创建 `CNAME` 文件，内容是你的域名
2. 在域名服务商添加 CNAME 记录指向 `你的用户名.github.io`
3. 在 GitHub Pages 设置中配置自定义域名

## 📝 关于仓库名

推荐使用 `LLM-Ruozhiba-QA`，这个名字：
- ✅ 外国人容易理解（Trick Questions = 陷阱题/诡计题）
- ✅ 专业且有趣
- ✅ 准确描述了项目内容

其他可选名称：
- `AI-Common-Sense-Failures` - AI 常识失败案例
- `LLM-Confusing-Questions` - 让 LLM 困惑的题目
- `AI-Fool-Me-Questions` - 能"骗到"AI 的题目

## 📝 注意事项

- GitHub Pages 免费版只支持静态网站
- 仓库必须是 Public（或使用 GitHub Pro）
- 每次推送后，部署需要 1-2 分钟
- 如果使用 GitHub Actions，首次部署可能需要更长时间
