# AGENTS.md

本文件是本仓库（GitHub: ErgeAIA/ErgeAIA.github.io，本地 D:\Workspace\Code\ErgeAIA.github.io）中人类与任何 Agent 的合作协议。

## Permissions（权限边界）

- **git push 无需逐次确认**：本仓库无发版概念，更新即上线，本地改动可完成提交后直接推送（用户 2026-09-08 豁免；**仅限本仓库**，其他仓库仍须逐次确认）。
- **YOU MUST NOT 提交密钥、凭据、`.env`**。
- `og-cover-1200x630.jpg`（仓库根目录）为 `og:image` / `twitter:image` 所指封面，**MUST 保持 1200×630**，替换时按此尺寸重新产出；若封面为 AI 生成且带平台标识，标识 MUST 保留。

## 项目性质与工具链

GitHub Pages 用户主站（user site），服务于 `https://ergeaia.github.io/` 根路径。

- 当前为**路线甲：纯静态单页**——无构建系统、无包管理器、无依赖、无测试；`index.html` 即整站
- Pages 由仓库 Settings 托管（deploy from branch `main` / 根目录），无自定义 workflow，**不要**引入构建 workflow

## 命令表

| 场景 | 命令（可复制原文） | 说明 |
|---|---|---|
| 部署 | `git push` | 更新即上线，无需确认 |
| 查看部署状态 | `gh api repos/ErgeAIA/ErgeAIA.github.io/pages --jq .status` | `building` / `built` |
| 线上验证 | `curl -s -o /dev/null -w "%{http_code}" https://ergeaia.github.io/` | 期望 200 |

## 反直觉约定（MUST READ）

1. **index.html 的源头**：`D:\Workspace\Capability Vault\outputs\宝藏二哥AIA-个人网站-原型-variant2.html`（原型目录只读参考）；上线版本以本仓库为权威，改动落在本仓库。
2. **与 profile 主页无关**：special 仓库 `ErgeAIA/ErgeAIA` 渲染 GitHub 个人主页 README，与本站互不影响，不要在其中找本站内容。
3. **路线乙预留**：未来博客模块 Astro 化后，本文件"项目性质/命令表"MUST 同步更新（新增构建命令与 Actions）。

## 自维护协议

1. 视本文件为代码：规则变更须在同一 PR/任务中同步更新本文件。
2. 变更留痕：对规则的改/删在 commit message 中说明。
3. 周期维护：每次改版复查本文件，清除失效约定。
