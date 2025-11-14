# Fundamental Analyzer Agent 任務指令

## 你的任務
你需要**自主搜尋並分析**台股公司的財務報表數據，計算關鍵財務比率。

## 執行流程

### Phase 1: 尋找財報數據源
1. **搜尋財報資料來源**
   - 關鍵字: "台灣上市公司財報 API", "公開資訊觀測站 財務報表"
   - 目標: EPS、ROE、負債比率、毛利率等

2. **探索可用工具**
   - 檢查是否有Python套件可以直接獲取
   - 評估 FinMind 的財報API
   - 備案: 從公開資訊觀測站爬取

### Phase 2: 下載財報數據
1. **讀取需要分析的股票清單**
   - 從 `data/raw/price_data/` 找出已下載的股票
   
2. **批量下載財報**
   目標格式:
```csv
   data/raw/fundamental/{stock_id}_financials.csv
   
   欄位:
   quarter,revenue,gross_profit,operating_income,net_income,
   total_assets,total_equity,total_liabilities,cash_flow_operating,...
```

3. **計算財務比率**
   根據 `financial_ratios.md` 的公式計算:
   - 獲利能力: EPS, ROE, ROA, 毛利率, 營益率, 淨利率
   - 財務結構: 負債比率, 流動比率, 速動比率
   - 經營效率: 存貨週轉率, 應收帳款週轉率
   - 現金流量: 營運現金流, 自由現金流
   - 估值: P/E, P/B, P/S, P/CF

### Phase 3: 輸出處理後數據
```csv
data/processed/fundamental_features/{stock_id}_ratios.csv

quarter,eps,roe,roa,gross_margin,debt_ratio,current_ratio,...
2020Q1,9.85,28.5,15.2,55.8,15.2,2.35,...
```

## 特殊處理
- **季報vs年報**: 優先使用季報
- **合併報表**: 使用合併財報而非母公司報表
- **異常值**: 標記並記錄異常財務數據
- **缺失值**: 記錄哪些公司哪些季度缺資料

## 輸出報告
`data/processed/fundamental_analysis_report.md`
