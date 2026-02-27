# PRD Sprint

> 把零散输入变成完整 PRD — Claude Code Skill

产品经理每天都在处理大量零散信息：客户邮件、会议记录、口头需求、历史文档。把这些变成一份结构清晰的 PRD，以前要 3 天，现在只要 2-3 小时。

## 它能做什么

```
输入：邮件 + 会议记录 + 口头描述 + 历史文档（任意组合）
  ↓
自动分析材料覆盖度（✅ 已有 / ⚠️ 模糊 / ❌ 缺失）
  ↓
精准追问（最多 2 轮，不啰嗦）
  ↓
输出：完整 PRD（背景/目标/用户故事/功能清单/Mermaid流程图/字段说明/验收标准）
  ↓
可选：生成可交互 HTML 原型 / 评审 PPT
```

## 安装

**前提**：已安装 [Claude Code](https://docs.anthropic.com/en/docs/claude-code)（Anthropic 官方 CLI）

```bash
# 克隆仓库
git clone https://github.com/CPTYUSHU/prd-sprint.git

# 复制到 Claude Code skills 目录
cp -r prd-sprint ~/.claude/skills/prd-sprint

# 重启 Claude Code 即可使用
```

或者手动下载：
1. 点击页面上方绿色 **Code** 按钮 → **Download ZIP**
2. 解压后将 `prd-sprint` 文件夹复制到 `~/.claude/skills/`
3. 重启 Claude Code

## 使用

在 Claude Code 中直接说：

```
帮我写个PRD。我们要做一个积分兑换功能。
客户邮件里提了这些需求：[粘贴邮件内容]
上周会议结论：[粘贴会议记录]
技术栈是 Java + React Native。
```

AI 会自动：
1. 扫描你的材料，告诉你哪些信息够了、哪些还缺
2. 快速追问关键缺失（最多 2 轮）
3. 生成完整 PRD 文档（`.md` 格式）
4. 问你要不要顺便生成原型或 PPT

### 触发词

以下任意一种说法都能触发：
- "写PRD"
- "PRD Sprint"
- "生成需求文档"
- "帮我整理PRD"
- "需求文档"

### 快速模式

如果你的材料已经很完整，或者赶时间：

```
快速写个PRD：[直接粘贴所有材料]
```

AI 会跳过追问，直接生成，信息不足的地方标 `[待确认]`。

## PRD 输出结构

```
1. 概述（一句话 + 背景 + 目标）
2. 用户故事
3. 功能清单（含优先级 P0/P1/P2）
4. 用户流程（Mermaid 流程图，可直接渲染）
5. 页面说明（含 ASCII 布局图）
6. 数据 & 字段说明（字段名/类型/必填/校验规则/示例值）
7. 异常流程 & 边界情况
8. 验收标准（每条可测试、可验证）
9. 待确认事项
```

## 文件结构

```
prd-sprint/
├── SKILL.md                  # Skill 主文件（Claude Code 读取这个）
├── references/
│   └── prd-template.md       # PRD 模板（AI 生成时参考）
└── README.md                 # 你正在读的这个
```

## 支持的输入类型

| 类型 | 说明 |
|------|------|
| 粘贴文本 | 邮件、会议记录、聊天记录、需求描述 |
| 文件路径 | 指向本地文档，AI 会自动读取 |
| 口头描述 | 直接用自然语言描述需求 |
| 截图 | 竞品截图、白板照片、草图 |
| 历史 PRD | 在已有文档基础上迭代 |

不需要把材料整理好再丢给它，越原始越好，整理是 AI 的活。

## 常见问题

**Q: 和 feature-card 什么区别？**
feature-card 是轻量级需求卡片，适合敏捷开发快速记录单个功能。prd-sprint 是完整的 PRD 文档，适合正式的需求评审和开发交付。

**Q: 需要什么 Claude Code 版本？**
任何支持 Skills 的 Claude Code 版本都可以。

**Q: 可以自定义 PRD 模板吗？**
可以，修改 `references/prd-template.md` 即可。AI 生成时会参考这个模板的结构。

**Q: 生成的原型是什么格式？**
HTML 文件，浏览器直接打开就能用，包含页面跳转和表单交互。

## License

MIT
