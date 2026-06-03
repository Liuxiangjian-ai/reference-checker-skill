<p align="center">
  <img src="https://img.shields.io/badge/语言-中文-green" alt="中文">
  <a href="README.en.md">
    <img src="https://img.shields.io/badge/Language-English-blue" alt="English">
  </a>
  <img src="https://img.shields.io/badge/类型-AI%20Skill-purple" alt="AI Skill">
  <img src="https://img.shields.io/badge/核查-DOI%20%2B%20元数据-orange" alt="DOI 和元数据">
  <img src="https://img.shields.io/badge/中文文献-CNKI%20%2B%20万方%20%2B%20维普-red" alt="中文文献核查">
  <img src="https://img.shields.io/badge/版本-v1.4.0-lightgrey" alt="v1.4.0">
  <img src="https://img.shields.io/badge/许可证-MIT-yellow" alt="MIT License">
</p>

# Reference Checker Skill｜参考文献核查 Skill

🌐 Language: 中文 | [English](README.md)

**不要让一条假文献毁掉整篇论文的可信度。**

Reference Checker Skill 是一个用于**学术论文投稿前参考文献逐条核查**的 AI Skill，适合研究生、科研作者、编辑、审稿助理和学术写作者使用。

它的目标不是“帮你简单看一下参考文献”，而是让 AI 按照严格流程，对参考文献列表进行**逐条、结构化、可追踪的核验**，尽量发现投稿前最容易被忽略、但最可能影响论文可信度的问题。

v1.4.0 起，本 Skill 明确支持**英文文献与中文文献的双语核查**。除 DOI、PubMed、Crossref、出版社页面等常规路径外，中文文献会优先使用**中文原题名**进行核查，并将**知网 CNKI、万方 Wanfang、维普 VIP/CQVIP、期刊官网、出版社目录、大学机构库、国家标准/政府官网**等纳入检索路径。

---

## v1.4.0 更新重点

这一版主要增强了中文文献核查能力：

* **支持中文文献逐条检查**：中文期刊论文、中文学位论文、中文图书、中文会议论文、标准、政策文件、专利等均可纳入核查。
* **增加中文数据库检索路径**：中文期刊优先按“中文原题名”检索，推荐依次核对期刊官网、知网、万方、维普等来源。
* **避免误判无 DOI 中文文献**：很多中文文献没有 DOI、PMID 或英文元数据，Skill 会要求 AI 不得仅因缺少这些字段就判定为不可验证。
* **增加中文溯源字段**：输出表格中的 `DOI / PMID` 扩展为 `DOI / PMID / Chinese Trace`，便于记录 CNKI、万方、维普、期刊官网、ISBN、标准号、专利号等信息。
* **增强中文格式检查**：新增对中文期刊名、中文作者名、GB/T 7714 风格、中文标点、页码、卷期、学位授予单位、出版社、ISBN 等字段的核查要求。
* **区分中文原题名与英文译名**：对于双语中文文献，应优先核验中文题名；英文译名不一致时，只有在影响文献身份识别时才标记为严重问题。

---

## 为什么需要这个 Skill？

在 AI 辅助写作越来越普遍的今天，参考文献错误变得更隐蔽，也更危险。

很多错误看起来“很像真的”：

* DOI 存在，但指向的是另一篇文章
* 题名看起来合理，但数据库里查不到
* 作者、期刊、年份、卷期页码彼此错配
* 中文题名、英文译名、期刊英文名之间不一致
* 中文文献没有 DOI，被错误地当作“无法核验”
* 预印本已经有正式发表版本，但文中仍引用旧版本
* 同一篇文献被重复引用
* AI 生成了格式完整、内容逼真、但实际不存在的参考文献

这些问题如果出现在投稿稿件中，轻则影响编辑和审稿人的第一印象，重则直接损害整篇论文的可信度。

**Reference Checker Skill 的核心价值，就是在投稿前帮你把这些问题尽可能提前暴露出来。**

---

## 这个 Skill 能做什么？

Reference Checker Skill 会要求 AI 对参考文献进行**逐条核查**，而不是只挑几条看起来可疑的文献抽样检查。

它会尽量核验每一条参考文献的关键信息，包括：

| 检查项目 | 是否检查 |
| --- | --- |
| 文献是否真实存在 | 是 |
| 文章题名 / 中文原题名 | 是 |
| 作者信息 / 中文作者名 | 是 |
| 期刊 / 来源 / 出版社 / 授予单位 | 是 |
| 发表年份 / 出版年份 / 授予年份 | 是 |
| 卷、期、页码或文章编号 | 是 |
| DOI | 如有则检查 |
| PMID / PMCID | 如有则检查 |
| CNKI / 万方 / 维普 / 期刊官网溯源 | 中文文献优先检查 |
| ISBN / 标准号 / 专利号 / 文件号 | 对应文献类型检查 |
| 重复引用 | 是 |
| 预印本与正式发表版本冲突 | 是 |
| 撤稿或来源风险 | 可检测时检查 |
| 中文/英文题名不一致 | 是 |
| GB/T 7714 或目标期刊格式一致性 | 可按需求检查 |

---

## 核心特点

### 1. 逐条核查，而不是抽样检查

很多参考文献检查工具只适合快速浏览，容易漏掉隐藏错误。

这个 Skill 默认要求 AI **逐条检查每一条参考文献**。除非用户明确要求抽样，否则不应跳过任何一条。

---

### 2. 不只查 DOI，还查元数据是否匹配

一个 DOI 能打开，并不代表这条参考文献就是正确的。

这个 Skill 会要求 AI 同时核对：

* 题名是否一致
* 作者是否匹配
* 期刊名称是否正确
* 年份、卷期、页码是否对应
* DOI 是否真的指向该文章
* PMID / PMCID 是否与文献信息一致
* 中文文献是否能通过知网、万方、维普、期刊官网或其他可靠来源溯源

它关注的不是“有没有 DOI”，而是**整条参考文献是否真实、准确、对应一致**。

---

### 3. 支持中文文献数据库检索

对于中文文献，Skill 会要求 AI 优先按**中文原题名**核查，而不是直接用英文译名检索。

推荐检索路径包括：

| 文献类型 | 推荐核查路径 |
| --- | --- |
| 中文期刊论文 | 期刊官网、知网 CNKI、万方、维普、DOI 元数据 |
| 中文学位论文 | 知网博硕士论文库、万方学位论文库、学校机构库、国家图书馆记录 |
| 中文图书 / 章节 | 出版社目录、ISBN 数据库、国家图书馆、高校图书馆目录 |
| 中文会议论文 | 会议官网、论文集、知网会议库、万方会议库 |
| 中文标准 | 国家标准全文公开系统、行业标准官网、主管部门网站 |
| 政策 / 法律 / 政府文件 | 官方政府网站、发文机关网站、法规数据库 |
| 中国专利 | 国家知识产权局、专利公布公告系统 |

如果中文数据库之间存在细微差异，Skill 会要求记录差异、说明核查路径，并根据证据强弱给出置信度，而不是简单给出“已验证”或“未找到”。

---

### 4. 对问题进行严重程度分级

所有发现的问题都会被标记为不同严重程度，方便你优先处理。

| 严重程度 | 含义 |
| --- | --- |
| `Critical` | 高风险问题，例如疑似假文献、不存在的文章、错误 DOI、DOI 指向另一篇文章、伪造 PMID/DOI/CNKI-like 信息 |
| `Major` | 真实文献，但关键元数据错误，例如题名、期刊、年份、卷期页码明显不匹配，或缺失导致无法溯源的中文来源信息 |
| `Minor` | 格式、大小写、字段不完整、中文/英文标点、期刊名缩写、引用风格不一致等小问题 |
| `Manual check` | 证据不足、数据库冲突、来源不可访问或文献类型复杂，需要人工进一步确认 |

---

### 5. 支持长参考文献列表分批检查

如果参考文献数量很多，AI 一次无法可靠检查完，Skill 会要求 AI 分批处理，并明确说明：

* 本轮检查了哪些编号
* 哪些参考文献还没有检查
* 是否需要继续下一批

这样可以避免 AI 在长列表中漏查、跳查或假装已经全部检查完成。

---

### 6. 输出结果适合人工复核

每一轮检查都会输出结构化表格，方便作者、导师、编辑或合作者快速定位问题。

示例输出表格包括：

| Ref | Submitted Title | Submitted Authors | Submitted Source / Journal | Year | DOI / PMID / Chinese Trace | Verification Route | Match Quality | Status | Confidence | Main Issue / Suggested Fix |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

核查完成后，Skill 还会要求 AI 汇总所有问题文献，方便用户一次性修改。

---

## 适合哪些场景？

这个 Skill 特别适合：

* 期刊论文投稿前检查
* 学位论文参考文献核查
* 综述论文长参考文献列表检查
* 生物医学和生命科学论文投稿
* 人文社科论文中的中文文献核查
* 中文核心、CSSCI、北大核心、科技核心等中文期刊投稿前检查
* 使用 AI 辅助写作后检查引用真实性
* 文献管理软件批量导出后的质量控制
* 编辑部或课题组内部的投稿前质控流程
* 检查疑似 AI 生成或 AI 修改过的参考文献

---

## 示例提示词

你可以这样使用：

```text
Please use the Reference Checker Skill to audit the following reference list.

Requirements:
1. Check every reference item by item.
2. Do not sample.
3. Verify title, authors, journal, year, volume, issue, pages, DOI, and PMID if available.
4. For Chinese references, search the original Chinese title first and use CNKI, Wanfang, VIP, official journal pages, or other reliable Chinese sources when applicable.
5. Classify problems as Critical, Major, Minor, or Manual check.
6. If the list is too long, check it in batches and ask me whether to continue.
```

中文用户也可以直接这样说：

```text
请使用 Reference Checker Skill 帮我逐条核查下面的参考文献列表。

要求：
1. 必须逐条检查，不要抽样。
2. 核查题名、作者、期刊、年份、卷、期、页码、DOI，如果有 PMID 也一并检查。
3. 中文文献请优先用中文原题名检索，并尽量通过知网、万方、维普、期刊官网、出版社目录、学校机构库或官方网站核查。
4. 不要因为中文文献没有 DOI 或 PMID 就直接判定为无法验证。
5. 将问题分为 Critical、Major、Minor 和 Manual check。
6. 如果参考文献太多，请分批检查，并明确告诉我本轮检查了哪些编号，还有哪些没有检查。
7. 全部检查完成后，请汇总所有有问题的参考文献。
```

---

## 推荐输出格式

每一轮核查应包含如下表格：

| Ref | Submitted Title | Submitted Authors | Submitted Source / Journal | Year | DOI / PMID / Chinese Trace | Verification Route | Match Quality | Status | Confidence | Main Issue / Suggested Fix |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

如果参考文献较多，本轮结束时应说明：

```text
This round checked references 1–20. References 21–58 remain unchecked.
Would you like me to continue with the next round, references 21–40?
```

全部核查完成后，应输出：

```text
Reference audit complete.
```

并汇总所有存在 `Critical`、`Major`、`Minor` 和 `Manual check` 问题的参考文献。

---

## 推荐仓库结构

```text
reference-checker-skill/
├── SKILL.md
├── README.md
├── README.zh-CN.md
├── README.en.md
├── assets/
│   └── cover.png
├── templates/
│   ├── report_template.md
│   └── correction_table_template.md
└── examples/
    ├── input_references.txt
    ├── input_references_zh.txt
    └── expected_output.md
```

---

## 安装与使用

下载或克隆本仓库后，将文件夹放入支持 Skill 工作流的 AI 环境中。

核心文件是：

```text
SKILL.md
```

如果你的环境不支持 Skill 文件夹，也可以直接将 `SKILL.md` 中的内容复制到：

* 自定义指令
* 项目指令
* Agent 工作流
* Manuscript checking prompt
* 投稿前质控流程

---

## 使用建议

为了提高核查准确性，建议用户提供尽可能完整的参考文献信息：

* 对英文文献：题名、作者、期刊、年份、卷期页码、DOI、PMID/PMCID。
* 对中文期刊论文：中文题名、中文作者、期刊全称、年份、卷期页码、DOI 或数据库来源。
* 对中文学位论文：题名、作者、授予单位、学位类型、年份、数据库来源。
* 对中文图书：书名、作者/编者、出版社、出版年份、ISBN、引用页码。
* 对标准/政策/专利：标准号、文件号、专利号、发布机构、发布日期。

---

## 重要说明

Reference Checker Skill 用于辅助参考文献核查，但不能完全替代人工审阅。

对于被标记为以下类型的参考文献，建议用户务必人工复核：

* `Critical`
* `Major`
* `Manual check`

另外，知网、万方、维普等中文数据库可能存在访问权限限制。Skill 的作用是要求 AI 采用正确的检索路径、记录证据来源和不确定性；如果数据库无法访问，应明确标记为 `Manual check`，而不是臆造核查结果。

这个 Skill 的设计原则是：**宁可严格标记可疑问题，也不要把无法确认的参考文献默认为正确。**

---

## License

MIT License.
