# Codex GitHub Handoff

这个仓库用于在 ChatGPT 网页版与 Codex 之间交接工作。代码、文档和任务结果都通过 Git 分支保存；聊天里只传递仓库名、分支名、提交号和简短目标。

## 推荐工作流

1. 网页版发起任务时，告诉 Codex 仓库、基准分支和目标。
2. Codex 为任务创建独立分支，例如 `codex/add-login-page`。
3. Codex 完成修改和验证后提交并推送该分支。
4. Codex 在最终回复中报告：仓库、分支、提交号、验证结果。
5. 网页版或另一个 Codex 会话从该分支继续，而不是重新接收完整代码和长篇上下文。

## 网页版提示词模板

```text
请在 GitHub 仓库 OWNER/REPO 中继续工作。
基准分支：main
如果已有交接分支，请先读取该分支的 HANDOFF.md 和最近提交。
任务：<写目标>

完成后请：
1. 使用独立的 codex/<简短任务名> 分支；
2. 运行合适的检查或测试；
3. 提交并 push 到 GitHub；
4. 更新 HANDOFF.md；
5. 最终只需报告仓库、分支、commit SHA、检查结果和下一步。
不要 force-push，不要直接改 main，不要提交密钥或本地配置。
```

## 从已有分支继续的提示词模板

```text
请继续 GitHub 仓库 OWNER/REPO 的分支 BRANCH。
先读取 HANDOFF.md、最近提交和当前差异，再完成：<后续目标>。
完成后提交并 push，更新 HANDOFF.md，并报告新的分支名和 commit SHA。
```

## 注意

- GitHub 是交接和版本存储层，不会把 ChatGPT 与 Codex 的额度合并。
- 这种方式主要减少重复粘贴代码、文件和历史说明带来的上下文消耗。
- 私有仓库需要在 ChatGPT/Codex 的 GitHub 连接中授予对应仓库访问权限。
- 合并前建议使用 Pull Request 审阅差异。
