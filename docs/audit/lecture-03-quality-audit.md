# 质量审核记录 · 03-headers（第 3 讲）

> §9 要求：`status = "reviewed"` 的前置条件是「**P0/P1 清零 + 有审核记录**」。
> 本文件是**自动生成的骨架** —— 机械部分已填，**判断部分留空待 Lead 填**。
> 自动生成时间：2026-09-29 12:45

## 1. 被审核版本

| 项 | 值 |
| --- | --- |
| 页面 | `content/03-headers/index.md` |
| 归一化哈希（CRLF→LF 后 SHA256 前 16） | `9B7EA14BF13B35AE` |
| 产出形态 | `output_mode = "explanation"`（依 `courselingo/docs/output-mode-decision.md` §3） |
| 源材料 | 见该页 front matter 的 `source_url` / `source_title` |

## 2. 六道机检（自动跑）

| 闸门 | 退出码 |
| --- | --- |
| `validate.py` | 0 |
| `check_style.py` | 0 |
| `audit_content.py` | 0 |
| `check_figures.py` | 0 |
| `check_reviewed.py` | 0 |
| `build_site.py` | 0 |

**✅ 六道全 0。**

## 3. 第一道人工闸门 · 非作者事实核对

- 记录：`docs/audit/03-headers-factcheck.md`
- **结论行（原样摘抄）**：P0（事实错误）：**0 条** ｜ P1（易误解/依据不足）：**2 条** ｜ P2（措辞）：**3 条**
- **⬜ 待 Lead 填**：逐条 P0/P1 的处置与复核情况

## 4. 第二道人工闸门 · 配图视觉复核（自动统计）

| 判定 | 张数 |
| --- | --- |
| 可用 | 5 |
| 需小修 | 3 |
| 有错误 | 0 |
| 判定无法解析 | 0 |
| 缺报告 | 0 |

**⬜ 待处置（非「可用」的图）**：

- `headers-1（需小修）`
- `headers-5（需小修）`
- `headers-6（需小修）`

⇒ 每一张要么改，要么写进 `docs/audit/visual-adjudications.md`（实测裁定，须含依据数值）。

## 5. 第三道人工闸门 · 透镜 3（陌生读者测试）

**⬜ 待 Lead 执行**（用一个**无项目上下文**的 subagent，只给它这一页 + 8 个机制问题）。

判据：❌ > 20% ⇒ P1；⚠️ > 40% ⇒ P1。

```
透镜 3：✅ ? 题 ｜ ⚠️ ? 题 ｜ ❌ ? 题
```

## 6. 本轮修复引入了什么新错

**⬜ 待 Lead 填。**

## 7. 结论

**⬜ 待 Lead 填**（P0 是否清零 / 三道人工闸门是否都过 / 是否同意提级）。
