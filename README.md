<h1 align="center">
  <br>
  [指定專題作品 (Python)] 推薦使用者買入與賣出外幣的系統<br>
  <h2 align="center">(網路爬蟲之應用)</h2>
</h1>


## 目錄
* [摘要](#摘要)
* [重點程式碼說明](#重點說明)
* [系統環境](#系統環境)
* [聯絡資訊](#聯絡資訊)
* [致謝](#致謝)
* [權限](#權限)

&nbsp;

## 摘要
### 1. 本作品內含網路爬蟲的相關技術，可自動擷取目前臺灣銀行之即時的外匯資料。
### 2. 設計圖形化介面的操作面板。
* 主要功能為：輸入欲查詢的天數，面板將顯示分析後的資料，並推薦適合買入與賣出的貨幣給使用者參考。
* 附加功能為：(1)繪出分析後的歷史外匯走勢圖，並儲存於資料夾中 (2)協助導覽至臺灣銀行外匯網頁。

![recommended_currencies01](images/recommended_currencies01.gif)

<strong><em>假使想要更加了解此程式的話，請參考本頁面底部之作者的聯絡方式。</em></strong>

&nbsp;

## 重點程式碼說明
### 1. 本作品內含網路爬蟲的相關技術，可自動擷取目前臺灣銀行之即時的外匯資料。
```python
# 於臺灣銀行的外匯資訊相關網頁 (https://rate.bot.com.tw/xrt?Lang=zh-TW)，讀取其網頁資料，並找到需要擷取的特定部分。
html_page = urllib.request.urlopen('https://rate.bot.com.tw/xrt?Lang=zh-TW')
sp = BeautifulSoup(html_page, 'html.parser')

# 從爬蟲獲取的外匯資料中，擷取買入/賣出的即期匯率及其對應的日期。
dates_in_source_codes = sp.select('日期')
spot_rates_codes = sp.select('匯率')
⋮

# 從擷取的即期匯率中，計算四種貨幣的匯率漲跌幅，根據匯率漲跌幅的高低，降序排列貨幣與資料的序位。
# 範例 [('澳幣', [最大值, 最小值, 平均值, 初始值, 現行值, 漲跌]), ('美金', [...]), ('人民幣', [...]), ('日圓', [...])]。
sorted_buying_spot_rates = sorted(buying_spot_rate_data.items(), key = lambda x: x[1][5], reverse = True)
sorted_selling_spot_rates = sorted(selling_spot_rate_data.items(), key = lambda x: x[1][5], reverse = True)
⋮  
```

&nbsp;

### 2. 使用 Tkinter 模組，產生圖形化介面的操作面板，方便使用者檢視與操作。
* 設計的操作面板具有 (1)分析資料 (2)清除資料 (3)檢視歷史外匯走勢圖 (4)導覽臺灣銀行外匯網站 之功能。
```python
def analysis_data():
  ⋮

def clear_data():
  ⋮

def check_chart():
  ⋮

def open_url():
  ⋮
```
  
![tkinter01](images/tkinter01.gif)

&nbsp;

### 3. 使用 Matplotlib 模組，繪出歷史外匯走勢圖。
```python
def check_chart():
  plt.figure(figsize = (15, 9), facecolor = 'whitesmoke', edgecolor = 'black', linewidth = 1)
  ⋮

  for index_currency_names in range(currency_amount):
    ⋮

    buying_line = some_buying_spot_rates[index_currency_names]
    selling_line = some_selling_spot_rates[index_currency_names]
    ⋮

    plt.subplot(currency_amount, 1, index_currency_names + 1)
    plt.plot(rate_dates, buying_line, color = plt_colors[index_currency_names], ls = '--', marker = 'x', lw = '2', ms = '7', label = plt_actions[0])
    plt.plot(rate_dates, selling_line, color = plt_colors[index_currency_names], ls = '--', marker = 'o', lw = '2', ms = '7', label = plt_actions[1])
    plt.legend(bbox_to_anchor = (1.1, 0.5), loc = 'right', prop = plt_font)
    ⋮  

    # 插入買入與賣出的外匯資料標籤。
    for a, b in zip(rate_dates, buying_line):
      plt.text(a, b, f'{b}', ha = 'center', va = 'bottom', fontsize = 7)
      ⋮

  plt.show() 
```

![matplotlib01](images/matplotlib01.gif)
  
* 以下為歷史外匯走勢圖
![twbank_currency_rates01](images/twbank_currency_rates01.png)

&nbsp;

### 4. 使用 os 模組，創建資料夾，創建前先檢查資料夾名稱是否存在，如果不存在，則創建新資料夾；如果存在則儲存圖片 (twbank_currency_rates.png)。
```python
def open_url():
  ⋮

  if not os.path.exists(folder_name): os.mkdir(folder_name)
  plt.savefig(f'{folder_name}/twbank_currency_rates.png')
```

![matplotlib02](images/matplotlib02.gif)

&nbsp;

### 5. 使用 webbrowser 模組，協助使用者導覽至台灣銀行的外匯網站。
```python
def open_url():
  webbrowser.get('C:/Program Files/Google/Chrome/Application/chrome.exe % --incognito').open_new_tab('網址')
```

![webbrowser01](images/webbrowser01.gif)
  
&nbsp;

## 系統環境
### 本程式所在作業系統
* OS：Windows 7 / 10 (Mac OS、Linux 系統亦可相容)

### 相關套件
* Python 核心：3.10
* Beautiful Soup：4.9

&nbsp;

## 聯絡資訊
👤 **Larry Jhuang**
  * Email: larry30500@gmail.com
  
&nbsp;
 
## 致謝
*非常感謝指導老師 (Francesco Ke) 提供程式設計的靈感和方向，並充分教導程式設計的注意事項和相關細節。*

*如果您喜歡此專案，記得點擊⭐️支持作者。*

&nbsp;

## 權限
目前設定為 MIT 權限。請參閱 `LICENSE`，了解更多相關 MIT 權限的規定。

&nbsp;

[[ 返回目錄 ]](#目錄)

