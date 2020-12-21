# AIoT 期末報告
## 說明
- dataset\solar_data_202003_202007.csv 為 **新竹市北區海濱路240號** 新竹市環保局掩埋場復育地太陽能案場中在 **3月至7月** 其中一個inverter(逆變器)的太陽能發電資料

將資料集(dataset)內的 solar_data_202003_202007.csv 的太陽能案場發電資料做為訓練資料集訓練你的預測模型，預測 2020年一月、二月、八月、九月、十月的 **發電度數** 。

訓練完後需將模型做成 restful API 按照以下格式接收並回傳資料，restful API 需開啟對外連線的功能，可自行架設或直接使用 ngrok。

#### [作業網址: http://aiotfinal.ddns.net:8000/ ](http://aiotfinal.ddns.net:8000/)

### 範例： 輸入 JSON 格式

```
{
    "columns": ["YEAR", "MONTH", "DAY", "HOUR", "OPTPWR", "ACV1", "ACV2", "ACCL1", "ACCL2", "ACF1", "IIT", "IHT", "DCVL1", "DCVL2", "IPA", "IPB"],
    "questions": [
        [2020, 10, 6, 15, 13.52, 230, 226, 20.1, 19.3, 60.1, 41, 42, 749, 750, 6.73, 6.81],
        [2020, 1, 25, 12, 3.91, 229, 226, 6.2, 5.6, 60.1, 36, 39, 770, 770, 1.93, 2.01],
        [2020, 10, 19, 12, 24.94, 233, 230, 36.0, 36.2, 60.5, 44, 49, 754, 738, 12.44, 12.52]
    ]
}
```

### 備註：
- columns 為欄位名稱
- questions 為需要預測之資料(每次筆數不會固定)

&nbsp;

### 範例： 回傳 JSON 格式

```
{
    "predictions": [1.0, 2.0, 3.0] 
}
```

### 備註：
- 回傳的 predictions 帶入模型後回傳的資料

&nbsp;
### <font color=#F03C15>注意</font>
- <font color=#F03C15>回傳的 **predictions 長度** 要與 **輸入的 questions 長度** 相同</font>