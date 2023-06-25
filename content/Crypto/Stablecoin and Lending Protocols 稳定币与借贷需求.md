---
title: "Example Title"
tags:
- Web 3.0
- Crypto
- Financial Transaction
---
## 稳定币是什么

在公有链发行的，与法币挂钩的代币

最常见的稳定币与美元挂钩，其存在的目的是为了维持市场的稳定性。

占比最大的两个稳定比是Tether发行的USDT和Centre`s USD Coin 发行的USDC。

### 法币抵押 （Fiat-backed Stablecoins）

法币抵押类似传统金融中的 Full-reserve banking (全准备金银行) 系统，银行系统所拥有的现金资产对应银行的负债，而法币发行公司所拥有的现金资产对应发行的数字货币（即为公司的负债）。在全准备金系统中，资产和负债为1：1的关系，当数字货币持有者想要赎回自己的资产时，自己持有的货币会焚毁（burn)，而对应的资产会被取出。

> **USDT**  
>
> 由Tether发行，每枚USDT背后对应着存储在Tether公司内的一美元。根据Tether公司的描述，这些美金资产（不一定是现金，也有债券等现金等价物）都是可以通过Tether平台承兑或赎回的。
>
> USDT发行的目的是为了加速货币的流通，给到用户一个较为稳定的对价币种。
>
> Tether会定期展示资产情况、进行审计、公布审计结果及余额信息，但Tether依然被人诟病背后可能资产不足以支撑USDT的价值，这也导致了每过一段时间就会有USDT 会de-peg (脱钩) 的传闻。

**在传统银行中，银行股东通过银行费用所获利；而Tether公司的股东通过铸造、焚毁、赎回USDT过程产生的费用而获利。**

**只要资产足够且赎回的渠道是畅通的，套利者就可以为整个USDT注入流动性从而防止USDT与美金脱钩。**

### 加密资产抵押 （Crypto-backed Stablecoins）

加密资产抵押一侧的抵押物（Cash Assets）为加密货币，而另一侧为本公司发行的货币，发行的货币为本公司的负债（Liabilities）。由于加密货币抵押物的价值是浮动的，因此不能简单地使用1：1的比例进行抵押，否则当抵押的加密货币价值下跌时自己发行的加密货币就会出现脱钩的情况。

> **如：**当一家公司抵押了3000w USD的ETH,每个ETH在此时价值3000USD,而发行了价值3000USD的新加密货币ETH2.0。当ETH贬值到1500USD的时候，此时公司持有的抵押资产价格只等于自己所发行ETH2.0价值的一半 (抵押不足)，则无法继续维持ETH2.0的价格稳定和流动性，从而导致ETH2.0脱钩

**解决方法:** 通过在Cash Assets 与 Liabilities之间增加一个Buffer（缓冲区）使得Buffer+Cash Assets （总储备金）的总价值远远高于Liabilities，**这也是下文MakerDAO的原理**

**Buffer - Known as "Collateralization Ratio/系统质押率"**：通过持有的加密资产与负债的比例而确定

> **如：**当Buffer = 150%的时候，每价值1USD的流通稳定币背后至少有价值1.5USD作为抵押

这也就保障了当所持有的加密资产价格下跌的时候，整个公司所持有的资产能够保障发行货币的价格不会de-peg

#### **DAI （由MakerDAO所发行的稳定币）**

​	USDT\USDC所存在的问题与传统金融行业中的问题相似，法币抵押稳定币的价格依赖于社会体系以及法律体系。若银行资产被冻结、审计、会计存在欺诈行为等等（如SVB），则用户手中的稳定币就变成了 “I own you” 的借条，因此法币抵押也被称为 “IOU” 模式。同时当区块链上的公司计划实行相同的模式时，会引入非常多不被信任的中间商（会计、审计等）这样的机制不太符合Web3.0 “去中心化自治” 的要点。

##### DAI的机制

​	DAI的核心机制被称为Collateralized Debt Position (CDP)，它的工作原理类似于实体资产抵押贷款：

> 假如你打算通过自己的房产抵押来进行贷款，当我们的房产贬值、银行判断我们无法正常偿还贷款的时候，就会**首先要求我们提前偿还贷款，如果我们无法提前偿还贷款，银行就会收走我们的房产；**
>
> 同理以太币（Ether）类似你所抵押的房产，当你抵押的以太币贬值的时候，MakerDAO会首先要求你偿还你的贷款，或者MakerDAO会向出价最高者拍卖掉你所抵押的Ether来偿还你的贷款。

会出现两种情况：1. 以太坊价格上涨；2. 以太坊价格下跌

我们其实不太需要考虑以太坊价格上涨的情况，因为当Ether价格上涨，则系统质押率会更高。因此你所抵押的Ether就可以Mint (铸造) 出更多的DAI，从而造成DAI价格的升高。

 而当以太坊价格下跌到一个点， (MakerDAO不会等到Ether价格下跌使得DAI单价低于1USD/de-peg的时候再进行相关的操作，一般在Ether出现价格下跌趋势，机构判断DAI存在脱钩风险的时候就开始了）MakerDAO便会拍卖或者要求持有者提前偿还。

**详细流程：**

​	当铸造DAI以后，CDP机制就会像保险箱一样将持有者质押的Ether “锁” 起来。而DAI的持有者随时可以赎回自己质押的Ether。

​	每当用户操作赎回自己的Ether时，会有一笔成为Stability Fee的价格被收取，可以将Stability Fee的看作是借贷的利息（interest on the loan)。然后还回去的DAI会被系统销毁，Ether会取出还给持有者，从而达到平衡机构内Ether与DAI比例的目的。

> **Example:**
>
> 假设：
>
> * Stability fee = 2% (这笔钱收取后会存放到Buffer Pool中，Buffer Pool不属于任何人，Work as reserve fund)
> * Collateralization Ratio 联合质押率 = 150%
>
> * **初始状态：**$ 1 ETH = \$ 3500 = generated => 2000 DAI$
>

**若：** 1 ETH 下跌到 \$2900，则此时1Ether能铸造的最大DAI数量为：$2900/150\% = 1933$ 

此时生成的2000个DAI超过了系统允许的1933个，则此Vault（CDP）就将被清算来还掉欠的2000个DAI，**同时还需要缴纳一笔清算的罚款** （13% ~ 33%， 该区间由MKR token holders投票决定）。

具体的罚款值由拍卖的单价决定，拍卖价格越高，持有者的损失越少，则罚款也就越少。
$$
the\ liquidation\ price = number\ of\ DAI * liquidation\ ratio = 2000 * 150\% = $ 3000 \\
即：当以太坊的价格跌至3000以下的时候，系统就将进行清算\\
the\ liquidation\ penalty = least\ 13\% * the\ liquidation\ price = 3000*13\% = 390\ DAI\\
total\ outstanding\ debt = the\ liquidation\ penalty\ +\ number\ of\ DAI  = 2000+390 = 2390\ DAI\\
机制目的: Total\ Colleteral > Total\ outstanding\ debt
$$
要求确保出价能够覆盖负债，因此整个拍卖过程包含两个阶段：

| Phase 1 “Setting Price” (保证债务能Cover)   | Phase 2 “negotiation” (减少被清算者损失)     |
| ------------------------------------------- | -------------------------------------------- |
| 2000 DAI for 1 ETH                          | For 2390 DAI, 出价0.95 ETH                   |
| 2200 DAI for 1 ETH                          | For 2390 DAI, 出价0.90 ETH                   |
| 2400 DAI for 1 ETH -> 满足 outstanding debt | For 2390 DAI, 出价0.87 ETH -> 没有更低出价者 |

假设此时出价者通过0.87 ETH，拍卖得到2390个DAI。其中2000DAI被用于还款，而390DAI被用于缴纳罚款。此时竞拍者获得的ETH的实际价值高于2390DAI或对应的每ETH高于 $2390/0.87 = \$2747 $，而此时ETH的售价为$ 2900，则此时竞拍者获利。

------

**罚款比例的计算：**

在本次清算（Liquidation）中，持有者将一个ETH（价值\$3000）生成了2000DAI，而清算结束后他持有2000个DAI和0.13（价值\$390）个ETH，总亏损为$\$610\  (=3000-2000-390)$，此时的罚款比例为 $20.33\%\ (=610/3000)$。

如果想进一步降低被清算者的损失，假设有竞拍者使用0.797个ETH拍得3000个DAI，则此时的罚款比例达到了最低的13%。

而如果在第一阶段叫到2390DAI便结束，而第二阶段无人继续叫价，则用户会面临Full liquidation (利用1ETH全部偿还2390DAI)，此时他将拥有2000DAI和0ETH，总损失1000，罚款比例为$33\%\ (=1000/3000)$。

------

**当以太坊继续暴跌的情况下…：**

若以太坊继续暴跌，假设一阶段最高报价为\$1500，则此时CDP全部清空后持有者将持有2000DAI + 0ETH，而此时系统的OutStanding Debt 为 $\$890 DAI (=2390-1500)$。此时Vault中没有任何资产可以用来清算，而系统处于欠债情况，则此时需要Buffer Pool参与工作。

系统会将Buffer Pool中对应金额的DAI拿出来销毁掉以补足欠债；

当Buffer Pool中的DAI依然不足以偿还债务的时候，Debt Protocol 会被激活。系统会生成MKR代币进行拍卖，直到拍卖价格补足Outstanding debt。

> 那MKR是否就是没有价值，只是机构用于印钞抵债的骗局工具的呢？
>
> 当正常情况下，Buffer Pool通过Stability fee和Liquidation Penalities是在不断积攒的，在这种情况下机构会从Buffer Pool中取出DAI来购买流通市场上的MKR并销毁掉，从而保证流通市场上MKR的价值属性。

------

**The DAI Saving Rate （DSR）：**

用户可以将自己持有的DAI存入DSR合约中来赚取利息，其实就是将DAI存入Buffer Pool中来积攒机构的风险抵抗能力，同时可以鼓励用户持有DAI；

当市场上的DAI流通量过高导致DAI的单价低于 $1，机构可以提高DSR的利率来吸引用户将DAI存入Buffer Pool，通过这种方式降低市场上的流动率从而提高单价；相反当DAI的单价过高的时候，机构可以选择降息。

##### MakerDAO的发展历史

* **Peg Stability Module（PSM）与MakerDAO在2023/3脱锚的原因**

  MakerDAO的PSM是一种允许用户以零成本将法币支持的稳定币与\$DAI交换的工具；

  使用PSM模块不会将你的法币支持的稳定币抵押在金库中，而是直接将它们兑换成\$DAI，用户也可以将\$DAI兑换成PSM模块，并获得法币支持的稳定币；

  PSM加强了\$DAI和美元之间的联系，允许Traders利用\$DAI和其他法币支持的稳定币之间的价格差异套利；

  PSM改变了MakerDAO的资产负债表。

  |                    Asset                     |   Liability    |
  | :------------------------------------------: | :------------: |
  | Loan from minting DAI (secured by ETH, WBTC) | DAI (from CDP) |
  |     Fiat-backed stablecoins (USDC, USDP)     | DAI (from PSM) |

  * **PSM的问题：**由于现在生成DAI的对应资产中37.2%（最大份额）是USDC（通过PSM）直接兑换而来，而USDC的Swap并不能像ETH/BTC一样产生Stability fee和Penalty fee，从而导致DAI也承受USDC的风险。

    即：如果USDC收到影响，而大量的Swap过程没有给Buffer Pool带来足够的增量，DAI也会承受来自USDC的压力。

  * **PSM的补足手段：**

    由于PSM工具的Allowanc有一个hardcap上限，当达到这个上限的时候用户只能用1 DAI 换1 USDC，但不能用1 USDC 换 1 DAI，这确保了DAI的数量不会疯狂上涨造成贬值，从而确保了DAI的价值不会低于USDC的价值；

    当时也有非常多的交易员通过做多DAI，做空USDC来赚取价差。只要USDC价格跌幅大于DAI的价格跌幅，这之间的差距就可以保证该策略有效盈利。

    如果USDC贬值（如\$0.98），MakerDAO通常会增加铸币费来维持USDC与DAI直接价格的锚定（即增加PSM工具的使用费用来注入Buffer Pool）。在某些情况下，MakerDAO可能需要吸收与这些债务有关的损失，以确保DAI价格的稳定。
    在极端情况下，如市场崩溃，借款人可能会购买DAI来偿还他们的债务。这将导致对DAI的需求大幅增加，从而推高其价格。在这种情况下，PSM可以帮助平衡市场，提供一种机制，允许用户以固定利率交换DAI和USDC，从而促进DAI价格的稳定。

* **RWA  （Real World Asset）**
  * RWA 是 MakerDAO 的一种新概念，它代表了 MakerDAO 投资于现实世界资产的价值。
  * 考虑到$USDC是由美元存款和美国政府债券支持的，直接投资于美国政府债券可以减少风险，并且基本上价值相似的资产。
  * MakerDAO设计了一个信托结构来间接持有现实世界的资产，这样做可以降低 MakerDAO 的风险，并增加其收入。
  * MakerDAO 的 RWA 概念的 token 是 MKR，它是一种能够给协议带来盈利能力的 token。

|                    Asset                     |   Liability    |
| :------------------------------------------: | :------------: |
| Loan from minting DAI (secured by ETH, WBTC) | DAI (from CDP) |
|     Fiat-backed stablecoins (USDC, USDP)     | DAI (from PSM) |

