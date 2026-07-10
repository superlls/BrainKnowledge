<div align="center">

# 🧬 BrainKnowledge 大脑知识库

**关于元认知、认知科学、大脑工作原理的系统性 Obsidian 笔记库**

[![Obsidian](https://img.shields.io/badge/Obsidian-Vault-7C3AED?style=flat-square&logo=obsidian&logoColor=white)](https://obsidian.md/)
[![Markdown](https://img.shields.io/badge/Markdown-Wikilink%20%2B%20Callout-000000?style=flat-square&logo=markdown&logoColor=white)](https://help.obsidian.md/)
[![主题](https://img.shields.io/badge/主题-7_大分类-brightgreen?style=flat-square)](./index.md)
[![Web](https://img.shields.io/badge/在线阅读-brainknowledge--web-3FCF8E?style=flat-square&logo=vercel&logoColor=white)](https://brainknowledge-web.vercel.app)

</div>

## ✨ 简介

每个文件对应一个知识点，包含详细解释与参考来源；每篇笔记带 `分类 / 神经递质 / 脑区 / tags` 等 frontmatter 属性，可用 Obsidian 的 `.base` 视图筛选。笔记之间以 `[[wikilink]]` 双向链接串联成知识网络。

本 vault 同时是两个网站的数据源：

- **正式站**（Next.js + Supabase + GSAP）：<https://brainknowledge-web.vercel.app> ← [brainknowledge-web](https://github.com/LeoLee0812/brainknowledge-web)
- **替代技术栈 demos**（SvelteKit + UnoCSS + Motion）：<https://brainknowledge-demos.vercel.app> ← [brainknowledge-demos](https://github.com/LeoLee0812/brainknowledge-demos)

vault 里的 `git commit` 会通过 post-commit 钩子自动触发网站同步与重建部署。

## 🚀 内容特色

- **检索入口**：完整的分类索引见 **[[index]]**——按 7 大主题归类全部笔记。
- **Obsidian 原生语法**：callout、`[[双向链接]]`、`==高亮==`、frontmatter properties 全面使用。
- **可追溯**：每篇笔记附参考来源章节。
- **自动化维护**：由 Claude Code `/元认知` 命令自动生成并维护；GPG 签名已启用，所有 commit 均带 Verified 标记。

## 📁 项目结构（7 大主题）

```
├── index.md                  # 知识库索引（MOC，检索入口）
├── 前额叶与自控/              # 冲动抑制、目标维持、注意力
├── 睡眠与晨起/                # 睡眠结构、皮质醇节律、做梦与晨起情绪
├── 多巴胺与奖赏/              # 预测误差、心流、成瘾机制
├── 焦虑与负面偏差/            # 负面偏差、应激反应、焦虑循环
├── 社交与情绪/                # 社会比较、情绪调节
├── 记忆/                      # 记忆编码、巩固与提取
├── 学习与认知效率/            # 学习策略、认知负荷
└── .claude/skills/            # Obsidian 工具技能（见下）
```

## 🛠️ 工具技能（Skills）

本仓库在 `.claude/skills/` 下安装了 5 个 [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills)（Obsidian 官方出品），为本知识库提供 Obsidian 原生能力。

### 1. `obsidian-markdown` — Obsidian 风格 Markdown ✅ 开箱即用

给笔记加上 wikilink、callout、properties 等 Obsidian 专有语法。

- 给 `心流状态.md` 加 callout 高亮：`> [!note] 定义` 放一句话定义，`> [!warning] 易混淆` 区分它与 `爽片沉溺与奖赏回路`。
- 把「多巴胺/成瘾」主题的笔记用 `[[双向链接]]` 串起来：`游戏成瘾_被操控感与逃避现实` ←→ `竞技网游vs探索游戏的多巴胺成瘾机制` ←→ `心流状态`。
- 给所有笔记补 frontmatter properties（如 `神经递质: [多巴胺]`、`脑区: [前额叶]`、`tags`），为下面的 Bases 视图打基础。

### 2. `obsidian-bases` — `.base` 数据库视图 ✅ 开箱即用

基于 properties 把一堆 `.md` 渲染成可筛选的动态表格 / 卡片视图。

- 建「按神经递质分类.base」：自动把含「多巴胺」「血清素」「皮质醇」的笔记分组成表（如归拢 `社会比较焦虑与血清素`、`最健康睡眠方式与皮质醇节律`）。
- 建「最近更新.base」cards 视图，按更新时间倒序，替代手动维护目录。
- 建「待补充.base」：筛选出缺少「参考来源」章节的笔记，方便查漏补缺。

### 3. `json-canvas` — `.canvas` 画布 / 关系图 ✅ 开箱即用

把知识点连成可视化白板，节点嵌入笔记、连线表达因果关联。

- 「多巴胺与成瘾」关系图：`不确定性与多巴胺_预测误差` →（奖赏回路）→ `游戏成瘾` / `爽片沉溺` / `心流状态`。
- 「睡眠—晨起」时间线：`最健康睡眠方式与皮质醇节律` → `梦多与REM反弹现象` → `早晨起床后情绪失控`。
- 「焦虑机制」因果图：`为什么大脑会默认先想坏结果` → `焦虑未来与负面偏差` → `焦虑逃避循环与身体应激反应`。

### 4. `defuddle` — 网页转干净 Markdown ⚙️ 依赖 Defuddle CLI（已安装）

抓取网页正文并剥离导航/广告，转成 markdown，比 WebFetch 省 token。

- 给一篇讲多巴胺预测误差的论文/科普网页链接，`defuddle parse <url> --md` 抓成干净正文，作为新笔记的「参考来源」素材。
- 整理睡眠机制主题时，把 PubMed 或科普文章正文提取出来直接入库，省去手动复制清理。
- 读 Nature / Scientific American 文章时先转 md，再按本库笔记格式提炼成知识点。

### 5. `obsidian-cli` — 命令行操控 Obsidian ⚙️ 依赖 Obsidian CLI（已安装，需 Obsidian 运行中）

直接对运行中的 Obsidian 读 / 建 / 搜笔记、查链接。

- `obsidian search query="多巴胺"` 一键找出所有相关笔记。
- `obsidian create name="新知识点" content="..."` 按格式快速建笔记。
- `obsidian backlinks file="心流状态"` 查看哪些笔记反向引用了它。

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=LeoLee0812/BrainKnowledge&type=Date)](https://www.star-history.com/#LeoLee0812/BrainKnowledge&Date)
