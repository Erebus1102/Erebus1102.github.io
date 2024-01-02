---
title: Practice - 6 - 链上数据分析
tags:
  - Crypto
  - Coding
  - Transaction
  - Financial
---
# 0. SQL & Dune 部分略
# 1 . 链上数据分析
## 分析Token
- 空投维度
	- 空投领取情况：从领取空投的地址转移到其他地址的数量，但此数据和真实情况会有一定出入。最好还是找 even loss
	- 空投售卖情况：
- 筹码维度
	- 集中度分析：大户的百分比、筹码分布情况
	- 大户排名：
	- 大户持仓成本：
- 流动性维度 - 反映资产情况与变现能力
	- 流动性池：
	- 流动性分布：
	- 流动性变化：
	- 总流动性：
- Smart Money

## 分析运营
- 用户情况
	- 新用户：Approve 资产 *（授权给合约转移资产完成交易）*、合约交互用户（*统计 Flow 和 to 的数量*）
	- 主要用户地区：活跃交互时区
	- DAU：Daily UAW (Unique Active Wallet)
- ROI
	- 激励成本
		- Native Token Incentive
		- X2E
		- Referral
	- 营收：资产售卖、服务费收入
	- 激励效率：营收 / 成本
# 工作流
1. 找到合约
2. 定位哈希
3. 找到核心 Event Log
4. 根据 Event Log 编写基础表
5. 梳理表格结构与逻辑
6. 将原表的结构与想要构建表的结构，以及构建逻辑告诉 ChatGPT
7. 将代码粘贴到 Dune，若报错，则将报错的行和报错代码粘贴给 ChatGPT；若输出的查询不是自己想要的，则检查条件关系是否有漏
8. 得到查询数据，根据查询数据构建可视化







---
BackLink： [[content/1-Crypto/0. Crypto Index|0. Crypto Index]]