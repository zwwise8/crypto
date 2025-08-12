# crypto
MANYU_data.parquet

block：以太链主网block number

vol：该block内的交易额，包括买入和卖出

net_vol：净交易额，买入交易额减去卖出交易额

trading times: 该block内的交易次数

price：该block内最后一笔交易的价格

------------------------------------

MANYU_trading.parquet

每一行是一笔完整的交易，固定交易额模式，即每次买入使用相同的金额

buy_block:买入时的block number

sell_block:卖出时的block number

pct：该笔交易的盈亏百分比，计算方法：sell_block的价格/buy_block的价格-1

holding_time:持仓时间，计算方法：sell_block-buy_block

sum_pct:盈亏百分比累加值

-------------------------------------

交易策略：长周期（30）和短周期（10）均线的双均线法

买入：当前block的短期均线值>长期均线值且当前空仓，则在下一个block买入

卖出：当前block的短期均线值<长期均线值，或当前block_number减买入时的block_number>300(1个小时)，或当前价格/买入时价格<0.95（亏损5%），则在下一个block卖出
