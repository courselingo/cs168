# 授权核实 · 第二人独立复核（Lead 签字）· UC Berkeley CS168

- **复核人**：CourseLingo Lead（独立于作者 `cs168-author`）
- **复核日期**：2026-09-29
- **复核对象**：`courses/cs168/course.toml` 的 `[license]` 段（`terms = "CC BY-SA 4.0（在线教材 textbook.cs168.io；课程站 sp25/fa26 未声明任何许可）"`）
- **复核方法**：`curl -x socks5h://127.0.0.1:7892` 抓**原始 HTML**，对 `rel="license"`、`by-sa`、`by-nc`、`All rights reserved` 各数一次，并抽出 CC 链接本身。
- **结论**：✅ **教材部分与作者记录一致，复核通过。**
  ⚠️ **课程站的「0 声明」我这次未能复核（抓取失败）—— 如实记为未复核，不假装核实过。**

## 1. 教材站根页（`https://textbook.cs168.io/`）· 复核通过

| 复核项 | 作者记录 | 我实测 | 一致 |
| --- | --- | --- | --- |
| `rel="license"` 命中 | >0（逐字给出 License 段） | **2** | ✅ |
| `by-sa` 命中 | — | **3** | ✅ |
| `by-nc` 命中 | **0**（这是四门里唯一不带 NC 的） | **0** | ✅ |
| CC 链接 | CC BY-SA 4.0 | **`http://creativecommons.org/licenses/by-sa/4.0/`** | ✅ |
| 抓取大小 | — | 22,239 B | — |

**⇒ `by-nc` = 0 这条我独立确认了** —— **它是本站唯一「译文可商用」的一门**，而这个结论的分量正在于 `by-nc` 恰为 0。

**⇒ `by-sa` = 3 且链接是 `by-sa/4.0`** ⇒ 与作者记录的 `terms` 逐字吻合。

## 2. 课程站（`https://cs168.io/`）· **未能复核**

**抓取 8 次全部失败**（本次未取得任何响应体）。

**⇒ 因此本文件**不主张**课程站「0 声明」这一点已被第二人复核。**
作者记录称课程站（sp25 / fa26）**未声明任何许可**；**那一结论我这次既未证实也未证伪。**
**⇒ 按保守一侧处理**：`[license.materials]` 的 `notes / slides / video / other` **维持 `false`**，
**课程站材料不进入产出范围**（与作者记录一致）。

## 3. 放行范围与义务

**⇒ 自本文件起，`cs168` 仓库中**由教材（textbook）衍生的产出**可以出译文。
课程站材料仍只能作原创讲解（且本次未经第二人复核，维持不产出）。**

| 要素 | 含义 | 对我们的约束 |
| --- | --- | --- |
| **BY** | 必须署名 | 每页给出教材名、作者与原文链接 |
| **SA** | 衍生作品须同协议 | 本仓库产出以 **CC BY-SA 4.0** 发布（与 6.006 的 BY-NC-SA、15-442 的 BY-NC **不能同仓**） |
| **无 NC** | **可商用** | 四门中唯一 |

**仍受排除**：**项目与作业解答**。课程站 Collaboration Policy 逐字要求
（`DO NOT POST SOLUTIONS TO PROJECTS ONLINE.` / `Publicly posting your solutions for any reason, including for your resume.` /
`This applies even after the semester is over.`）⇒ **这是学术诚信条款，与授权宽严无关，永久排除。**

## 4. 下一步（若要把某一讲改为 transcript）

1. **补做课程站第二人复核**（本次失败）—— 或**明确把范围限定在教材**，那样就不依赖课程站；
2. 该讲**实际依据的那份教材页面**单独取证一次（逐页原则，同 6.006）。
