# 公文写作助手（gongwen-writing）

一个面向党政机关 / 企事业单位文秘场景的 Claude Code 插件，帮你把零散的工作内容写成规范、得体、能过关的公文——工作总结、工作汇报、述职报告、请示、通知、纪要、讲话稿等常见文种全覆盖。

## 能做什么

- **工作总结 / 工作汇报 / 述职报告**：搭结构、抓亮点、写问题、排下一步
- **法定公文**：请示、报告、通知、通报、函、纪要、意见
- **事务文书**：讲话稿、调研报告、事迹材料、经验交流材料、对照检查材料
- **格式与语言把关**：层次序数、数字标点、易错词、政治表述分寸

## 安装（二选一）

### 方式 A：通过 GitHub Marketplace（推荐）

在 Claude Code 里执行：

```
/plugin marketplace add mini-tang/gongwen-writing
/plugin install gongwen-writing@mini-tang-gongwen
```

### 方式 B：通过 npm

先添加一个指向 npm 包的市场，再安装：

```
/plugin marketplace add mini-tang/gongwen-writing
/plugin install gongwen-writing@mini-tang-gongwen
```

> npm 包 `@mini-tang/gongwen-writing` 是同一插件的 npm 发布形态，作为 marketplace 的 `source: npm` 来源。详细见下方「npm 发布」。

## 使用

装好后，两种方式触发：

1. **直接说需求**：说"帮我写个上半年工作总结""给上级写个请示"，插件会自动触发。
2. **斜杠命令**：`/gongwen-writing:gongwen-writing`（插件名:技能名）。

插件会先问你几个关键问题（文种、给谁看、岗位、素材、篇幅），再动笔。**请尽量提供真实素材**（做了哪些事、关键数据、亮点、问题），它不会凭空编造数字和成绩，缺失处会标注「〔待补充〕」请你补。

## 目录结构

```
gongwen-writing/
├── .claude-plugin/
│   ├── plugin.json          # 插件清单
│   └── marketplace.json     # 市场清单（引用本仓库插件）
├── skills/
│   └── gongwen-writing/
│       ├── SKILL.md         # 技能主入口
│       ├── references/      # 各文种写法、语言规范、格式规范
│       └── examples/        # 交互示例
├── package.json             # npm 发布用
├── LICENSE                  # MIT
└── README.md
```

## npm 发布（可选）

`package.json` 已配置好，发布步骤：

```bash
npm login                    # 首次需登录，并在 npmjs.com 创建 @mini-tang 作用域
npm pack --dry-run           # 预览 tarball 内容
npm publish                  # 发布 @mini-tang/gongwen-writing
```

发布后，如需让 npm 作为安装来源，把 `.claude-plugin/marketplace.json` 里插件的 `source` 改为：

```json
"source": { "source": "npm", "package": "@mini-tang/gongwen-writing" }
```

## 如何定制（贴近本单位）

不同单位对公文格式、术语、语气的要求不同。三种方式，从简到繁：

1. **对话里直接给材料（最省事）**：写的时候把你单位的范文 / 术语表 / 格式要求贴进来或 `@` 文件，skill 会以它为准、模仿其风格。
2. **加进 `references/unit/`（作者 / fork 者适用）**：把你单位的 `.md` 材料放进 `skills/gongwen-writing/references/unit/`，skill 写作时会优先参考。适合你自己维护、或 fork 本仓库改成单位专属版。
3. **fork 本仓库**：改完后重新发布成你自己的插件。

> 注意：直接修改"已安装插件"目录里的文件，插件更新时会被覆盖，不推荐。

## 许可

MIT
