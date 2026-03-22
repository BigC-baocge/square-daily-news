---
name: square-daily-news
description: |
  币安广场每日速递（专业版）- 800-1000字深度分析，8大板块专业日报格式。
  自动拉取全球行情+地缘政治+宏观政策+DeFi+币圈要闻 → 输出深度分析报告。
  触发条件：写今日市场速递、币安广场每日速递、市场速递、今日速递、发币安广场
metadata:
  author: QD
  version: "2.0"
  triggersJeffJia-inspired:
    - "写今日市场速递"
    - "币安广场每日速递"
    - "市场速递"
    - "今日速递"
    - "发币安广场"
---

# 币安广场每日速递（专业版）

生成每日加密市场深度分析报告，适配币安广场风格（800-1000字，8大板块专业格式）。

## 核心升级（v2.0）

| v1.0 | v2.0 |
|------|------|
| 300-500字 | 800-1000字深度分析 |
| 简单4段 | 8大板块专业日报 |
| CoinGecko+DefiLlama | +东方财富+新浪财经+PANews |
| 基础行情罗列 | 全球行情+地缘政治+宏观政策+DeFi+币圈要闻+深度观点 |

## 工作流程

### Step 1: 获取全球市场数据

#### 1.1 主流币行情（必选）
```bash
curl -s "https://api.binance.com/api/v3/ticker/24hr?symbol=BTCUSDT&symbol=ETHUSDT&symbol=BNBUSDT&symbol=SOLUSDT&symbol=XRPUSDT"
```

#### 1.2 东方财富热点新闻（新增）
```bash
# 抓取东方财富 crypto/币圈 热点
curl -s "https://stock.eastmoney.com/a/cywjh.html"
```

#### 1.3 新浪财经币圈新闻（新增）
```bash
# 抓取新浪财经数字货币新闻
curl -s "https://finance.sina.com.cn/money/virtualcurrency/index.shtml"
```

#### 1.4 PANews 每日必读（新增）
```bash
# 调用 PANews API 获取每日必读
curl -s "https://api.panewslab.com/v3/articles?cid=8&limit=10"
```

#### 1.5 地缘政治数据（新增）
关注：特朗普政策、伊朗局势、美联储动向、ETF审批动态

### Step 2: 询问用户关注币种

问用户：今天想重点关注哪个代币？没有的话自动选热点币。

### Step 3: 生成8大板块专业报告

```
📊 《今日加密市场深度分析》

══════════════════════════════════
🌍 一、全球行情概览
BTC ${{价格}} (24h {{涨跌幅}}%)
ETH ${{价格}} (24h {{涨跌幅}}%)
SOL/XRP/BNB 关键位分析
══════════════════════════════════

🌐 二、地缘政治与宏观
• 特朗普政策最新动向
• 美联储利率预期
• ETF审批进展
══════════════════════════════════

💼 三、宏观政策动态
• 各国监管政策变化
• 机构入场/退场信号
• 传统金融拥抱加密进展
══════════════════════════════════

🔄 四、DeFi 生态数据
• TVL 变化趋势
• 主流协议锁仓量
• 借贷/DEX 活跃度
══════════════════════════════════

📰 五、币圈要闻速递
• 今日热点事件（3-5条）
• 机构动态
• 技术进展
══════════════════════════════════

💎 六、热点聚焦
{{聚焦代币}} 深度分析
• 基本面：{{背景故事}}
• 技术面：{{价格走势}}
• 链上数据：{{资金流向}}
══════════════════════════════════

🔍 七、情绪分析与信号
• 市场情绪指标
• 多空仓位变化
• 社区情绪倾向
══════════════════════════════════

💡 八、深度观点
{{AI生成专业分析}}
⚠️ 风险提示
══════════════════════════════════

数据来源：综合 Binance、东方财富、新浪财经、PANews
仅供参考，不构成投资建议🙂
```

### Step 4: 关键函数（新增）

#### 4.1 获取东方财富热点
```python
def get_eastmoney_hot_news():
    """抓取东方财富币圈热点"""
    # 解析 https://stock.eastmoney.com/a/cywjh.html
    pass
```

#### 4.2 获取新浪财经新闻
```python
def get_sina_finance_news():
    """抓取新浪财经数字货币新闻"""
    # 解析 https://finance.sina.com.cn/money/virtualcurrency/
    pass
```

#### 4.3 获取PANews必读
```python
def get_panews_daily_must_reads():
    """调用PANews API获取每日必读"""
    # GET https://api.panewslab.com/v3/articles?cid=8&limit=10
    pass
```

#### 4.4 地缘政治分析
```python
def analyze_geopolitical():
    """分析地缘政治影响"""
    # 关键词：trump/iran/fed/etf
    pass
```

#### 4.5 情绪分析
```python
def analyze_sentiment():
    """市场情绪分析"""
    # 基于新闻情感计算多空倾向
    pass
```

### Step 5: 输出并建议发布

- 输出完整 8 板块报告
- 建议发布到币安 Square
- 建议标签：#市场分析 #加密日报 #深度报告

## 定时任务

| 时间 | 内容 |
|------|------|
| 9:00 | 昨日全市场回顾 + 今日展望 |
| 21:00 | 当日总结 + 次日预警 |

## 注意事项

1. 风格：专业、深度、数据驱动
2. 字数：800-1000字
3. 观点：保持客观理性，标注风险
4. 数据：多源交叉验证

## API 依赖

- Binance Public API
- 东方财富爬虫
- 新浪财经爬虫
- PANews API
- Web Search（备选）
