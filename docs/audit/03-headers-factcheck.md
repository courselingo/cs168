# 事实核对 · UC Berkeley CS168 第 3 讲 首部：网络只看信封，不看信

- 核对人：非作者（`fig-pruner`。**没有**参与本讲任何一轮写作，也没有与作者 `cs168-author` 讨论过本讲内容；本讲的 6 条方向自检是 Lead 转述给我的，我**不采信其附带的引文**，全部回源重核）
- 核对日期：2026-09-29
- 被核对版本：`content/03-headers/index.md`，归一化 SHA256 前16 = **05B935358F0D63D7**（15885 B；作者交付 commit `aa85d73`）
  - 归一化 = `path.read_bytes().replace(b"\r\n", b"\n")` 之后再算 SHA256（工作区 CRLF、git 存 LF）
  - 同次核到两张牵动结论的配图：`figures/headers-4.svg` 前16 `58EBBEF42058E436`（2123 B）、`figures/headers-6.svg` 前16 `E97ECB7732BDC869`（2899 B）
- 源材料（本次实际依据的，逐个列出）：
  1. **教材该节**：<https://textbook.cs168.io/intro/headers.html>（本次现抓，HTTP 200，35,279 B，HTML SHA256 前16 `356949B00ACDB70D`）
     - 转成「一元素一行」的 **56 个文本块**（11,077 字符，SHA256 前16 `36FB51F90A783D24`）。**本记录一律用 `t.N` 指第 N 块**（`t.1` = `H1 Headers`；源该节共 8 个 `[H2]`，见下）
  2. **教材根页（目录）**：<https://textbook.cs168.io/>（本次现抓，200，22,239 B，前16 `C5492B3E0ED8773B`），用于核第 2/4 讲指针与 `Addressing` 章节是否存在
  3. 抓取方式：`curl.exe -s -L --max-time 40 -x socks5h://127.0.0.1:7892`，首次即 200
  4. 本次另读了 `headers-4.svg`、`headers-6.svg`、`headers-7.svg` 三个文件的文本层（其余配图未读，见最后「没核到的」）
- 源该节 8 个 `[H2]`（用于核「结构跟随源顺序」）：`Why Do We Need Headers?`、`Headers are Standardized`、`What Should a Header Contain?`、`Multiple Headers`、`Addressing and Naming`、`Layers at Hosts and Routers`、`Multiple Headers at Hosts and Routers: Analogy`、`Multiple Headers at Hosts and Routers`

## 结论

P0（事实错误）：**0 条** ｜ P1（易误解/依据不足）：**2 条** ｜ P2（措辞）：**3 条**

P0 = 0 的意思是：**逐块读完的范围内，没有找到与本教材该节相冲突的断言**；不等于我已验证全部主张（未核到的项目见最后一节）。

## P0 · 事实错误

**0 条。**

## P1 · 易误解或依据不足

1. **P1-1 · `headers-6.svg` 的两列按行读会配错层次（图内版面，非源冲突）**
   - 图要表达的是源 `t.37`：`In summary: The lower 3 layers are implemented everywhere, but the top 2 layers are only implemented at the end hosts.` 与 `t.56`：`Each router parses Layers 1 through 3, while the end hosts parse Layers 1 through 7.`（就是「同一套下面三层」的包含关系）。
   - 但版面把它画成了：左列（端主机）五个框 `y=76/137/198/259/320` = 第七层/第四层/第三层/第二层/第一层；右列（路由器）三个框 `y=76/137/198` = 第三层/第二层/第一层。两列框高（36）与行距（61）**完全相同**，于是**按行读**得到的配对是 `第七层↔第三层`、`第四层↔第二层`、`第三层↔第一层`——正好把「同一套下面三层」画成了「三组不同的层」，与图本身要讲的包含关系相反。
   - 框内标签写得很清楚（「第三层：网际」等），所以**按标签读不会错**：这是版面/对齐问题，不是内容错误。建议把右列三框对齐到左列的第三/二/一层三行（`y=198/259/320`），或给两列补一条层次轴。
   - 我的判定依据只是这 4 个坐标值与两组间距相等这一事实；**若本项目的立场是「两列各自独立成栈，不要求跨列对齐」，本条可以降级**——但按行读出来的配对是错的，这一点是真的。
2. **P1-2 · 第八节自报的「账目数」与正文不符（内部不一致，非源冲突）**
   - 正文 L150 说「也带来了**几笔**账」，随后列 **第一笔**（开销，L152）、**第二笔**（格式改不动，L154）、**第三笔**（藏在分工里，L156），再加 **还有一点**（公开可见，L158）。
   - 但收尾的解读（L162）写「**两笔账**一笔来自体积，一笔来自时间」，配图 `headers-8` 的 `alt`（L160）也写「要付的**两笔**账：开销与格式固化」。
   - 读者跟着正文数到三笔（外加一点），再看到「两笔账」的总结，会以为漏了一笔、或以为第三笔不算账。建议把 L162 改成「这些账里最直接的两笔…」，或把第三笔与「还有一点」并进前两笔。

## P2 · 措辞

1. **P2-1 · L68「接收方才知道该读多少」是我们的补白**：源 `t.17` 只写 `The header could also contain other metadata like the length of the packet. Note that packets can vary in size (e.g. the user might only need to send a few bytes).`——没有写「接收方按它决定读多少」。无害，但属未标补充。
2. **P2-2 · L110「后面讲寻址那一章会把 IP 地址拆开细讲」**：源 `t.31` 只说 `As we look at the different layers in more detail, we'll see that different layers have different addressing schemes.`，没有点名某一章。教材目录里确有 `Addressing`（`/routing/addressing.html`）✅，所以指针成立；但「会拆开细讲 IP 地址」这句是补充。
3. **P2-3 · 溯源（L182）把整段「代价与边界」声明为我们的归纳**：方向保守、**不算错**；只是其中**第二笔**（部署后极难更改、标准组织会花好几年，L154 与 L50）**直接来自源 `t.11`**。建议写成「本段的归并与框架是我们的；其中第二笔的事实依据是源文」。

## 作者自报的 6 条方向自检 · 独立复核（不采信其引文，逐条回源）

| # | 作者自报 | 独立判定 | 我核到的源文（逐字） |
| --- | --- | --- | --- |
| 1 | 往下走是包上，往上走是剥掉 | ✅ 成立 | `t.25` `Notice that as we moved to lower abstraction layers, we wrapped more headers around the data. Then, as we moved to higher abstraction layers, we peeled layers off the data.`（页 L82 引用与 L83 中译都对；L85 的强调句也对） |
| 2 | 路由器先拆再包 | ✅ 成立 | `t.49` `The router reads and unwraps the Layer 1 and Layer 2 headers, revealing the Layer 3 header underneath.` + `t.50` `to pass the packet along to the next hop, the router must go down the stack again, wrapping new Layer 2 and Layer 1 headers` |
| 3 | **没有一台路由器会看到第三层以上**（否定的包含关系） | ✅ 成立，原文核到 | `t.51` 逐字 `Notice that none of the routers look beyond the Layer 3 protocol, because the upper layers are only parsed by the end hosts.` |
| 4 | 下面三层到处都要实现，上面两层只在端主机上 | ✅ 成立 | `t.37` 逐字 `In summary: The lower 3 layers are implemented everywhere, but the top 2 layers are only implemented at the end hosts.`（页 L122 引用逐字一致）；另 `t.56` `Each router parses Layers 1 through 3, while the end hosts parse Layers 1 through 7.` |
| 5 | 源地址不是送达所必需 | ✅ 成立 | `t.15` `Technically, the source address is not required to deliver the packet, but in practice, we almost always include the source address in the header.` |
| 6 | 首部一旦部署就很难改 | ✅ 成立 | `t.11` `Once we design a header and deploy it on the Internet, it's very hard to change the design (we'd have to get everybody to agree to change it). This is why standards bodies can spend years designing and standardizing headers.`（页 L50「是**很难改**，不是麻烦一点」与「花好几年」都对得上） |

**6/6 成立**，并且 6 条在正文里都确实写到了（依次落在 L85 / L140 / L140 / L122,L125 / L63 / L50,L154）。**方向没有一条写反。**

## 句中点名的另一处：`headers-4` 底部那行字有没有把两个方向写死？

**写死了，而且写了三处，三处一致**（逐字抄录）：
- `<title>`（该文件 L14）：`往下走一层层包上，往上走一层层剥掉`
- `<desc>`（L4）：`发送时从里往外一层层包上，接收时从外往里一层层剥掉。`
- 底部那行（L28）：`发送时从里往外一层层包上，接收时从外往里一层层剥掉`

三个全宽方框是「最外层：箱子／中间层：信封／最内层：信纸」，都没有箭头；方向信息由标题 + 底部行 + `desc` 三处承载，彼此一致，也与源 `t.25` 的两个方向一致（往下=包上、往上=剥掉；等价地：发送=从里往外、接收=从外往里）。

**⇒ 我的独立判断：不需要箭头，这行字够用，两个方向都写死了。** 本条我**不**记为 P1/P2。
（补充：`headers-7` 的 `desc` 同样把路由器两个方向写全了——`拆掉上一跳带来的第一、二层首部，露出第三层首部` + `再为下一跳包上新的第一、二层首部` ✅ 与源 `t.49`–`t.51` 一致。）

## 已逐条回源、未发现问题的（抽样清单）

- **11 处英文引文逐字一致**（源用弯引号 `’`、页用直引号，属排版差异）：`t.3`（交换机不知道拿这串比特怎么办）、`t.6`（邮局只读信封）、`t.9`（首部是 API）、`t.11`（部署后极难改）、`t.14`（必须有目的地址）、`t.15`（源地址非必需）、`t.25`（包上/剥掉）、`t.28`（有线发不了无线）、`t.32`（IP 地址编码位置；页用 `...` 标了截断，规范）、`t.37`（下面三层到处）、`t.51`（每跳先拆再包 + 不看第三层以上）。
- **事实清单**：`packet`/`header`/`payload` 的定义与分工（`t.3`–`t.7`）✅；端主机**自己必须懂首部**（`t.7` `the end hosts still need to know about headers`）✅；微软改首部别人读不懂（`t.10`）✅；标准组织花好几年（`t.11`）✅；三项「不是必需但有用」= 源地址（`t.15`）、校验和（`t.16`）、长度（`t.17`），页 L61 说「列了**三样**」✅ 数目对；公司秘书/收发室类比与拆箱顺序（`t.19`–`t.24`）✅；同层对端 + 秘书写名字给对方的秘书看（`t.26`）✅；协议与「第二层可选无线/有线」（`t.27`、`t.28`）✅；地址与名字三样（`www.google.com` / `74.124.56.2` / MAC **从不改变**，`t.32`）✅；Soda Hall 与街道地址（`t.31`）✅；端主机五层全有、路由器不看 L4/L7 且理由是「没有浏览器 + 不必操心可靠性（尽力而为）」（`t.34`–`t.36`）✅；主机 A 加首部顺序 7-4-3-2-1（`t.46`）✅；主机 B 剥掉顺序 1-2-3-4-7（`t.52`）✅；每跳可用不同的第一、二层协议（`t.53`–`t.55`）✅。
- **结构**：页 `##` 推进顺序与源 8 个 `[H2]` 顺序一致（页把源最后两个 H2「Analogy」与「正文」并进第七节）⇒ 溯源 L181 的清单 ✅。
- **L2 那条缺陷本讲没有重犯**：第 2 讲记录里我记了「溯源点名的小节名在页面里不存在」，本页 L148 **真有** `## 八、代价与边界` ✅。
- **该节确实没有代价那一段**：源 8 个 `[H2]` 里没有代价类小节，且 `overhead`/`extra`/`cost`/`bandwidth`/`waste`/`larger` 各 **0 命中**（唯一 `more headers` 命中是 `t.25` 的包上句，`size`/`byte` 各 1 命中是 `t.17` 的长度说明）⇒ 溯源 L182「教材该节没有单列这一节」✅ 实质正确。

## 我核不到的（诚实记录）

- **L110「后面讲寻址那一章会把 IP 地址拆开细讲」**：`/routing/addressing.html` 我**没有抓**，无法判断它是否「拆开细讲 IP 地址」；只核到教材目录里该章存在。⇒ 不判对错。
- **L158「网络地址转换与加密这两条路线，走的就是相反的方向」**：NAT（`/end-to-end/nat.html`）与 TLS（`/end-to-end/tls.html`）两节我没抓；教材该节也没有这句话（它在自报为我们的「代价与边界」段里）。
- **L168「下一讲会接着讲架构」**：目录核对 ✅（`/intro/architecture.html` = `Network Architecture`），但那一节内容我没读。
- **其余 5 张配图**（`headers-1/2/3/5/8`）我只读了正文里的 `alt`，没有逐张读 SVG 文本层；`headers-8` 的账目数问题（P1-2）是从 `alt` 与正文比对得出的。
- **授权（CC BY-SA 4.0）与第二人复核记录**：不在本次范围。
- **机检指标**（汉字数 3814 / 图 8 / 密度 2.10 / 术语标记 9）与图内像素、墨迹、总墨量：不在本次范围。
- **检索范围与词**（否定性结论一律附范围）：
  - 全文范围：`headers.html` 转成的 **56 个文本块逐块读完**（含 8 个 `[H2]` 的全部段落）。
  - 为 P1-2/溯源另检索：`overhead` `extra` `cost` `bandwidth` `waste` `larger` `byte` `size` `more headers`（命中数见上）。
  - 为 6 条方向自检另检索：`none of the routers`（1 命中，`t.51`）、`In summary`（2 命中，`t.37`/`t.56`）、`unwraps`（`t.49`）、`peeled`（`t.25`）。
  - 目录：抓教材根页一次，核 `Addressing` / `Network Architecture` / `NAT` / `TLS` 四条路径存在。

---

**核对人声明**：本记录只覆盖基线前16 `05B935358F0D63D7`（作者 commit `aa85d73`）；页面或配图再改动，结论不自动成立（P1-1 已把 `headers-6.svg` 的基线哈希一并钉住：`E97ECB7732BDC869`）。本记录**不修改**任何正文、配图或 `status`。
