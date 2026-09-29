# 讲次清单 · UC Berkeley CS168 Computer Networks

> 本文件定义这门课的「**全量**」= 下表全部讲授单元。逐讲产出一页。
> 授权：**CC BY-SA 4.0**（在线教材 `textbook.cs168.io` 站根页，`by-nc` 命中 **0** ⇒ 本站四门里唯一可商用的一门）。
> 第二人独立复核（Lead 签字）见 `docs/audit/license-cs168-second-review.md`。
> 依据：教材站**侧栏目录**（根页 + 8 个部分索引页，2026-09-29 抓取）；
> **52 条章节页逐条实测返回 200**（其中 2 条首次 `000`，重试后 200 —— `000 ≠ 404`）。

## 授权边界（写作时不变）

**可用**：教材正文（`textbook.cs168.io`，CC BY-SA 4.0）—— 可作讲解依据，也**允许**出译文
（Lead 已双签；本项目当前口径仍为 `explanation`，见平台仓 `docs/output-mode-decision.md`）。

**不可用**：**课程站**（`cs168.io` / `fa26.cs168.io`）的讲义、幻灯片、视频、项目、作业 ——
该站**未声明任何许可**，且第二人复核时**抓取 8 次全败**，如实记为「未复核」
⇒ `course.toml` 的 `[license.materials]` 的 `notes / slides / video / other` **维持 `false`**，**不产出**。

**永久排除**：**项目与作业解答**。课程站 Collaboration Policy 逐字要求
（`DO NOT POST SOLUTIONS TO PROJECTS ONLINE.`、`Publicly posting your solutions for any reason, including for your resume.`、
`This applies even after the semester is over.`）—— **这是学术诚信条款，与授权宽严无关。**

## 讲次表（52 讲，按教材侧栏顺序）

| # | slug（拟定） | 标题（原文） | 教材小节 |
| --- | --- | --- | --- |
| 1 | `introduction-to-the-internet` | Introduction to the Internet | `/intro/intro.html` |
| 2 | `layers-of-the-internet` | Layers of the Internet | `/intro/layers.html` |
| 3 | `headers` | Headers | `/intro/headers.html` |
| 4 | `network-architecture` | Network Architecture | `/intro/architecture.html` |
| 5 | `designing-resource-sharing` | Designing Resource Sharing | `/intro/sharing-resources.html` |
| 6 | `links` | Links | `/intro/links.html` |
| 7 | `introduction-to-routing` | Introduction to Routing | `/routing/intro.html` |
| 8 | `model-for-intra-domain-routing` | Model for Intra-Domain Routing | `/routing/model.html` |
| 9 | `routing-states` | Routing States | `/routing/solutions.html` |
| 10 | `distance-vector-protocols` | Distance-Vector Protocols | `/routing/distance-vector.html` |
| 11 | `link-state-protocols` | Link-State Protocols | `/routing/link-state.html` |
| 12 | `addressing` | Addressing | `/routing/addressing.html` |
| 13 | `router-hardware` | Router Hardware | `/routing/router.html` |
| 14 | `model-for-inter-domain-routing` | Model for Inter-Domain Routing | `/routing/autonomous-systems.html` |
| 15 | `border-gateway-protocol` | Border Gateway Protocol (BGP) | `/routing/bgp.html` |
| 16 | `bgp-implementation-and-issues` | BGP Implementation and Issues | `/routing/bgp-implementation.html` |
| 17 | `ip-header` | IP Header | `/routing/ip-header.html` |
| 18 | `transport-layer-principles` | Transport Layer Principles | `/transport/reliability.html` |
| 19 | `tcp-design` | TCP Design | `/transport/tcp-design.html` |
| 20 | `tcp-implementation` | TCP Implementation | `/transport/tcp-implementation.html` |
| 21 | `congestion-control-principles` | Congestion Control Principles | `/transport/cc-principles.html` |
| 22 | `congestion-control-design` | Congestion Control Design | `/transport/cc-design.html` |
| 23 | `congestion-control-implementation` | Congestion Control Implementation | `/transport/cc-implementation.html` |
| 24 | `tcp-throughput-model` | TCP Throughput Model | `/transport/throughput-model.html` |
| 25 | `congestion-control-issues` | Congestion Control Issues | `/transport/cc-issues.html` |
| 26 | `router-assisted-congestion-control` | Router-Assisted Congestion Control | `/transport/router-based-cc.html` |
| 27 | `dns` | DNS | `/applications/dns.html` |
| 28 | `http` | HTTP | `/applications/http.html` |
| 29 | `ethernet` | Ethernet | `/end-to-end/ethernet.html` |
| 30 | `layer-2-routing-stp` | Layer 2 Routing (STP) | `/end-to-end/l2-routing.html` |
| 31 | `arp` | ARP: Connecting Layers 2 and 3 | `/end-to-end/arp.html` |
| 32 | `dhcp` | DHCP: Joining Networks | `/end-to-end/dhcp.html` |
| 33 | `nat` | NAT: Network Address Translation | `/end-to-end/nat.html` |
| 34 | `tls` | TLS: Secure Bytestreams | `/end-to-end/tls.html` |
| 35 | `end-to-end-connectivity` | End-to-End Connectivity | `/end-to-end/end-to-end.html` |
| 36 | `datacenter-topologies` | Topologies | `/datacenter/topology.html` |
| 37 | `datacenter-congestion-control` | Congestion Control | `/datacenter/datacenter-cc.html` |
| 38 | `datacenter-routing` | Routing | `/datacenter/datacenter-routing.html` |
| 39 | `datacenter-addressing` | Addressing | `/datacenter/datacenter-addressing.html` |
| 40 | `virtualization` | Virtualization | `/datacenter/virtualization.html` |
| 41 | `software-defined-networking` | Software-Defined Networking | `/datacenter/sdn.html` |
| 42 | `host-networking` | Host Networking | `/datacenter/host-networking.html` |
| 43 | `multicast` | Multicast | `/beyond-client-server/intro.html` |
| 44 | `ip-multicast` | IP Multicast | `/beyond-client-server/ip-multicast-service-model.html` |
| 45 | `dvmrp` | DVMRP | `/beyond-client-server/dvmrp.html` |
| 46 | `core-based-trees` | Core-Based Trees | `/beyond-client-server/cbt.html` |
| 47 | `ip-multicast-challenges` | IP Multicast Challenges | `/beyond-client-server/ip-multicast-challenges.html` |
| 48 | `overlay-multicast` | Overlay Multicast | `/beyond-client-server/overlay-multicast.html` |
| 49 | `collective-operations` | Collective Operations | `/beyond-client-server/collective-operations.html` |
| 50 | `collective-implementations` | Collective Implementations | `/beyond-client-server/collective-implementations.html` |
| 51 | `wireless-links` | Wireless Links | `/wireless/wireless-links.html` |
| 52 | `cellular` | Cellular | `/wireless/cellular.html` |

**⇒ 52 个讲授单元。**（8 个部分：Introduction 6、Routing 11、Transport 9、Applications 2、
End-to-End 7、Datacenters 7、Beyond Client-Server 8、Wireless 2。）

## 不计入的条目（说明为何）

| 条目 | 为何不计入 |
| --- | --- |
| `/glossary.html` | 术语表页，不是讲授单元 |
| 8 个部分索引页（`/intro/`、`/routing/` … `/wireless/`） | 导航页，无独立讲解内容 |
| 课程站讲义 / 幻灯片 / 视频 | **未声明许可**（且未获第二人复核）⇒ 不产出 |
| 课程站项目与作业（含解答） | **学术诚信条款永久排除**，与授权宽严无关 |

## 备注

- **第 1 讲已产出**：`content/01-internet-architecture-and-protocols/`（≡ 本表第 1 行，教材 `/intro/intro.html`）。
  它的溯源里还引了 `/intro/layers.html`、`/intro/headers.html`、`/intro/architecture.html` **作背景** ——
  **那三节仍按本表各自成页**（第 1 讲是总览，第 2–4 讲把分层、首部、架构分别讲透），
  产出时会在两处互相点名，避免读者以为重复。
- **教材的层号取名与常见叫法有出入**：教材把第三层叫 **Internet Layer**（网际层），
  正式名是 **network layer**（网络层）；产出时两者都给出，并以教材为准。
- **`/routing/solutions.html` 不是习题解答**：它的标题是 `Routing States`（路由状态），
  属正文小节 ⇒ **计入**。（与「永久排除作业解答」不冲突。）
- 抓取注意：本站在本机代理下**会间歇性返回 `000`**（本次 52 条里有 2 条首次失败），
  **重试即成功**；`000` 不等于 `404`，**不可据 `000` 判断页面不存在**。
