## 1. 量化的概念与基本流程教学
### 1.1 量化的基本概念与特点
- 什么是量化: 是指利用数学、统计学和计算机科学等量化方法来进行金融市场分析、投资和交易的实践。它结合了金融学和量化技术，*旨在通过系统性的方法和模型来识别投资机会、管理。减少人为情绪和直觉性的干预*
- 风险和优化投资组合量化的核心思想: 基于大量的历史和实时市场数据，通过数学模型和算法来寻找和利用市场中的规律和趋势。*数据驱动，定量分析*。金融量化的目标是通过合理的模型和策略，获得持续稳定的投资回报
- 量化不是高频交易、自动交易，量化的核心是策略分析 (选股+择时)，*量化交易可以是高频的但不一定全部是高频的*
- 量化的优势: 纪律性、系统性、及时性、准确性和分散化
### 1.2 量化的基本流程
- 基本流程：In data -> Process -> Output Data
	- In data: 数据采集与预处理 （数据类型包括：行情数据、基本面数据、数据化的新闻、成交回报）
	- Process：量化分析、策略分析（选股、择时、仓位控制、止盈止损）
	- Output data：买卖信号和下单交易 （买入信号、卖出信号、交易费用、收益）
- 策略的生命周期：
	- 想法、实现策略、检验策略、运行策略、优化策略
- 量化的具体流程拆解：
	- 数据获取: 结构化数据 (行情、交易类数据) 、非结构化 (新闻、推文、公告、研报)
	- 数据分析与挖掘: 时间序列、统计、机器学习等
	- 构建信号: 基础信号->合成信号
	- 构建策略: 根据行情、持仓、调仓购买、风控等策略
	- 回测: 策略有效性和稳定性证明
	- 策略分析: 对交易策略的绩效进行评估和分析。包括计算收益率、风险指标、胜率等，并与基准进行比较。根据评估结果，进行策略的优化和改进。
	- 模拟交易: 接入实时行情数据
	- 实盘交易: 实时下单、撤单、考虑交易滑点、流动性等
## 2. 加密货币的数据收集和分析
### 2.1 数据分析的基本流程
- Objective： Input - to - Output
- 数据：
	- 收集数据：K 线数据、新闻、提案、推特等
	- 数据清洗与预处理：缺失值、异常值、重复值、时间顺序、时间间隔、数据完整性
	- 时间序列可视化
	- 数据探索性分析：均值、标准差、相关性、周期性、趋势
- 建模
- 评估模型
- 持续监控和更新
### 2.2 时间序列处理
- 创建时间序列
	- 创建一个包含时间序列数据的 DataFrame。可以使用 pd. Data_range ()来生成一组日期时间索引，然后将其与数据一起组合
```
import pandas as pd
import numpy as np

# 创建一个日期范围
data.rng = pd.data_range(start = '2023-01-01',end = '2023-12-31', freq = 'D')

# 创建一个包含随机数据的DataFrame
data = (value: np.random.randint(1,100, size = len(data.rng)))
df = pd.DataFrame(data, index = data.rng)
```
- 索引
	-  将日期列转换为时间序列类型、索引
	- To_datetime () 将包含日期和时间信息的字符串列转换为时间序列类型
	- 时间序列索引，同其他切片方法
```
# 创建一个DataFrame包含日期列
data = {'Data':['2023-01-01','2023-01-02','2023-01-03'], 'Value'：[10, 20, 16]}
df['Data'] = pd.to_datatime(df['Data'])

# 将日期列设计为索引
df.set.index('Data',inplace=True)

# 现在可以按照日期进行数据检索
selected_data = df['2023-01-01：2023-01-03']
```
- 重采样
	- Rule：指定重新采样的规则，可以是字符串或时间偏移对象
	- How：指定如何聚合数据。如（‘mean’、‘sum’、‘max’等），也可以是自定义函数
	```
	# 将每日数据重采样为每月数据，计算每月的平均值
	monthly. data = df. resample ('M') .mean（） 
	```
-  滚动计算
	- 滚动计算是一种常见的操作，用于计算时间序列数据中滚动窗口内的统计指标。滚动计算通常用于平滑数据、计算移动平均值、计算累积值等任务
```
# 基本语法: rolling_data = df[Column].rolling (window = window_size).agg (aggregation_function)
# 'Column'：要进行滚动计算的列
# 'Window_size': 滚动窗口的大小，表示在窗口内计算统计指标的数据含量
# 'aggregation_function'：指定如何聚合，如（‘mean’、‘sum’、‘max’等），也可以是自定义函数
rolling.mean = df['value'].rolling (window = 5).mean() 
```
### 2.3. 技术指标计算——TA-Lib
- TA-Lib（Technical Analysis Library 是一个流行的技术分析库，提供了大量的技术指标计算函数，如移动平均、相对强度指标、布林带等
- SMA （简单移动平均线）
	- 参数 1：收盘价序列，参数 2：时间周期（均线的计算长度即几日均线）
	- `sma_10 = talib.SMA (df['close'], timeperiod=10)` 
- RSI：
	- `Rsi_14 = talib.RSI(df['close'], timeperiod=14) `
- 万能 ta. Add_all_ta_features 计算所有指标: 
	- `df = add_all_ta_features (df, open="open", high="high", low="low”，close="close", Volume="volume",fillna=True) `
### 2.4. 量化常用的开源库
- Prophet: Facebook 开发时间序列预测库，用于预测金融时间序列趋势和季节性。
- Scikit-Learn: 用于机器学习和数据挖掘的 Python 库，可用于建立和评估量化金融策略 
- PyTorch: PyTorch 是深度学习框架，用于构建和训练复杂的深度学习模型 
- Keras: Keras 是一个高级深度学习库，使深度学习模型的构建更加简单
- XGBoost: 可用于回归和分类任务，常用于建立预测模型和特征工程 
- LightGBM: LightGBM 是另一个梯度提升库，适用于大规模数据和高维数据集
- Zipline: Zipline 是 Python 的量化金融库，可以用于策略构建和回测，同时与多个数据源和交易所接口兼容
- Backtrader: Backtrader 是一个用于策略开发和回测的 Python 框架，支持多种数据源和交易接口
## 3. CCXT 库操作
### 3.1 CCXT 和交易所 API
>[!TIP]  [CCXT](https://github.com/ccxt/ccxt) 是一个用于加密货币电子化交易的 JavaScript / Python / PHP 库，支持诸多比特币/以太币/山寨币交易市场的交易 API 。
>- **CCXT** 库可用于世界各地的加密货币/山寨币交易所的连接和交易，以及转账支付处理服务。它提供
>- 了快速访问市场数据的途径，可用于存储数据，分析，可视化，指标开发，算法交易，策略回测，机器人程序，网上商店集成及其它相关的软件工程。

- **CCXT STRUCTURE**
	- Unified CCXT API
		- Public
		- Private
	- Custom Exchange API
		- Public
		- Private
	- Base Exchange Class
- **API**（**A**pplication **P**rogramming **I**nterface）
>API 允许不同的软件应用程序之间共享数据和功能，从而使他们能够相互协作，实现各种任务和功能
- Web API: 通过 HTTP 协议提供的 API，通常以 JSON 或 XML 格式返回数据。Web API 通常用于访问互联网上的服务，如社交媒体 API、天气 API 等。
- 库或 SDK: 软件库或开发工具包，包含了一组函数和类，开发人员可以在自己的应用程序中直接调用。例如，Python 的标准库就是一组 API。
- *交易所 API: 提供了访问交易所的市场数据、执行交易、查询账户信息、安全性和身份验证等功能的接口*
### 3.2 创建交易所对象
>交易所类 (Exchange Class):  每个支持的交易所都对应一个交易所类，这些交易所类继承自 ccxt. Exchange 类，提供了与特定交易所进行交互的方法和属性。
	- 例如，ccxt. Binance 表示与 Binance 交易所进行交互的类，ccxt. Kraken 表示与 Kraken 交易所进行交互的类，以此类推。提供 api 密钥和私钥 (如果涉及私有函数)
	- 使用时要指定交易所，注意交易所数据是否受到限制
```
import ccxt
# 创建交易所对象（Example Binance）
exchange = ccxt.binance({
	'apikey'：'Your api key',
	'secret': 'your_secret_key'
})
```

### 3.3 公共方法和私有方法
#### 3.3.1. 公共方法
>公共函数 (Public Functions): 这些函数用于执行不涉及账户认证的公共操作，如获取市场数据、查询交易对、获取市场深度、获取 K 线图等。这些函数通常不需要 API 密钥，因此是公共可访问的。

- 常用的市场信息- Unified Public API
```
fetch_markets () # 获取所有可用交易对的信息
fetch_order_book (symbol, limit = None, params = {})# 获取指定交易对的市场深度数据。
order_book = exchange. Fetch_order_book ('BTC/USDT')
fetch_trades (symbol, since = None, limit = None, params = {})# 获取指定交易对的最新交易历史数据。
trades = exchange. Fetch_trades ('BTC/USDT')
fetch_ohlcv (symbol, timeframe = '1 m', since = None, limit = None, params = {}): # 获取指定交易对的 K 线图数据。
klines = exchange.Fetch_ohlcv ('BTC/USDT', timeframe='1 h')
```

> - 当 unified API 不能满足数据需求时, 查看交易所官方文档, 自定义 api 端点和 parameter。
> - publicGet 方法是一种特殊的方法, 它用于执行 HTTP GET 请求以获取与公共市场数据相关
的信息。这个方法通常用于查询市场信息、获取市场深度、获取交易对信息等。
- 基本语法1 : `exchange.publicGet(endpoint, params = {})
	`# Endpoint: 表示要访问的 API 端点/路径`
	`# Params: 表示可选参数` `
```
# 用例:
order_book = exchange.publicGet(
	'/api/v3/depth',
	{'symbol': 'BTC/USDT', 'limit': 10}
	)
```
- 基本语法 2 (拼接形式 (路径首字母大写)): `exchange.publicGetKlines(params = {})
	`params = {symbol:’BTC/USDT’, interval:’1d’}`
```
# 用例:
order_book = exchange.publicGet(
	'/api/v3/depth',
	{'symbol': 'BTC/USDT', 'limit': 10}
)
```
#### 3.3.2. 私有方法
>私有方法 (Private Methods): 私有方法用于执行需要账户认证的操作, 如下单、取消
订单、查询账户余额等。这些方法通常需要提供 API 密钥和密钥密钥。
```
查询账户余额 (fetch balance())
创建限价单和市价单(create_limit_buy_order()，create_limit_sell_order()，create_market_buy_order()，create marketsell_order())
查询订单状态 (fetch_order())
取消订单(cancel_order())
查询交易历史记录(fetch_my_trades())
查询充币和提币历史记录 (fetch deposit_history()，fetch_withdrawalhistory())
```
```
import ccxt
# 创建交易所对象（示例：Binance）
exchange = ccxt.binance({
	'apikey'：'Your api key',
	'secret': 'your_secret_key'
})
# 私有方法：下单
order = exchange.create_limit_buy_order('BTC/USDT', 0.001, 350000.0)

# 私有方法：取消订单
exchange.cancel_order(order['id'])
```
### 3.4 辅助方法和异常处理
#### 辅助方法
>辅助方法 (Helper Methods): 辅助方法用于执行一些通用的操作, 如将时间戳转换为日期时间、将日期时间转换为时间戳等
- .Parse 8601 (timestamp): 将 ISO 8601 格式的时间戳字符串解析为 Python 的 Datetime. Datetime 对象
- .iso 8601 (datetime): 将Python的Datetime.Datetime 对象格式化为ISO8601格式的字符串。
- .milliseconds ();. Microseconds () 返回当前时间的毫秒/微秒级别时间戳
```
import ccxt
# 创建交易所对象（示例：Binance）
exchange = ccxt.binance()

# 获取当前时间的毫秒级别时间戳
milliseconds.timestamp = exchange.milliseconds()
# 将毫秒级别时间戳转换为ISO 8601 格式的字符串
iso8601_datetime = exchange.iso8601(milliseconds.timestamp)

# 打印转换结果
print('毫秒级别时间戳：'，milliseconds.timestamp)
print('ISO 8601 格式的字符串：'，iso8601_datetime)
```
#### 错误处理
- 错误处理 (Error Handling): ccxt 库提供了一些异常类和错误处理机制, 以便捕获和处理与交易所通信过程中可能出现的错误。
```
ccxt.BaseError:所有ccxt异常的基类
ccxt.NetworkError:与网络连接或通信相关的错误，如连接超时、无法连接到交易所等
ccxt.ExchangeError:交易所返回的错误，如无效的交易对、无效的订单等ccxt.AuthenticationError:身份验证失败的错误，如无效的API密钥、密钥密钥等ccxt.InsufficientFunds’: 资金不足的错误，用于指示账户余额不足以执行交易。ccxt.Invalidorder’: 无效的订单错误，用于表示订单参数错误。
ccxt.0rderNotFound”:找不到订单错误，用于表示查询订单时未找到指定的订单ccxt.ExchangeNotAvailable:交易所不可用错误，用于表示交易所处于维护模式或不可访问。
```

```
#错误处理:捕获ccxt异常
try:
	#执行一些操作
except ccxt.BaseError as e:
	print(f"交易所错误: {e}")
except Exception as e:
	print(f"其他错误: {e}")
```

### 3.5 数据收集和策略实战
- 结合 for, def 等收集感兴趣币种 spot、option 的交易数据
- 构建策略和交易信号, 画图
- 根据交易信号进行回测, 计算回测的重要指标
- 回报率、最大回撤、年化回报率、胜率、盈亏比等
- 代码和不懂的指标问 chatgpt, 根据 chatgpt 写出的代码基础上进行修改和优化
- 回测分析、结合图表进行策略优化

## ChatGPT 代码修改实战
*Example:* 
[Intro_to_Quant3_DataCollection.ipynb - Colaboratory (google.com)](https://colab.research.google.com/drive/1oJJ1ay4MZ_llEHaTTOUQoWcC6J6amGqS?usp=sharing#scrollTo=m4IGnKPNwyUI)

## Reference
- [Intro_to_Quant1_Python.ipynb - Colaboratory (google.com)](https://colab.research.google.com/drive/1GgF0MTh-lAd1H4oL6A0bWn2nlFatwsIS?usp=sharing)
- [Intro_to_Quant2_Pandas.ipynb - Colaboratory (google.com)](https://colab.research.google.com/drive/1BKfCxjbsDjPOW6bDnujq128N_yVKwzvD?usp=sharing)
- [Intro_to_Quant3_DataCollection.ipynb - Colaboratory (google.com)](https://colab.research.google.com/drive/1oJJ1ay4MZ_llEHaTTOUQoWcC6J6amGqS?usp=sharing)
- [Gryphsis Academy 初级课程 - 币圈量化交易1- 量化与python基础 - YouTube](https://www.youtube.com/watch?v=lo9Jl_W9WWc)
- [Gryphsis Academy 初级课程 - 币圈量化交易2- Python 数据处理 - YouTube](https://www.youtube.com/watch?v=mmydroukRhc&t=3932s)
- [Gryphsis Academy 初级课程 - 币圈量化交易3 - CCXT 库 - YouTube](https://www.youtube.com/watch?v=6rVTjfT_vek)


---
BackLink： [[content/1-Crypto/0. Crypto Index|0. Crypto Index]]