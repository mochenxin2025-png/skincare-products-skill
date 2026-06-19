# 🧴 护肤品分析技能 (Skincare Products Skill)

> 面向皮肤科学的 AI 智能体框架，用于化妆品配方分析。从作用机制、配方逻辑和科学证据角度评估护肤、身体护理和头发护理产品——**不看品牌、营销或价格**。

[![版本](https://img.shields.io/badge/版本-2.1-blue)](https://github.com)
[![许可证](https://img.shields.io/badge/许可证-MIT-green)](https://github.com)
[![平台](https://img.shields.io/badge/平台-8-orange)](https://github.com)
[![品类](https://img.shields.io/badge/产品品类-10-purple)](https://github.com)

[![English](https://img.shields.io/badge/English-blue)](README_EN.md)

---

## 📖 这是什么？

这是一个**结构化的智能体技能**，可以将任何 AI 助手转变为面向皮肤科学的化妆品配方分析师。它不是根据品牌声誉、营销宣传或价格来评估产品，而是应用：

- **第一性原理推理** — 在分析成分之前先确定生物学目标
- **循证评估** — 每个功效机制都映射到 A–E 证据等级
- **15 类成分本体论** — 在功效分析之前进行统一分类
- **30 条已记录的成分相互作用** — 协同、拮抗和冲突规则
- **调和平均置信度评分** — 五因素不确定性传播
- **按品类优化的权重配置** — 10 大产品类型的优化评分维度

该框架包含 **631 条结构化数据条目**，涵盖成分数据库、相互作用规则和科学参考文献。

---

## 🎯 分析品类

| 品类 | 示例 | 规格文档 |
| --- | --- | --- |
| 🧼 洁面产品 | 泡沫洁面、凝胶洁面、洁面乳 | 内联 |
| 🚿 沐浴露 | 沐浴啫喱、沐浴液 | `body-wash-spec.md` |
| 💧 保湿霜 | 面霜、凝霜、乳液 | 内联 |
| 🧪 精华 | 安瓶、精华水 | 内联 |
| ☀️ 防晒 | SPF 乳液、防晒喷雾、物理/化学防晒 | 内联 |
| 🧴 身体乳 | 身体霜、身体黄油 | `body-lotion-spec.md` |
| 🧴 洗发水 | 去屑、头皮护理、日常洗发 | `shampoo-spec.md` |
| 💆 护发素 | 冲洗型护发素、发膜、免洗护发素 | `hair-conditioner-spec.md` |
| 💋 润唇膏 | SPF 润唇膏、唇霜、唇膜 | `lip-balm-spec.md` |
| 👶 婴幼儿产品 | 宝宝霜、沐浴露、护臀霜 | 内联 |

另有 **12 种肤质/状况评估**：正常、干性、油性、混合性、敏感、痘痘肌、脂溢性皮炎、玫瑰痤疮、屏障受损、毛周角化、身体痘痘、婴幼儿。

---

## 🧠 工作原理

```
输入（文字/OCR）→ 验证 → 本体论映射 → 数据库查询
→ 相互作用分析 → 机制分析 → 架构分析
→ 风险分析 → 皮肤适配 → 置信度 → 评分 → 输出
```

### 评分公式

```
最终得分 = Σ(PS × EM × IM × 权重) − 营销惩罚

PS = 存在度评分 (0.0–1.0)：产品在每个维度的满足程度
EM = 证据乘数：A=1.00  B=0.90  C=0.70  D=0.50  E=0.20
IM = 相互作用修正：协同=1.10  独立=1.00  拮抗=0.85  冲突=0.70
```

### 置信度

通过**调和平均**（最差因素感知）聚合五个因素：

$$C = \frac{5}{\frac{1}{I} + \frac{1}{D} + \frac{1}{M} + \frac{1}{X} + \frac{1}{C}}$$

| 分值 | 标签 | 行为 |
| --- | --- | --- |
| ≥ 80% | 🟢 高 | 确定性语言，数值评分 |
| 60–79% | 🟡 中 | 谨慎语言，数值评分附带说明 |
| 40–59% | 🟠 低 | 仅定性描述，无数值评分 |
| < 40% | 🔴 极低 | "数据不足" — 保守模式 |

---

## 🏗️ 架构

```
skincare-products-skill/
├── SKILL.md                           # 入口 — YAML 前置元数据 + 核心流程
├── references/                        # 按需加载的详细文档
│   ├── framework-full.md              #   完整 L0–L12 + M13–M22 规范
│   ├── ingredient-ontology-map.md     #   326 个 INCI 名 → 15 类本体论
│   ├── bootstrap-database.md          #   140 条目（防晒剂、表面活性剂、防腐剂、保湿剂、风险成分）
│   ├── extended-databases.md          #   85 条目（润肤剂、硅油、聚合物、植物提取物）
│   ├── interaction-rules.md           #   30 条相互作用规则及证据等级
│   ├── scoring-algorithm.md           #   完整评分公式 + 烟酰胺精华走查
│   ├── confidence-engine-spec.md      #   调和平均公式 + 回退联动
│   ├── input-parsing-spec.md          #   OCR 纠错 + INCI 规范化 + 中日韩语言表
│   ├── output-format-spec.md          #   Markdown 模板 + JSON API Schema
│   ├── evidence-citation-spec.md      #   50+ 精选参考文献（含 DOI）
│   ├── body-wash-spec.md              #   洗去型逻辑、表面活性剂评估、体验成分
│   ├── body-lotion-spec.md            #   四大功能系统、KP 评估、屏障友好成分
│   ├── shampoo-spec.md                #   抗真菌层级、脂溢性皮炎发病机制
│   ├── hair-conditioner-spec.md       #   阳离子/硅油/脂肪醇系统、死角蛋白约束
│   └── lip-balm-spec.md               #   封闭剂层级、薄荷醇/樟脑危险、半黏膜
├── assets/
│   └── report-schema.json             #   JSON Schema 机器可读报告
└── platforms/
    └── obsidian/                       #   Obsidian 格式的公式卡片
```

> **设计原则**：渐进式披露。仅 `SKILL.md` 始终加载（~380 行）。15 个参考文件按需加载——当智能体需要成分数据、相互作用规则或品类特定评估逻辑时才会读取。

---

## 🔬 关键设计决策

### 15 类成分本体论

每个成分在功效分析前**必须**归入恰好一个主要类别：

```
核心活性 [A] · 配方支持 [FS] · 皮肤调理 [SC]
质地修饰 [TM] · 防腐 [P] · 溶剂 [S] · 螯合剂 [C]
乳化剂 [E] · 稳定剂 [ST] · 成膜剂 [FF] · 着色剂 [CO]
香精 [FR] · 植物提取 [B] · 营销成分 [M] · 风险成分 [R]
```

风险 `[R]` 是加性的——一个成分可以同时是 `[A]`（活性成分）和 `[R]`（安全风险）。

### 6 级优先层级

规则冲突时：

```
安全规则 > 科学证据 (A/B) > 内部数据库
> 本体论映射 > 机制推理 > 启发式估计
```

### 级联回退

```
数据库匹配？→ 是：完全置信度
           → 否：本体论匹配？→ 是：推断 + 降低置信度
                              → 否：机制推理？→ 是：进一步降低置信度
                                               → 否："未知 [成分名]" — 绝不捏造
```

### 品类特定权重配置

没有两个产品类型共享相同的评分维度。洁面产品优先考虑安全性（30%），防晒产品优先考虑 UV 防护（35%），药用洗发水优先考虑抗真菌证据（40%），沐浴露优先考虑表面活性剂质量（35%）。

---

## 📊 数据规模

| 资源 | 条目数 |
| --- | --- |
| 成分本体论映射 | 326 个 INCI 名称 |
| 数据库条目（引导 + 扩展） | 225 |
| 成分相互作用 | 30 条规则 |
| 精选参考文献 | 50+（含 DOI） |
| 产品品类 | 10 |
| 肤质/状况 | 12 |
| 权重配置 | 10 |
| **结构化数据总计** | **~651** |

---

## ⬇️ 下载与安装

### 方式一：Git 克隆（推荐）

```bash
git clone https://github.com/mochenxin2025-png/skincare-products-skill.git
cd skincare-products-skill
```

### 方式二：下载 ZIP 压缩包

[![Download ZIP](https://img.shields.io/badge/下载-ZIP压缩包-brightgreen?style=for-the-badge)](https://github.com/mochenxin2025-png/skincare-products-skill/archive/refs/heads/master.zip)

点击上方徽章，或手动进入 GitHub 仓库页面 → **Code → Download ZIP**，解压即可。

### 方式三：作为 Hermes Agent 技能安装

如果你在使用 [Hermes Agent](https://hermes-agent.nousresearch.com)，可以用一条命令安装：

```bash
# 确保已加载 hermes-agent 技能：
hermes skills install skincare-products-skill
```

或者从本地目录复制安装：

```bash
cp -r /path/to/skincare-products-skill $HERMES_HOME/skills/
# 验证安装：
hermes skills list | grep skincare
```

### 方式四：Hermes 技能归档包（`.7z`）

下载便携式归档包用于离线安装：

👉 [**skincare-products-skill.7z**](https://github.com/mochenxin2025-png/skincare-products-skill/releases/download/v2.1/skincare-products-skill.7z)
*(使用 7-Zip 解压到 `$HERMES_HOME/skills/`)*

---

## 🚀 使用方法

### 作为 Reasonix Code / Claude Code 技能

将整个 `skincare-products-skill/` 目录放入你的 skills 文件夹。`SKILL.md` 中的 YAML 前置元数据提供自动激活触发。

### 作为 ChatGPT Custom GPT

使用便携式单文件版本。将内容粘贴到 Instructions 字段中。

### 作为 Cursor 规则

将规则内容放入 `.cursorrules` 或 `.cursor/rules/skincare.md`。

### 触发示例

```
"分析这个成分表：Aqua, Niacinamide, Butylene Glycol..."
"这个防晒霜好吗？" [附上产品照片]
"比较这两款保湿霜"
"评价这款去屑洗发水"
"看看这支润唇膏 — 含有薄荷醇"
```

---

## 🛡️ 防幻觉机制

框架包含明确的防幻觉规则，防止 AI 在化妆品分析中的常见错误：

- 未经声明证据，绝不假定浓度
- 绝不从成分数量或热门程度推断功效
- 洗去型产品（沐浴露、洗发水、护发素）：成分表中后三分之一的成分 → 微量浓度 → 重新归类为营销成分 `[M]`
- 体验成分（薄荷醇、樟脑、海盐）→ 仅感官工程 → `[M]`
- 胶原蛋白、多肽、干细胞、黄金在护肤品中 → 始终为 `[M]`
- "使用数个世纪" ≠ 临床证据 → 最高证据等级 D
- 数据库缺失 → "证据不足" — 绝不捏造
- 未找到相互作用规则 → 独立（IM 1.00）— 绝不发明相互作用

---

## 📝 输出示例

```markdown
## ⑬ 综合评分：54 / 100（🟢 高置信度）

| 维度 | 权重 | PS | EM | IM | 贡献值 |
| --- | --- | --- | --- | --- | --- |
| 核心功效 | 35 | 0.85 | 0.90 | 1.00 | 26.8 |
| 配方架构 | 20 | 0.70 | 0.50 | 1.00 | 7.0 |
| 安全性 | 20 | 0.85 | 0.70 | 1.00 | 11.9 |
| 支持系统 | 15 | 0.50 | 0.50 | 1.00 | 3.75 |
| 皮肤适配 | 10 | 0.70 | 0.70 | 1.00 | 4.9 |

## ⑭ 结论

**优点**：公认的有效活性成分（烟酰胺 10%），临床证据充分。
**不足**：配方架构简单，缺乏抗氧化支持系统。
**建议**：推荐给正常至油性皮肤、寻求肤色提亮的人群。
```

---

## 🔌 平台兼容性

| 平台 | 状态 | 说明 |
| --- | --- | --- |
| Reasonix Code | ✅ 原生支持 | 完整多文件渐进式披露 |
| Claude Code | ✅ 兼容 | YAML 前置元数据 + 文件读取工具 |
| Codex CLI | ⚠️ 需适配 | 不同的技能清单格式 |
| Cursor Rules | ⚠️ 扁平化 | 多参考文件 → 单个 `.cursorrules` |
| Windsurf | ⚠️ 扁平化 | 同 Cursor |
| RooCode | ⚠️ 扁平化 | 同 Cursor |
| ChatGPT Custom GPT | ⚠️ 截断风险 | Instructions 字段 ~8K 字符限制 |
| Gemini Gems | ⚠️ 截断风险 | 系统指令长度限制 |

---

## 🤝 贡献指南

新的产品品类、成分数据库条目和相互作用规则遵循一致的模板：

1. **新品类的创建**：定义第一性原理 → 权重配置 → 领域规则 → 防幻觉规则
2. **新成分的添加**：遵循 M21 架构（名称 / 别名 / 类别 / 本体论 / 机制 / 证据 / 风险 / 浓度 / 皮肤兼容性）
3. **新相互作用的记录**：组合 + 类型 + 机制 + 证据等级 + IM 值

---

*基于 Reasonix Code Skill Creator 格式构建。证据等级遵循 A–E 分类。所有结论应经皮肤科医生确认后再用于医疗决策。*
