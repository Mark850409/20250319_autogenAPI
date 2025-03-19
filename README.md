# AutoGen多功能查詢API

這是一個基於FastAPI和AutoGen框架開發的多功能查詢API系統，提供天氣查詢、網路搜索、知識問答和文生圖等功能。

## 功能特點

- 🌤️ **天氣查詢**：獲取指定地點的天氣信息
- 🔍 **網路搜索**：支持網頁、新聞和學術資料的搜索
- 💡 **知識問答**：回答用戶提出的各類問題
- 🎨 **文生圖**：根據文字描述生成相應的圖片

## 系統架構

```mermaid
graph TD
    Client[客戶端] --> API[FastAPI服務器]
    API --> Weather[天氣查詢團隊]
    API --> Search[搜索團隊]
    API --> Knowledge[知識問答團隊]
    API --> Image[文生圖團隊]
    
    Weather --> WeatherConfig[weather_team.json]
    Search --> SearchConfig[news_team.json]
    Knowledge --> KnowledgeConfig[knowledge_team.json]
    Image --> ImageConfig[image_team.json]
    
    subgraph 環境配置
        ENV[.env文件]
        WeatherConfig
        SearchConfig
        KnowledgeConfig
        ImageConfig
    end
    
    subgraph API端點
        Weather --> WeatherAPI[/weather]
        Search --> SearchAPI[/search]
        Knowledge --> KnowledgeAPI[/knowledge]
        Image --> ImageAPI[/image]
    end
```

## 系統要求

- Python 3.8+
- FastAPI
- Uvicorn
- AutoGen
- python-dotenv

## 安裝步驟

1. 克隆代碼庫：
```bash
git clone [repository-url]
```

2. 安裝依賴：
```bash
pip install -r requirements.txt
```

3. 配置環境變數：
   - 創建 `.env` 文件
   - 設置必要的API密鑰和配置

4. 運行服務：
```bash
python main.py
```

## API端點

### 1. 天氣查詢 `/weather`
- 方法：GET
- 參數：
  - location: 地點名稱（默認：台北）
  - detail: 是否返回詳細信息（默認：false）

### 2. 網路搜索 `/search`
- 方法：GET
- 參數：
  - query: 搜索關鍵字
  - num_results: 返回結果數量（1-5）
  - category: 搜索類別（web/news/academic）
  - search_type: 搜索類型

### 3. 知識問答 `/knowledge`
- 方法：GET
- 參數：
  - question: 問題內容
  - detail: 是否返回詳細解答

### 4. 文生圖 `/image`
- 方法：GET
- 參數：
  - prompt: 圖片描述文字

## 配置文件

系統使用JSON格式的配置文件：
- weather_team.json：天氣查詢團隊配置
- news_team.json：新聞搜索團隊配置
- knowledge_team.json：知識問答團隊配置
- image_team.json：文生圖團隊配置

## 錯誤處理

所有API端點都包含錯誤處理機制，返回格式：
```json
{
    "status": "error",
    "message": "錯誤描述"
}
```

## 開發團隊

[您的團隊信息]

## 授權協議

[授權信息] 