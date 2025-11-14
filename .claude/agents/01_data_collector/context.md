# 台股市場知識背景

## 重要概念
- 台股交易時間: 09:00-13:30 (週一至週五)
- 漲跌幅限制: ±10%
- 股票代碼格式: 4位數字 (例如 2330 = 台積電)

## 常見數據源
1. **台灣證券交易所**: https://www.twse.com.tw/
2. **FinMind**: https://finmindtrade.com/
3. **公開資訊觀測站**: https://mops.twse.com.tw/

## Python套件參考
- `yfinance`: 台股需加 .TW 後綴
- `twstock`: 台股專用套件
- `pandas_datareader`: 支援多數據源

## 假日處理
台股不交易日包括:
- 週六、週日
- 國定假日
- 颱風假 (臨時公告)
