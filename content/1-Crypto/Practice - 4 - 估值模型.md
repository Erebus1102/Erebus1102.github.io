---
title: Practice - 4 - 估值模型
tags:
  - Crypto
  - Financial
  - Transaction
---
# 1 . 传统金融的估值模型
## 1.1. 估值流程
### Step 1 - 营收业绩拆分
- **自上而下 - 适合公司涉及行业对市场是新兴行业**: [宁德时代]( https://docs.google.com/spreadsheets/d/19amdACjlxEpa3RUv2d2yZc5oRY6SzQk1gdTWgPZ7hOQ/edit#gid=1259842236 )
	- *定义*: 自上而下估值法先从宏观经济因素开始分析，然后逐步细化到微观分析，最后到公司产品/技术层面（如锂电池材料）
	- *拆分思路*：对公司核心业务进行详细的拆分
	- *数据划分为*：Assumption（手动输入的预测值、可以修改）、Historical data (历史数据，不可修改) Formula (公式，不可修改)
- **自下而上 - 适合公司涉及行业对市场是传统行业**: [长江电力](https://docs.google.com/spreadsheets/d/1diIyZA4tMP2hPusGR_aTHikmw6KUetMPQUC6B0DAuzQ/edit#gid=129636194)
	- *定义*: 自下而上估值法从具体公司细节开始分析，然后可能考虑行业情况和更广泛的经济环境
### Step 2 - 基于营收拆分情况构建利润表、资产负债表和现金流量表
- *利润表*：根据拆分情况与加量关系进行利润表构建
- *资产负债表*
- *现金流量表*
## 1.2. 估值方法
### 方法一 - 绝对估值法
- DCF/折现现金流模型（核心思路：过去的 100 \$ 钱与现在的 100 \$ 价值是不等价的）
	- 
- 敏感性分析（由于 r 与终值对 DCF 结果的影响特别大，因此一般要进行敏感性分析）
- WACC（加权平均资本成本）
	- 定义：由于公司的融资来源于债券、股票两个途径，而两种途径的风险程度不同，所以两者的回报率不同
### 方法二 - 相对估值法
- PE、PS、PB、EV/EBITDA
	- PE：
	- PS：
 - 综合估值
	- 定义：通过 DCF、PE、PB、EV/EBITDA 等不同方式估值后得到一个估值区间

# 2 . 为什么要搭建估值模型
## For 投资
- 价格传导机制：基本面分析 -> 技术分析
- 评估项目低估还是高估
- 根据实际情况调整模型假设，更新估值
## For 融资
- 判断估值合理性
- 与投资人进行业绩对赌

# 3 . 如何构建代币的估值模型
## 3.1. 构建代币估值模型的可行性
- 传统金融存在较大信息不对称性，*而区块链技术降低信息不对称性，资金流更加透
- Token 通常有一定用途，可以会为 Token 持有人产生现金流
## 3.2. 数据源
- 公开信息
	- 传统金融：招股说明书、财报
	- Web3：白皮书/官方文档、链上数据
- 非公开信息
	- 传统金融：实地调研、专家 Call
	- Web3：Discord 询问、Twitter Space AMM
## 3.3. 业绩拆分
>[!Example] 业绩拆分案例 - DEX
>- 盈利模式：交易量驱动手续费收入
>- 量：自上而下，总交易量 -> DEX 渗透率 -> 协议市场份额
>- 价：手续费率，随着竞争的加剧，一般价格都会呈现下降趋势


>[!Example] 业绩拆分案例 - 借贷
>- 盈利模式：TVL 驱动营收
>- 量：自上而下，蓝筹币和稳定币有多少会存入借贷协议->资本利用率->借贷需求
>- 价 ：借款利率
## 3.4. 估值对象 - 是 Market Cap or FDV(Fully Diluted Value)？
- 传统金融：对 Market Cap 进行估值，因为不会有频繁的锁仓股票释放
- Web 3
	- 关注通胀率，若通胀率低，则用 Market Cap，通胀率高，则用 FDV
	- 同业对比的时候，保持估值对象的一致
	- 关注解锁周期
# 4.  Case Study
- [LSD 行业市场空间](https://docs.google.com/spreadsheets/d/1jpc44P6phYTRDMKG2LCITMMm9niKWUoOqiFb9dJClbs/edit#gid=1780010314)
	- 参与 LSD 的以太坊数量
	- LSD 的市场占有情况
	- 服务费情况
	- 以太坊价格变化情况
- [Radiant Capital](https://docs.google.com/spreadsheets/d/1RWfy-hkCgZEC5o-GXmxq376znpK67YYWQuOLsJVEs8k/edit#gid=1178455905)
	- 质押的稳定币、BTC、ETH、L 1、L 2 上币的 TVL 情况
	- 资本利用率
	- 加权风险水平结果
	- Total Fee of Holders
	- 折现率通过 CAPM 确定（将国债作为无风险收益率，将比特币看作是大盘）
- [DYDX](https://docs.google.com/spreadsheets/d/1SKk6RGApMKYhAF9gGhwCFykVJRXbbPjgxuW7pyS1fMM/edit#gid=1178455905)