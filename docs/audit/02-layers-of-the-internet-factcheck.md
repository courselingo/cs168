# 事实核对 · UC Berkeley CS168 第 2 讲 互联网是分层搭起来的

- 核对人：非作者（`fig-pruner`。**没有**参与本讲任何一轮写作，也没有与作者 `cs168-author` 讨论过本讲内容）
- 核对日期：2026-09-29
- 被核对版本：`content/02-layers-of-the-internet/index.md`，归一化 SHA256 前16 = **AA48DE94A748A005**
  （全 64 位 `AA48DE94A748A005E59645EB83835F0C0EB3969358890BB5AD8D65265E8C3C15`，17754 B）
  - 归一化 = `path.read_bytes().replace(b"\r\n", b"\n")` 之后再算 SHA256（工作区 CRLF、git 存 LF）
- 源材料（本次实际依据的，逐个列出）：
  1. **教材该节**：<https://textbook.cs168.io/intro/layers.html>（本次现抓，HTTP 200，34,565 B，SHA256 前16 `54B8BE6467012F5E`）
     - 转成「一元素一行」的 48 个文本块：11,299 B，SHA256 前16 `BD0F07DBD8592D01`。**本记录一律用 `t.N` 指这 48 块里的第 N 块**（`t.1` 是 `H1 Layers of the Internet`，`t.2` 起是各 H2 与段落）
  2. **教材根页（目录）**：<https://textbook.cs168.io/>（本次现抓，200，22,239 B，SHA256 前16 `C5492B3E0ED8773B`），用于核「第 1/3/4 讲」的讲次与标题
  3. 抓取方式：`curl.exe -s -L --max-time 40 -x socks5h://127.0.0.1:7892`，首次即 200（未出现 `000`）
  4. 本记录的英文引文一律照抄抓取到的 HTML 文本（源用弯引号 `’`），中译只为定位

## 结论

P0（事实错误）：**0 条** ｜ P1（易误解/依据不足）：**3 条** ｜ P2（措辞）：**4 条**

P0 = 0 的意思是：**逐块读完的范围内，没有找到与本教材该节相冲突的断言**；不等于我已验证全部主张（未核到的项目见最后一节）。

## P0 · 事实错误

**0 条。**

## P1 · 易误解或依据不足

1. **P1-1 · 「按平方级长」「长不大」是页面的推理，源只说了"不太高效"**（三、L59；同源的说法还有 L46「每加一片网络，就要跟已有的每一片都连一遍」与 L61 的 `alt`「左图的每台机器都要跟对面连一条线」）
   - 源 `t.11`（H2《Layer 3: Internet Layer》第 1 段）逐字：`One possible approach is to add a bunch of links between different local networks, but this doesn’t seem very efficient. (What if the two local networks were in different continents?)`
   - 源**没有**给出：连线数量的量级（平方级）、"每加一片网络就要与每一片已存在的网络相连"、"每台机器对每台机器连线"这三个论证；它只给了「不太高效」这个判断 + 「若两片网络在不同洲」这个反问。
   - 本页溯源（L190–191）只把「代价与边界」一段登记为我们的归纳，**没有**登记这一段推理 ⇒ 三处应就近标为我们的推理（结论本身合理，我**不判错**，只判归属）。
   - 检索范围与词：该节全部 48 块；`quadrat` 0 命中、`grow` 0 命中、`squar` 1 命中（唯一命中是 `t.23` 的画法约定 `draw end hosts as circles, and routers as squares`）、`efficien` 1 命中（就是上面那句 `doesn’t seem very efficient`）。
2. **P1-2 · 溯源点名的「代价与边界」一节在本页不存在**（溯源 L191：「「代价与边界」一段是我们的归纳，教材该节没有单列小标题」）
   - **标注确实存在**（Lead 点名要核的这处，答案是"标了"）；而且**实质正确**：那三条代价在源里查不到（`header` 0 命中、`overhead` 0 命中，整节 48 块）。
   - 但**本页没有叫「代价与边界」的小节**：本页 `## ` 共 13 个 —— 一、起点…／二、把两台机器连起来…／三、直觉做法为什么不行…／四、核心思路…／五、网络的网络…／六、抽象的层次…／七、第三层的服务模型…／八、分组…／九、第四层…／十、第七层与「不许跳层」，以及这两条规矩的代价／十一、脉络回顾／读完应该能回答／溯源。「代价与边界」只出现在溯源那一行里。
   - ⇒ 读者按这个名字找不到要核的段落（那段账实际在**第十节末段**「分层不是不要代价…」）⇒ 应把溯源里的名字改成「第十节末段」，或给那段加一个小标题。
3. **P1-3 · 「马车」不是源里的那一项**（一、L24：「邮政里这一步是邮差、**马车**、卡车或信鸽」）
   - 源 `t.4` 逐字：`In the postal system, this could be a mailman, the Pony Express, a truck, a carrier pigeon, etc.`
   - 源的第二项是 **Pony Express**（1860–61 年美国骑马接力邮递），页面写成「马车」；同句其余三项（邮差、卡车、信鸽）都对得上。
   - 检索：`carriage` 0 命中、`horse` 0 命中、`Pony` 1 命中（即上面那句）。建议改为「驿马快递（Pony Express）」或「快马邮递」。影响面很小（只影响类比里的举例），但它是名字被换掉，所以不放 P2。

## P2 · 措辞

1. **第三层的名字没有英文原名，与其它层体例不一致**（L181、L190 用「网际层」）
   - 其它层都给了原名：`physical layer`（L29）、`link`/`link layer`（L39、L46）、`transport layer`（L147）、`application layer`（L158）；只有第三层是纯中文「网际层」。
   - 教材该节的 H2 逐字是 `Layer 3: Internet Layer`（`t.10`）。
   - 另记一条**给你的回答**：你转述的作者要点「教材把第三层叫 Internet Layer，正式名是 network layer」——**本页里没有这句话**（页面既没提 network layer，也没给 Internet Layer 的英文原名），所以这一处没有"说错"，只有"没说出来"。
2. **海底光缆的例子丢了主体**（四、L82）
   - 源 `t.17` 逐字：`For example, if AT&T builds an undersea cable, they might charge a fee for other ISPs to send data through that cable.`
   - 本页写成「一条海底光缆修好之后，别的 ISP 想借道可能要被收费」——"谁建的、谁收费"这层结构没了（机制不变，例子变泛）。同段 `AT&T、亚马逊云，甚至伯克利自己` 与源一致 ✅。
3. **L116 那句读不通，且「协议之外」的对立不是教材的说法**
   - 本页：「所谓 [[term:protocol]]（protocol）之外，这里要谈的是另一件事：网络对用户承诺什么。」
   - 源 `t.31` 把服务模型说成 `a contract between the network and users, describing what the network does and doesn’t support`；该节并没有"在协议之外另立服务模型"这层对立（`protocol` 在该节只出现在别的上下文：`t.27` 下层协议可以变、`t.41`/`t.42` 传输层协议、`t.46` 第七层协议）。建议改写为「同一层除了协议本身，还要说清它对上层承诺什么」。
4. **「拿掉的保证被搬到上面几层去补」是我们的归纳**（七、L128）
   - 源 `t.34` 对"为什么选最弱的承诺"只给一条理由：`One major reason is, it is much easier to build networks that satisfy these weaker demands.`；"保证上移"这句话源里没有（源是在第四层才讲重发与排序，`t.41`）。建议标为我们的话。

## 已逐条回源、未发现问题的（抽样清单，供复核者不必重做）

- **13 处英文引文全部逐字一致**（只有弯/直引号差别）：`t.5`（电气工程那句）、`t.9`（分组与起止）、`t.11`（拉线）、`t.12`（邮局）、`t.15`（怎么找路）、`t.16`（容量）、`t.22`（端主机与交换机，本页按句截断，源同段还有一句举例）、`t.26`（Liskov：`“Modularity based on abstraction is the way things are done.” (Barbara Liskov, Turing lecture)`）、`t.32`（三种服务模型）、`t.34`（一条理由）、`t.37`（切分组）、`t.42`（流）、`t.47`（不许跳层）。
- **结构与顺序**：本页 `## ` 的推进顺序与源 H2 顺序一致（`Layer 1: Physical` → `Layer 2: Link` → `Layer 3: Internet` → `Network of Networks` → `Layers of Abstraction` → `Layer 3: Best-Effort Service Model` → `Layer 3: Packets Abstraction` → `Layer 4: Transport` → `Layer 7: Application`）⇒ 溯源 L190 的清单 ✅。
- **具体事实**：LAN 与 `e.g. all the computers in UC Berkeley`（`t.8`）✅；第二层的两件事（分组起止 + 多人共用一根线，`t.9`）✅；`switch or router`（`t.13`）✅；routing unit 与 congestion control unit 的分工（`t.15`、`t.16`）✅；ISP 与"经济与政治动机"、海底光缆收费（`t.17`）✅；不同链路可用不同第二层技术、L3 协议照样能用（`t.20`）✅；端主机圆 / 路由器方（`t.23`）✅；分层的两个好处（各自决定怎么送 + 创新并行，`t.27`、`t.28`）✅；服务模型 = 网络与用户的合同、Internet 一种都没选、只给 best effort（`t.31`–`t.33`）✅；分组的定义与"大小有上限"（`t.36`、`t.37`）✅；分组一生（发送方切片 → 一跳一跳 → 任何交换机都可能丢，`t.38`）✅；传输层的三件事（重发/切片/重排序，`t.41`）✅；应用层那个"若下层专为视频而建，邮件客户端就得自建基础设施"的例子（`t.44`）✅；这门课更关心基础设施而不是应用内容（`t.45`）✅；层间只依赖上下相邻层、只通过接口打交道（`t.46`、`t.47`）✅；第五/六层 1970 年代标准化时被认为需要、如今过时且功能基本落在第七层（`t.48`）✅。
- **讲次指针**（溯源 L192「第 1 讲是总览、第 3 讲讲首部、第 4 讲讲架构」）：教材根页目录显示 `/intro/intro.html` = `Introduction to the Internet`、`/intro/headers.html` = `Headers`、`/intro/architecture.html` = `Network Architecture`，本页是 `/intro/layers.html` = `Layers of the Internet` ✅ 四条路径与标题都对得上。

## 我核不到的（诚实记录）

- **L152「后面讲 transport-layer 的那一章，会把「怎么知道丢了」「重发多少次」「发快了会怎样」这些问题逐个展开」**：教材 `/transport/*` 各页（`Transport Layer Principles`、`TCP Design`、`TCP Implementation`、`Congestion Control *`）我**没有抓**，无法判断这三问是否对应其章节结构 ⇒ 不判对错。
- **L169「这些账会在讲架构那一节里再算一遍」**：`/intro/architecture.html` 我没抓。按目录标题看，第一条代价（每层一份 header）更像 `/intro/headers.html`（第 3 讲 `Headers`）的主题；**我读不到那两页，所以不判错**，只把这一处指涉记为待核。
- **授权（CC BY-SA 4.0）**：教材站根页的声明与 `docs/audit/license-cs168-second-review.md` 的双签不在本次范围，我未复核。
- **配图几何/像素**：本次只核正文与 `alt` 里的事实主张，没有渲染 SVG、没有量墨迹（那是视觉复核的活）。
- **检索范围与词**（否定性结论一律附范围）：
  - 全文范围：`layers.html` 转成的 **48 个文本块逐块读完**（含全部 H2 与段落，11,299 B，`t.1`–`t.48`）。
  - P1-1：`quadrat`、`grow`、`scale`、`squar`、`efficien`（命中数见 P1-1）。
  - P1-2：`header`、`overhead`、`interface`（`header`/`overhead` 各 0 命中；`interface` 1 命中，即 `t.47` 的接口与不许跳层）。
  - P1-3：`Pony`、`carriage`、`horse`。
  - 层名：`Internet Layer`、`network layer`（后者 0 命中）。
  - 讲次：抓教材根页目录一次（200）。

---

**核对人声明**：本记录只覆盖开头钉住的基线版本（前16 `AA48DE94A748A005`）。页面若再改动，结论不自动成立。本记录**不修改**任何正文、配图或 `status`——`status` 由 Lead 处理。
