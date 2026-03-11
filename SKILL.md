---
name: square-daily-news
description: |
市场速递生成  每日加密器，适配币安广场风格。
  自动拉取热点 + 可选用户指定代币/观点 → 输出300-500字广场文章。
  触发条件：写今日市场速递、币安广场每日速递、市场速递、今日速递、发币安广场
metadata:
  author: QD
  version: "1.0"
  triggersJeffJia-inspired:
    - "写今日市场速递"
    - "币安广场每日速递"
    - "市场速递"
    - "今日速递"
    - "发币安广场"
---

# 币安广场每日速递

生成每日加密市场速递，适配币安广场风格（300-500字，数据驱动，谨慎中性）。

## 工作流程

### Step 1: 获取市场热点数据

使用 opentwitter skill 搜索加密市场热点：
```bash
curl -s -X POST "https://ai.6551.io/open/twitter_search" \
  -H "Authorization: Bearer $OPEN_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"keywords": "BTC ETH 加密", "maxResults": 10, "product": "Top"}'
```

或使用 web_search 搜索今日加密新闻。

### Step 2: 获取主流币行情

使用 Binance API 获取主流币价格：
```bash
curl -s "https://api.binance.com/api/v3/ticker/24hr?symbol=BTCUSDT&symbol=ETHUSDT&symbol=BNBUSDT&symbol=SOLUSDT&symbol=XRPUSDT"
```

### Step 3: 询问用户关注币种

问用户：今天想重点关注哪个代币？没有的话自动选热点币。

### Step 4: 获取代币详细信息

使用 jina-reader 或 web_search 查询代币近期走势、链上数据、背景故事。

### Step 5: 询问用户观点

问用户有没有特定观点想融入？没有则自动生成谨慎型观点。

### Step 6: 生成文章

根据以下模板生成文章，**注意添加合适的 emoji 表情配合内容**：

```
《今日市场速递》📈

大盘方面，{{主流币行情汇总}}，主流币24h涨幅大多集中在1%-3%区间📊。

今日热点：{{热点币}} 领跑热搜榜🔥；资金净流入前五为 {{资金流入榜}}。

重点关注：{{聚焦代币}}
{{代币背景故事}}
当前价格 {{价格}}，24h {{涨跌幅}}🚀。
链上数据显示：流动性 {{流动性}}，持仓地址 {{持仓数}}+，近24h活跃地址增长 {{活跃地址增长}}%💵。

观点：{{观点}}⚠️

数据来源：Binance Skills Hub，仅供参考，不构成投资建议🙂
```

**emoji 使用建议：**
- 涨幅大 → 📈🚀🔥
- 跌幅大 → 📉🔻
- 资金流入 → 💵👍✅
- 风险提示 → ⚠️🎯
- 整体乐观 → 😊👍
- 支撑位/机会 → 🎯🔄
- 成交量大 → 💵📊

### Step 7: 输出并建议发布

- 输出完整文章
- 建议发布到币安 Square
- 建议标签：市场速递、加密行情、{代币}

## 注意事项

1. 风格要符合币安广场：数据驱动、谨慎中性、轻提示风险
2. 字数控制在300-500字
3. 如果没有具体数据，可以用"热度较高""资金关注"等模糊表述
4. 观点尽量偏谨慎，但有数据支撑

## API 依赖

- 6551 Twitter API (OPEN_TOKEN)
- Binance Public API (无需 Key)
- Web Search (用于新闻/代币信息)
