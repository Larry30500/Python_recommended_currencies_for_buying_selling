<h1 align="center">
  <br>
  [專題作品] 網路爬蟲-推薦外幣買賣
</h1>


## 目錄
* [作品簡介](#作品簡介)
* [作品內容](#作品內容)
* [設備與環境](#設備與環境)
* [聯絡資料](#聯絡資料)
* [致謝](#致謝)
* [權限](#權限)


## 作品簡介
### 提供圖形化介面操作，使用者輸入欲查詢天數，系統將推薦給使用者的目前外幣買入與賣出排序與資訊。
### 提供的功能為 (1)買入和賣出的外幣漲跌排序 (2)查看歷史匯率走勢圖 (3)開啟開臺灣銀行匯率網頁 (4)退出程式
#### 1. 使用 urllib.request/bs4 模組，自動抓取目前臺灣銀行的外匯資料。
#### 2. 使用 Tkinter 模組，產生圖形化介面，方便使用者檢視與操作。
#### 3. 使用 Matplotlib 模組，將外匯的歷史資料，彙整成趨勢圖。
#### 4. 使用 os 模組，創立資料夾並儲存圖片。
#### 5. 使用 webbrowser 模組，打開網站

  ![result_images](images/result.gif)

<strong><em>若您有興趣想更了解此程式，請參考下方的聯絡方式，進一步聯絡作者，謝謝參閱。</em></strong>


## 作品內容
### 1. 使用 urllib.request/bs4 模組，自動抓取目前臺灣銀行的外匯資料。
* 需先檢查是否已安裝 urllib.request 和 bs4 套件
  ```python
  import urllib.request
  from bs4 import BeautifulSoup
  ```
  
* content
* content
  ```python
  codes
  ```
  
* 從爬蟲獲取的外匯資料中，擷取需要的貨幣名稱和匯率
  ```python
  codes
  ```
  
### 2. 使用 Tkinter 模組，產生圖形化介面，方便使用者檢視與操作。
#### 使用 ...
* tkinter
  ```python
  codes
  ```
 
### 3. 使用 Matplotlib 模組，將外匯的歷史資料，彙整成趨勢圖。
#### 使用 ... 
 * clear_data 
  ```python
  codes
  ```

### 4. 使用 os 模組，創立資料夾並儲存圖片。
#### 使用 ...
* matplotlib 
  ```python
  codes
  ```

### 5. 使用 webbrowser 模組，打開網站
#### 使用 ...
* open_url
  ```python
  codes
  ```


## 設備與環境
### 電子設備/作業系統
* OS: Windows 7
* CPU: Intel(R) Core(TM) i5-4430 CPU @ 3.00GHz
* RAM: 8.00 GB

### 開發軟體/套件版本
* Python: 3.10.1
* urllib3: 1.26.4
* beautifulsoup4: 4.9.3
* matplotlib: 3.3.4
* tkinter: 8.6


## 聯絡資料
👤 **Larry**
  * Github: https://github.com/Larry30500
  * Email: larry30500@gmail.com


## 致謝
*非常感謝幫助過我完成此專案的所有開發者。*

*如果您喜歡此專案，記得點擊⭐️支持作者。*


## 權限
目前設定為 MIT 權限。請參閱 `LICENSE`，了解更多相關 MIT 權限的規定。

<br><br>[返回目錄](#目錄)

