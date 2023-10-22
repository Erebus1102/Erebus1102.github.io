---
title: "Autonomous Networks"
tags:
- Study
- AN
---
# Communications is about moving information from place to place
It would be plausible that：
- the best way to send analog information is via analog communications
- the best way to send digital information is via digital communications
Shannon showed us that this is wrong, It is always best to use digital communications

# Shannon’s 3 theorems
1. Separation Theorem
![[content/notes/images/Pasted image 20230724110950.png]]
3. Source Encoding Theorem
Information 的衡量方式：bits/bytes （bytes = 8bit）
5. Channel Capacity Theorem
Physical links have finite capacity (bits per second)
$C = BWlog_2 (SNR+1)$

# Quality of Service & Quality of Experience
## QoS: 
## QoE: 

# Network
> [! Info]  早期的电报/电话都是单线传递的，但这种结构非常的低效（inefficient）。为了解决这个问题，网络结构诞生
	Networks are arbitrary connected graphs
	• nodes are called Network Elements
	• edges are links
	• End-points (customers) are nodes, and are called peers or hosts
	
**解决方案：** 通过将每个节点都介入网络中，然后为每个节点分配一个虚拟地址，然后按照某种方式在不同虚拟地址之间传播信息
- Autonomous networks can be joined to form **internetworks**
- Networks can be partitioned to form **subnetworks**
- **Virtual private networks (VPNs)** are subnetworks accessible by a customer and simulate a private network
## 信息论
- 从信息论的角度来看，网络具有输入和输出
- 信息在输入端输入到网络中，并需要在输出端无（或最小）损失地到达
- 将输入与输出相关联称为连接（关联是长期的）或流（关联是短暂的）
## Network value
**网络的价值：** 与 N 个节点通信的能力价值远大于与一个节点通信的价值。网络中的每个节点都愿意为与 N 个节点联系的能力付费，因此网络的价值是所有节点的价值总和。**价值随 N 呈超线性增长，这导致网络合并。**
### 网络价值计算法则
#### Metcalfe ’s Law 
>[!info] Metcalfe定律的基本思想是，网络中的每个节点都可以与其他节点进行通信，因此，节点的价值随着网络中节点数量的增加而增加。
$V \sim N ^{2}$
#### Reed ’s Law
>[!info] Reed定律的基本思想是，网络中的每个节点都可以与其他节点组成不同的子群，因此，节点的价值随着网络中子群数量的增加而增加。
$V \sim 2 ^{N}$
#### Odlyzko ’s Law 
>[!info] Odlyzko定律的基本思想是，网络中的每个节点都可以与其他节点建立连接，节点的价值随着节点数量和节点之间的连接数量的增加而增加。
$V \sim N log N$
#### Stein ’s LinkedIn Law 
>[!info] Stein's LinkedIn Law 的基本思想是，网络中的每个节点都可以通过朋友的朋友建立连接，节点的价值随着节点数量的增加而增加。
$V \sim N ^{4/3}$

# 网络的特征
## 链路 
物理层技术、同步/异步、QoS 参数、OAM 机制...
## 网络元素
功能、管理/非管理、参与控制协议、入/出端口数量、处理数据速率...
## 网络
规划、网络元素和链路数量、寻址、分段、分区、互通性、控制和管理机制...

## 研究方向
- 如何将香农理论扩展到网络中？ 
- 通信对全球能源消耗和二氧化碳排放的贡献为2％，如何设计网络以最小化能源消耗？ 
- 虚拟专用网络在单个全局网络中运行，如何避免入侵和资源窃取？如何保护隐私？ 
- 摩尔定律：最佳计算速率每2年翻一倍
- Butters 定律：光传输速度每9个月翻一倍，如何跟上这个趋势？ 
- 如何最优地规划庞大或快速扩张的网络？
	- 什么应该集中控制？
	- 什么应该分散控制？