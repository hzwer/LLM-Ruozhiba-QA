# LLM Ruozhiba QA (LLM 弱智题收集库)

针对 LLM 定制的弱智吧问题 [在线网页](https://hzwer.github.io/LLM-Ruozhiba-QA/)

## 📝 题目格式

题目文件存放在 `questions/` 文件夹下，每个题目一个 JSON 文件（如 `ruozhiba-0001.json`）。

每个题目包含以下信息：
- `id`: 唯一标识符
- `question`: 问题内容
- `category`: 分类
- `description`: 题目说明
- `kimi_answer`: Kimi (K2.5 Fast) 的回答链接
- `kimi_excerpt`: Kimi (K2.5 Fast) 的回答精华摘录
- `stepfun_answer`: Step 3.5 Flash 的回答链接
- `stepfun_excerpt`: Step 3.5 Flash 的回答精华摘录

系统会自动扫描 `questions/` 文件夹下的所有 JSON 文件（排除 `index.json`）并展示。只需在 `questions/` 文件夹下创建符合格式的 JSON 文件即可。

## 🤝 贡献

欢迎提交 PR 添加新的弱智题！

如果你嫌麻烦，想好你的题，然后提个 issue 即可

如果你愿意帮项目者直接生成好放进来：

1. Fork 本项目
2. 在 `questions/` 文件夹下创建新的 JSON 文件
3. 提交 Pull Request

系统会自动识别并展示新添加的题目文件。

## 📄 许可证

MIT License

---

**注意**：本项目旨在以轻松幽默的方式探索 AI 的局限性，并非贬低 AI 技术。
