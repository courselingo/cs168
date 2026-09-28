<div align="center">

# CourseLingo 课程仓库模板

把这个目录复制成一个独立的课程仓库 —— 或者用 `scripts/new_course.py` 自动生成。

</div>

---

## 这个模板解决什么

一门课从「想翻译」到「有网站」，中间有大量重复劳动：术语不统一、内容格式各异、授权说不清、构建要装一堆依赖。

这个模板把这些固化成可执行的约束：**零依赖、可校验、带授权闸门**。

## 目录结构

```
course.toml        课程元数据 + 授权闸门（第一个要改的文件）
glossary.toml      术语表 —— 本项目的核心资产
content/
  <NN>-<slug>/
    index.md       一讲（+++ TOML front matter + 正文）
    figures/*.svg  配图
scripts/
  new_lecture.py   新建一讲
  validate.py      校验（CI 强制）
  build.py         构建静态站 → site/
.github/workflows/ 校验 + 部署到 GitHub Pages
site/              构建产物（不入库）
```

## 三条命令

```bash
python scripts/new_lecture.py --title "Raft 领导者选举" --slug raft-leader-election \
    --source-url "https://pdos.csail.mit.edu/6.824/lec05.txt" --source-title "Raft (2)"

python scripts/validate.py       # 校验：术语、授权、格式
python scripts/build.py --out site   # 构建静态站
```

只依赖 **Python 3.11+ 标准库**。没有 `npm install`，没有 `pip install`，`git clone` 之后直接能跑。

## ★ 授权闸门

`course.toml` 里的 `[license].verified` 默认为 `false`。在它为 `true` 之前：

- `validate.py` **硬拦截**任何 `output_mode = "transcript"` 的讲座；
- 也就是说，**翻译完整逐字稿这条路在代码层面是走不通的**，必须先核实授权。

这不是形式主义。翻译逐字稿属于衍生作品，复制了原作的全部表达，其合法性完全取决于原课程的实际许可条款。详见 [内容策略](https://github.com/courselingo/courselingo/blob/main/docs/content-policy.md)。

模板默认产出的是 **`explanation`** —— 我们自己撰写的概念讲解。

## 术语标记

正文里引用术语一律写 `[[term:key]]`，不要手写「中文（English）」：

```markdown
[[term:leader-election]] 是 [[term:consensus]] 的第一道门槛。
```

- key 的推导规则：`en = "leader election"` → key 为 `leader-election`
- 渲染时首现显示「领导者选举（leader election）」，之后只显示「领导者选举」
- 引用不存在的 key 会被 `validate.py` 判为 ERROR

## 配图

图放在讲座目录的 `figures/` 下，用 Markdown 图片引用：

```markdown
![一句话说清「图里有什么 + 结论是什么」的中文 alt](figures/write-path.svg)
```

- 用**手绘 SVG + 中文标签**，不要 Mermaid —— 风格会飘。
- 规范见 [配图规范](https://github.com/courselingo/courselingo/blob/main/docs/diagram-conventions.md)，
  生成交给 `course-diagram` 技能。
- 模板里的 `content/01-what-is-a-distributed-system/figures/write-path.svg`
  是一张**已通过房规校验**的示例，可直接照着写。

一致性目前靠规范与自检：`validate.py` **不校验 SVG**（`pipeline-spec.md` §6 里没有这一项）。
如果你本机装了 `svg-diagram` 技能，可以手动跑它的 linter：

```bash
node ~/.agents/skills/svg-diagram/tools/svg-lint/bin/svg-lint.mjs content/*/figures/*.svg
```

> 预期会有 1 类警告：本项目的品牌色（如文字色 `#1f2937`）不在该 linter 的内置调色板里。
> 这是可接受的 —— 品牌色优先，别为了消警告改掉自己的配色。

## 论文（经典课程的另一半）

6.824 这类课程是**围绕论文**组织的 —— MapReduce、GFS、Raft、Paxos……所以论文在这里是一等公民：

```
papers.toml                     每篇论文的元数据 + **各自的**授权
content/papers/<key>/index.md   论文页（导读或全文翻译），key 对应登记表
```

关键是：**论文的授权和课程无关，而且通常更严。** 多数论文的版权在出版社
（ACM / IEEE / USENIX），而**翻译整篇论文 = 复制全部表达的衍生作品**，
风险与翻译逐字稿同级。

所以论文页分两档，闸门完全不同：

| `output_mode` | 是什么 | 闸门 |
| --- | --- | --- |
| `guide` | **我们自己写的导读**：它解决什么问题、怎么解、代价是什么 | **不设闸门** —— 概念不受著作权保护 |
| `translation` | 全文翻译 | 必须 `verified = true` **且** `allows_translation = true` |

**只「核实了」不够** —— 核实的结果完全可能是「不允许翻译」。两个条件缺一不可，
`validate.py` 与 `build.py` 各自独立拦截一次。

> ⚠️ **「网上能免费下载」≠「可以翻译」。** 作者把 PDF 挂在自己主页上不构成任何授权。
> 核实方法与逐篇结论见[论文授权](https://github.com/courselingo/courselingo/blob/main/docs/paper-licensing.md)。

讲座可以声明它涉及哪些论文，站点会自动交叉链接：

```toml
papers = ["mapreduce", "gfs"]     # 必须是 papers.toml 中已登记的 key
```

新建论文页的步骤（登记 → 建目录 → 写稿）见 [SOP](https://github.com/courselingo/courselingo/blob/main/docs/SOP.md)，
或直接用 `course-paper` 技能。

## 校验会拦下什么

| 档位 | 检查 |
| --- | --- |
| ❌ ERROR | 授权闸门（transcript 模式未授权） |
| ❌ ERROR | front matter 缺字段、讲次/slug 重复、slug 格式错误 |
| ❌ ERROR | `[[term:key]]` 引用了不存在的术语 |
| ❌ ERROR | **疑似整段转载英文原文**（连续 >400 字符且几乎全为 ASCII） |
| ❌ ERROR | **论文翻译闸门**：`translation` 但该论文未核实或不允许翻译 |
| ❌ ERROR | 论文页的 `paper` key 未登记 / 重复；`papers = [...]` 引用了未登记的论文 |
| ⚠️ WARN | glossary 里的英文原词出现在正文却没加标记（术语漂移） |

## 建新课程

用平台仓库的脚本，而不是手抄模板：

```bash
python scripts/new_course.py --id mit-6.5840 --out ../courses/mit-6.5840 \
    --title "Distributed Systems" --title-zh "分布式系统" \
    --institution MIT --course-number "6.5840 / 6.824" \
    --homepage "https://pdos.csail.mit.edu/6.824/"
```

它会连 `.github/workflows/` 一起复制，并生成干净的 `course.toml` / `glossary.toml`。
