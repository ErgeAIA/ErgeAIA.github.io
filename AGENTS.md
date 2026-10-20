# AGENTS.md

本文件是本仓库（GitHub: `ErgeAIA/ErgeAIA.github.io`，线上 `https://ergeaia.github.io/`）中人类与任何 Agent 的合作协议。

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

1. **index.html 的源头**：原型出自用户的能力库项目 Capability Vault（`outputs/` 下的个人网站原型 variant2，只读参考）；上线版本以本仓库为权威，改动落在本仓库。
2. **与 profile 主页无关**：special 仓库 `ErgeAIA/ErgeAIA` 渲染 GitHub 个人主页 README，与本站互不影响，不要在其中找本站内容。
3. **路线乙预留**：未来博客模块 Astro 化后，本文件"项目性质/命令表"MUST 同步更新（新增构建命令与 Actions）。
4. **公开仓库不写本地路径**：本仓库连同本文件是公开的，MUST NOT 出现盘符、用户名或本地目录结构；需要指代用户本地项目时只写**项目名**（如「ThemeVault」「Capability Vault」），本地路径、查色命令、抓图命令等操作性细节一律留在 Agent 记忆里。
5. **页面手写数字的口径**：index.html 无构建系统，数字为手写静态值（不像 profile 主页有 shields.io 实时查询），MUST 在本条登记口径与更新时间，改动数字时同步更新本条。2026-09-12 口径：宝库区"2600+ 位读者" = 公众号后台 2607 取整模糊化；"46+ 预设 Agent""4 个已发布 Agent 技能"来自 AI Vault 当前版本能力。前车之鉴：关于我区块曾手写"878+ 桌面软件下载"，与 ErgeMD 实际总下载（GitHub API 实测 511）严重失真，2026-09-12 已随数据卡改版移除——新增人气/下载类数字前先确认其经得起实时核对，宁可不展示。
6. **色板与字体声部的权威源是用户的主题仓库 ThemeVault**（指代本地项目只写项目名，本文件公开可见）：
   - 颜色 = erge 家族 `#001 dark` / `#002 light`，已全量 token 化到 `:root` 与 `[data-theme="light"]`。新增颜色 MUST 走令牌，MUST NOT 硬编码 hex/rgba——**含 JS 里的内联 `style.background`**，内联样式优先级高于 CSS 变量，会击穿主题（已踩过：header 滚动态曾内联写死深色，浅色主题下留一块深底）。
   - 字体 = ember `#006` 登记的声部（`fontStyle: display-mono`，fonts 含 IBM Plex Mono）。本站按该登记拆成**两声部同族**：大标题（hero / 区块标题 / 页脚品牌 / follow 标题 / 入口卡名称）用 **IBM Plex Serif + Noto Serif SC 900**，技术层（导航品牌 / 卡片标题 / 分组标签 / 日期与计数）用 **IBM Plex Mono**——同属 IBM Plex 超级家族，一种人格两种字面。**MUST NOT 从别的产品站抄声部**（aivault-site 的 DM Serif Display + 霞鹜文楷 是产品站选择，不代表品牌门户）；Space Grotesk 已于 2026-10-21 撤除（检测器判为 AI 界面趋同字体）。
   - 等宽只用在短文本上：等宽字宽固定，窄容器里的中英混排（如入口卡名称）会被撑到换行，此类元素归衬线声部。
   - 拉丁字体 MUST 自托管 woff2 并 `preload`（Google Fonts 在大陆不可靠，display 挂了品牌字就没了）；正文中文可继续走 Google Fonts，但栈尾 MUST 保留 `PingFang SC, Microsoft YaHei` 兜底。
   - ember 同时登记 `radius-none`（直角），本站**未采纳**（用户 2026-10-21 决定保留圆角），改圆角前须再确认。
   - 主题契约：`<html data-theme>` + `localStorage['ergeaia-theme']` + head 内联脚本首帧定主题（防闪）；默认跟随系统。改动任何一套配色后 MUST 用脚本核算两主题的文字对比度（AA：正文 4.5:1、大字 3:1）。

## 自维护协议

1. 视本文件为代码：规则变更须在同一 PR/任务中同步更新本文件。
2. 变更留痕：对规则的改/删在 commit message 中说明。
3. 周期维护：每次改版复查本文件，清除失效约定。
