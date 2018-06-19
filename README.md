# ServerStatus-Toyo： 

* ServerStatus-Toyo版是一個酷炫高逼格的雲探針、雲監控、伺服器雲監控、多伺服器探針~，該雲監控（雲探針）是ServerStatus（ https://github.com/tenyue/ServerStatus ）項目的最佳化/修改版。
* 線上示範：https://tz.toyoo.pw    
* 我的部落格：https://doub.io/shell-jc3/

# 目錄介紹：

* clients  使用者端檔案
* server   服務端檔案
* web      網站檔案  

# 更新說明：

* 2017.10.12, 負載Load 最佳化，並且支援CentOS6系統
* 2017.10.10, 修改負載 Load 的值為：目前伺服器上連結SSR等軟體的IP總數(只要軟體監聽IPv6那麼就能統計，例如SSH)
* 2017.04.30, 最佳化手機顯示式樣
* 2017.04.29, 去除主機名設定
* 2017.04.27, 增加一鍵部署腳本

# 安裝教學：     

執行下面的程式碼下載並執行腳本。
``` bash
wget -N --no-check-certificate https://softs.loan/Bash/status.sh && chmod +x status.sh

# 如果上面這個腳本無法下載，嘗試使用備用下載：
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/status.sh && chmod +x status.sh
```
下載腳本後，根據需要安裝使用者端或者服務端：
``` bash
# 顯示使用者端管理選單
bash status.sh c
 
# 顯示服務端管理選單
bash status.sh s
```
執行腳本後會出現腳本操作選單，選擇並輸入` 1 `就會開始安裝。

一開始會提示你輸入 網站伺服器的域名和埠，如果沒有域名可以直接回車代表使用` 本機IP:8888`

## 簡單步驟：

首先安裝服務端，安裝過程中會提示：

``` bash
是否由腳本自動設定HTTP服務(服務端的線上監控網站)[Y/n]
 
# 如果你不懂，那就直接回車，如果你想用其他的HTTP服務自己設定，那麼請輸入 n 並回車。
# 注意，當你曾經安裝過 服務端，同時沒有移除Caddy(HTTP服務)，那麼重新安裝服務端的時候，請輸入 n 並回車。
```

然後 添加或修改 初始範例的節點設定，注意使用者名稱每個節點設定都不能重複，其他的參數都無所謂了。

然後安裝使用者端，根據提示填寫 服務端的IP 和前面添加/修改 對應的 節點使用者名稱和密碼（用於和服務端驗證），然後啟動就好了，有問題請貼出 詳細步驟+日誌(如果有)聯繫我。

# 使用說明：

進入下載腳本的目錄並執行腳本：

``` bash
# 使用者端管理選單
./status.sh c
# 服務端管理選單
./status.sh s
```

然後選擇你要執行的選項即可。

``` bash
ServerStatus 一鍵安裝管理腳本 [vx.x.x]
-- Toyo | doub.io/shell-jc3 --
 
0. 升級腳本
————————————
1. 安裝 服務端
2. 移除 服務端
————————————
3. 啟動 服務端
4. 停止 服務端
5. 重啟 服務端
————————————
6. 設定 服務端設定
7. 查看 服務端訊息
8. 查看 服務端日誌
————————————
9. 切換為 使用者端選單
 
目前狀態: 服務端 已安裝 並 已啟動
 
請輸入數字 [0-9]:
```
# 其他操作

### 使用者端：

啟動：service status-client start

停止：service status-client stop

重啟：service status-client restart

查看狀態：service status-client status

### 服務端：

啟動：service status-server start

停止：service status-server stop

重啟：service status-server restart

查看狀態：service status-server status

### Caddy（HTTP服務）：

啟動：service caddy start

停止：service caddy stop

重啟：service caddy restart

查看狀態：service caddy status

Caddy設定檔案：/usr/local/caddy/caddy

預設腳本只能一開始安裝的時候設定設定檔案，更多的Caddy使用方法，可以參考這些教學：https://doub.io/search/caddy

——————————————————————————————————————

安裝目錄：/usr/local/ServerStatus

網頁檔案：/usr/local/ServerStatus/web

設定檔案：/usr/local/ServerStatus/server/config.json

使用者端查看日誌：tail -f tmp/serverstatus_client.log

服務端查看日誌：tail -f /tmp/serverstatus_server.log

# 其他說明

網路即時流量單位為：G=GB/s，M=MB/s，K=KB/s

伺服器總流量單位為：T=TB，G=GB，M=MB，K=KB

### CentOS7系統 負載顯示異常的問題

CentOS7系統 預設可能沒有安裝 netstat 依賴，所以會造成IP檢測(負載)出錯，手動安裝即可：
`yum install net-tools -y `

# 相關開源項目，感謝： 

* ServerStatus：https://github.com/BotoX/ServerStatus
* mojeda: https://github.com/mojeda 
* mojeda's ServerStatus: https://github.com/mojeda/ServerStatus
* BlueVM's project: http://www.lowendtalk.com/discussion/comment/169690#Comment_169690
