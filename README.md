# LLM Ruozhiba QA (LLM 弱智题收集库)

一个专门收集那些会让 AI 大模型"犯傻"的弱智题目的项目。

## 📖 项目简介

你有没有遇到过这样的情况：问 AI 一个看似简单的问题，但它却给出了令人啼笑皆非的答案？

比如：
- "我想去洗车店洗车，如果我家离洗车店只有50米，你建议我开车去还是走路去？"
- 虽然距离很近，但必须开车去，因为要洗车。某些 AI 可能会建议走路，忽略了"洗车"这个前提条件...

这个项目旨在收集这类"弱智题"，帮助测试和评估 AI 模型的常识推理能力。

## 🌐 在线访问

**https://hzwer.github.io/LLM-Ruozhiba-QA/**

## 📝 题目格式

题目文件存放在 `questions/` 文件夹下，每个题目一个 JSON 文件（如 `car-wash.json`, `example-question.json`）。

每个题目包含以下信息：
- `id`: 唯一标识符（建议使用两个单词，用连字符连接，如 `car-wash`）
- `question`: 问题内容
- `category`: 分类
- `description`: 题目说明
- `added_date`: 添加日期
- `difficulty`: 难度（可选）
- `chatgpt_answer`: ChatGPT 的回答（链接）
- `stepfun_answer`: Stepfun 的回答（链接）

`questions/index.json` 文件列出了所有题目文件名，用于加载题目。

## 🤝 贡献

欢迎提交 PR 添加新的弱智题！

1. Fork 本项目
2. 在 `questions/` 文件夹下创建新的 JSON 文件，文件名和 id 使用两个单词（用连字符连接，如 `car-wash.json`，id 为 `"car-wash"`）
3. 在 `questions/index.json` 中添加新文件名
4. 提交 Pull Request

题目应该对人类来说很简单，但对 AI 可能困难。

## 📄 许可证

MIT License

---

**注意**：本项目旨在以轻松幽默的方式探索 AI 的局限性，并非贬低 AI 技术。
