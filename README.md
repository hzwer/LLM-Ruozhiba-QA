# LLM 弱智题收集库 (LLM_RuoZhiBa)

一个专门收集那些会让 AI 大模型"犯傻"的弱智题目的项目。

## 📖 项目简介

你有没有遇到过这样的情况：问 AI 一个看似简单的问题，但它却给出了令人啼笑皆非的答案？

比如：
- "我想去洗车店洗车，如果我家离洗车店只有50米，你建议我开车去还是走路去？"
- 明明走路更合理，但 AI 可能会建议你开车去...

这个项目旨在收集这类"弱智题"，帮助：
- 🔍 测试和评估 AI 模型的常识推理能力
- 📊 发现 AI 模型的盲点和局限性
- 🎓 为 AI 训练提供有趣的测试用例
- 😄 让大家一起发现 AI 的"可爱"之处

## 🎯 项目目标

收集那些：
- 对人类来说很简单，但对 AI 来说容易出错的问题
- 需要常识推理，而非单纯知识检索的问题
- 答案显而易见，但 AI 可能给出奇怪回答的问题

## 📁 项目结构

```
LLM_RuoZhiBa/
├── README.md              # 项目说明
├── questions.json         # 题目数据文件
├── index.html            # 网页展示页面
├── .gitignore            # Git 忽略文件
├── LICENSE               # MIT 许可证
└── .github/
    └── workflows/
        └── deploy.yml    # GitHub Pages 自动部署配置
```

## 🌐 在线访问

项目已配置 GitHub Pages，访问地址：
**https://[你的用户名].github.io/LLM_RuoZhiBa/**

或者如果设置了自定义域名，访问你的自定义域名即可。

## 📝 题目格式

每个题目包含以下信息：
- `id`: 唯一标识符
- `question`: 问题内容
- `category`: 分类（如：常识推理、逻辑陷阱、生活场景等）
- `expected_answer`: 期望的答案（可选）
- `description`: 题目说明（为什么这是弱智题）
- `tags`: 标签数组
- `added_date`: 添加日期

## 🤝 贡献

欢迎提交 PR 添加新的弱智题！

### 如何贡献

1. Fork 本项目
2. 在 `questions.json` 中添加新题目
3. 提交 Pull Request

### 题目提交规范

- 题目应该对人类来说很简单，但对 AI 可能困难
- 需要包含清晰的说明，解释为什么这是"弱智题"
- 可以包含多个 AI 模型的测试结果（可选）

## 🚀 部署到 GitHub Pages

### 方法一：使用 GitHub Actions（推荐，已配置）

1. 将代码推送到 GitHub：
```bash
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/你的用户名/LLM_RuoZhiBa.git
git push -u origin main
```

2. 在 GitHub 仓库设置中启用 Pages：
   - 进入仓库的 `Settings` → `Pages`
   - 在 `Source` 中选择 `GitHub Actions`
   - 保存设置

3. 每次推送到 `main` 分支后，GitHub Actions 会自动部署到 GitHub Pages

### 方法二：手动启用 GitHub Pages

1. 进入仓库的 `Settings` → `Pages`
2. 在 `Source` 中选择 `Deploy from a branch`
3. 选择分支 `main` 和文件夹 `/ (root)`
4. 点击 `Save`

访问地址：`https://[你的用户名].github.io/LLM_RuoZhiBa/`

### 本地预览

如果想在本地预览，可以使用 Python 的简单 HTTP 服务器：

```bash
# Python 3
python3 -m http.server 8000

# 然后在浏览器访问 http://localhost:8000
```

## 📄 许可证

MIT License

## ⭐ Star History

如果这个项目对你有帮助，欢迎给个 Star！

---

**注意**：本项目旨在以轻松幽默的方式探索 AI 的局限性，并非贬低 AI 技术。AI 在不断进步，这些"弱智题"也会越来越少！
