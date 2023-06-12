# OKX-Python.Trading.Spot-Tutorial.Article-Chinese
OKX-Python交易现货-官方教程文章-中文翻译


## 原文链接

[OKX Learn-Tutorials-Article | How to trade spot on a Jupyter Notebook: Pt. 1](https://www.okx.com/learn/spot-trading-with-jupyter-notebook)

[OKX Learn-Tutorials-Article | How to trade derivatives on a Jupyter Notebook: Pt. 2](https://www.okx.com/learn/derivatives-trading-with-jupyter-notebook)

<br>
<br>

---

<br>
<br>

## 如何在 Jupyter Notebook 上交易现货：Pt.1

### 本教程将向您介绍如何通过在 Jupyter Notebook 上调用 python-okx 库中的函数来进行简单的现货交易。

以下是我们将在本文中介绍的步骤：

- 如何在 Jupyter Notebook 上运行 - - Python 代码片段
- 如何安装 python-okx 包
- 如何创建 API 密钥
- 如何导入 OKX 模块
- 如何访问我们的市场数据
- 如何阅读我们可用的交易对
- 如何读取您的账户余额
- 如何访问四种不同的帐户模式
- 如何确定您当前帐户配置的模式
- 如何下现货订单
- 如何访问订单的详细信息
- 如何取消订单
- 如何修改订单
- 如何访问未结订单列表
- 如何访问订单历史记录
- 如何使用 Jupyter Notebook 进一步使用 OKX API

### 如何在 Jupyter Notebook 上运行 Python 代码片段

#### Jupyter Notebook 

是一款功能强大且易于使用的 Python 开发和数据分析工具。 您可以在 Windows、Mac OS 或 Linux 上运行 Jupyter Notebook 服务器。

本教程提供了有关如何启动和运行 Jupyter Notebook 的非常全面的指南。

### 如何安装 python-okx 包
开始运行 Jupyter Notebook 后，只需在笔记本或终端（或通过 Windows 的命令提示符）运行 pip install python-okx 即可安装 python-okx 包：

'pip install python-okx --upgrade'

### 如何创建API密钥

在登录OKX后，您可以前往“账户”然后选择“API”以创建API密钥。

如果您要创建用于测试目的的API密钥，请确保前往“资产”，然后选择“模拟交易”。

您现在可以为您可能拥有的不同主/子账户创建API密钥。

在权限菜单中选择“交易”，以便使用API密钥进行交易。

您现在可以访问您的API密钥、秘密密钥和口令。请将它们放在安全的地方！

您可以在笔记本中实例化Python变量来保存您的API详细信息，以供以后使用。

    api_key = "xxxxx"
    secret_key = "xxxxx"
    passphrase = "xxxxx"
    
### 如何导入OKX模块

在python-okx中，我们提供了以下基于我们的REST API模块的模块。阅读我们的指南以了解如何导入[OKX模块](https://www.okx.com/docs-v5/zh/#overview-v5-api-key-creation)。

Trade
BlockTrading
Funding
Account
Convert
Earning
SubAccount
MarketData
PublicData
TradingData
Status
NDBroker
FDBroker

要导入Trade模块，您可以运行以下命令：

‘import okx.Trade as Trade’

恭喜，您现在已准备好使用python-okx中可用的全面功能！

### 如何访问我们的市场数据
有关如何访问我们的[市场数据的更多信息](https://www.okx.com/docs-v5/en/#rest-api-market-data-get-tickers)，请阅读我们的专门指南。

    import okx.marketData as MarketData

    flag = "1" #live trading: 0 , demo trading : 1

    MarketDataApi = MarketData.MarketAPI(flag=flag)

    result = marketDataAPI.grt_tickets(instType="SPOT")
    print(result)

### 如何访问OKX市场数据
如何阅读我们提供的交易对
有关如何阅读我们提供的[交易对的更多信息](https://www.okx.com/docs-v5/en/#rest-api-public-data-get-instruments)，请阅读我们的专门指南。

### 如何阅读我们的交易对
如何读取您的账户余额
有关如何读取您的[账户余额的更多信息](https://www.okx.com/docs-v5/en/#rest-api-account-get-balance)，请阅读我们的专门指南。

注意：在tdMode下进行现货交易，您主要需要检查每个ccy下的cashBal、frozenBal参数以及details，以及totalEq参数。

如何读取账户余额
如何访问四种不同的账户模式
在我们的统一账户系统中，有四种账户模式：

简单账户
单币种保证金账户
多币种保证金账户
组合保证金账户
为了了解不同账户模式之间的区别以及如何通过Web UI设置账户模式，请阅读我们的专门指南。

在保证金模式或交易模式下，参数tdMode决定了您的仓位如何进行保证金，每次下单都需要设置该参数。

对于在简单或单币种保证金账户模式下的现货交易，请将tdMode设置为'cash'。

对于在多币种保证金或组合保证金账户模式下的现货交易，请将tdMode设置为'cross'。

下面是一个快速说明，如何确定当前账户配置为哪种模式。

如何确定当前账户配置为哪种模式
有关如何确定当前账户配置为哪种模式的更多信息，请阅读我们的专门指南并输入acctLv参数。

如何确定当前账户配置为哪种模式
如何在简单/单币种保证金模式下下单
1. 如何下限价单
有关如何在简单或单币种保证金账户模式下下限价单的更多信息，请阅读我们的专门指南。

以下是以19,000 USDT的价格购买0.01 BTC的示例。

如何下限价单
2. 如何下市价单
有关如何在简单或单币种保证金账户模式下下市价单的更多信息，请阅读我们的专门指南。

以下是以当前市场价格购买100 BTC的示例：

如何下市价单
3. 如何在现货交易中使用目标货币参数tgtCcy
在现货交易中，参数tgtCcy决定了size参数sz的单位，可以是交易对的基础货币或报价货币。例如，在BTC-USDT这个交易对中，基础货币是BTC，报价货币是USDT。

默认情况下，tgtCcy = base_ccy，这意味着您指定的sz是基础货币的数量。然而，如果您将tgtCcy = quote_ccy设置如下所示，则您将购买价值100 USDT的BTC，而不是以市场价格购买100 BTC。

使用目标货币参数
4. 如何使用客户端订单ID参数clOrdId
当您下单时，可以通过指定参数clOrdId来指定自己的客户端订单ID，稍后可以在调用订单取消、修改或检索端点时使用它作为标识符。

使用客户端订单ID参数
如何访问特定订单的详细信息
有关如何获取特定订单的详细信息的更多信息，请阅读我们的专门指南。

1. 使用ordId
访问订单详细信息
2. 使用clOrdId
使用clOrdId访问订单详细信息
如何取消订单
有关如何取消订单的更多信息，请阅读我们的专门指南。

您也可以使用clOrdId而不是ordId。

如何取消订单
如何修改订单
有关如何修改订单的更多信息，请阅读我们的专门指南。

您也可以使用clOrdId而不是ordId。

如何修改订单
如何访问未完成订单列表
有关如何访问未完成订单列表的更多信息，请阅读我们的专门指南。

访问未完成订单列表
如何访问订单历史记录
1. 过去7天的订单历史记录
有关如何访问过去7天的订单历史记录的更多信息，请阅读我们的专门指南。

访问订单历史记录（7天）
2. 过去3个月的订单历史记录
有关如何访问过去3个月的订单历史记录的更多信息，请阅读我们的专门指南。

访问订单历史记录（3个月）
如何通过Jupyter Notebook进一步使用OKX API
有关更多示例，请下载完整的Jupyter Notebook。

如果您对我们的API有任何疑问，请随时在OKX API支持的Telegram频道中提问。

https://www.okx.com/docs-v5/en/#rest-api-market-data-get-tickers
