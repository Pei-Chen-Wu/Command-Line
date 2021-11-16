# Command Line 指令
## 基本指令
### 檔案操作
* ls（list）
    * 列出所有檔案和路徑 
    * 變化型
        1. 列出隱藏的目錄：ls -a
        2. 列出詳細資料：ls -l (ll)
        3. 包上述兩個：ls -la
        4. 列出 .js 的檔案：ls *.js
* cat（catenate）
    * 將檔案內容顯示在 Terminal 面板
* echo
    * 印出字串在 Terminal 面板
    * 印出字串在檔案中

* less
    * 將檔案內容以分頁顯示在 Terminal 面板 (僅閱讀)
* grep
    * 抓取特定關鍵字，並高亮顯示（有分大小寫）
    * 寫法：grep 字串 檔名
* wget
    * 下載檔案至當前目錄
    * 不是每台電腦都有的指令，可以透過 Homebrew 進行安裝。
    * 安裝指令：brew install wget
    * 寫法： wget 圖片網址
* vim
    * 進入 vim 編輯器，分為普通模式跟編輯模式
    * 對應 key：
        * i / o / a 進入編輯模式
        * esc 進入普通模式 (選取複製 右鍵貼上)
        * :q 退出
        * :wq / :x 存檔後退出
        * :w 存檔
        * :q! 不存檔直接退出
        * /word 搜尋
        * :number 到那行
* tail
    * 印出檔案的最後幾行
    * 變化型：tail -f 常用於 web server 查看 log debug 時

* head
    * 可以將一段文本的開頭一部分輸出到標準輸出（默認輸出前10行）
    * 變化型
        * -n: 輸出的行數（可以負數，表示輸出除了後x行以外的全部內容）
        * -c: 輸出的字節數

* find
    * 尋找檔案的指令，會將欲尋找的檔案找出來
    * [root@tsai /root]# find / -name bin
    * 上面的意思為：在 / 目錄（根目錄）下尋找檔名（-name）為 bin 的檔案，要注意的是，因為 Linux 的檔案很多，如果你的電腦比較舊，可能會找很久
### 目錄操作
* cd（change directory）
    * 切換目錄
    * 變化型
        1. 回到 home 目錄：cd ~ # 屬於使用者底下的資料夾
        2. 回到根目錄：cd / # 電腦最底層
        3. 回到上一層資料夾：cd ..
    * 訣竅
        * 輸入前幾個字母，再按一次 tab 會幫你自動補完資料夾名稱
* mkdir（make directory）
    * 新建資料夾
* rm （remove）
    * 刪除檔案，這邊的刪除檔案是「直接刪除」，並不會進到垃圾桶中，因此使用時要小心
    * 變化型：
        1. rmdir （remove directory）：刪除空資料夾，若資料夾內有檔案就無法刪除。
        2. rm -rf ：刪除整個檔案或整個資料夾 ＃謹慎使用，刪掉就真掰掰了。
    * 小訣竅
        * 當刪除的檔名帶有空格或特殊字元時可使用單引號將檔名括起來，舉例：rm '要 刪 除 的 檔 名'
* mv（move）
    * 移動檔案
        * 寫法：mv 檔名 路徑 ＃要注意相對路徑跟絕對路徑的差異
    * 改檔名
        * 寫法：mv 原檔名 新檔名
* touch
    * 碰一下檔案
    * 假設檔案不存在，就會建立一個新的檔案。假設檔案存在，更改檔案些改時間。
* cp（copy）
    * 複製檔案
    * 變化型
        cp -r
        寫法：cp -r 原資料夾名稱 新資料名稱
        舉例：cp -r folder folder_copy
* whoami（Who am I）
    * 是作業系統中用於檢視目前有效用戶名稱的命令
* pwd（print working directory）
    * 顯示目前路徑

* clear
    * 清空 Terminal 面板
* exit
    * 關閉 Terminal

### 其他
* date
    * 印出現在時間
* top（table of processes）
    * 印出所有 processes 。可以顯示即時的系統負載狀態，而它也可以用於指令稿中，輸出各種系統資訊
* htop
    * 查看伺服器硬體使用情形
* df
    * 確認硬體空間
    * df -h (詳細)
* python --version
    * 檢查版本
* nvidia-smi
    * 顯示當前GPU使用情況
* history
    * 列出command歷史
* alias
    * 自訂指令名稱
* man
    * 指令手冊
### 組合技
* ｜ (pipe)
    * 串接指令
    * 把「前面指令的輸出」變成「後面的輸入」
    * EX
    ![](https://i.imgur.com/2to1d33.png)

* > (redirect)
    * 重新導向
    * 此方式檔案原內容會被新增的內容將全部覆蓋掉，若要避免可使用 >>
    * EX
    使用 echo 將內容新增至檔案中 #若無此檔案則會直接新增檔案並增加其內容
    ![](https://i.imgur.com/5DHhcPA.png)

## 進階指令
### 壓縮/解壓縮
* zip
    * 壓縮：zip FileName.zip DirName
    * 解壓：unzip FileName.zip
* unzip
    ![](https://i.imgur.com/PDYXtCA.png)

* tar
    * -c 打包檔案
    * -x 解開壓縮檔
    * -t 檢視壓縮檔的內容
    * -z 使用gzip 壓縮
    * -v 顯示執行過程
    * -P 使用絕對路徑
    * -f 指定壓縮檔的檔案名稱。 此參數的後面要接檔案名稱，因此要注意參數的順序(通常是把f 參數寫在最後一個，或是與其它參數分開使用)
### 查看磁碟
* lsblk
    * 列出有關所有可用或指定的塊設備的信息
    * -a 是默認選項
    ![](https://i.imgur.com/gOJKCoF.png)
    ![](https://i.imgur.com/SyQ1NjT.png)
    * 更多用法
    ![](https://i.imgur.com/cCHtiWY.png)

* df -h
    *  顯示有關檔案系統之總空間以及可用空間的相關資訊
### 監控系統
* ps
    * 察看執行中的程式的一個指令，你可以配合其參數  -aux  來執行
    [root@tsai  root]#  ps  -aux
    *  在輸出的第一列中會出現 『PID』字樣，在那一欄中的咚咚就是每一個程式執行的代碼
* htop
    * 安裝 ： apt-get install htop
    ![](https://i.imgur.com/54CKtPZ.png)
    ![](https://i.imgur.com/BT5NNMd.png)
    * 退出 ： q
* kill
    * 用來殺掉執行中程式的指令，需配合 ps 這個指令
    * 可以 ps  -aux 這個指令查出  ftp  這個程式的代碼（PID），假設其 PID 為 110 ，然後輸入：
     [root@tsai  root]# kill  110
### 輸入/輸出導向，管線操作
https://blog.gtwang.org/linux/linux-io-input-output-redirection-operators/
### 排程任務
* cron
![](https://i.imgur.com/FCNa1rj.png)

### 其他
* bas script

# Linux

## 安裝語言
* cmd
```cmd=
sudo apt-get install fcitx-table-boshiamy #新酷音輸入法(中文)
```
* setting
    * manage installed languages
    * keyboard input method system(fcitx)
    ![](https://i.imgur.com/z4OZOel.png)

* 小鍵盤圖示
    * 點+
    * 取消only show current language
    * 搜尋chewing
    ![](https://i.imgur.com/f2mNiih.png)
    
* log out
## 複製貼上功能
* Ctrl + Shift + C 複製
* Ctrl + Shift + V 貼上
* Ctrl + U 剪下游標前的字元到剪貼簿
* Ctrl + K 剪下游標後的字元到剪貼簿
* Ctrl + Y 貼上

### 亮度控制器
#### 安裝
```bash=
sudo apt-get update
sudo add-apt-repository ppa:apandada1/brightness-controller
sudo apt-get update
sudo apt-get install brightness-controller
```
#### 啟動
```bash=
brightness-controller
```
#### 界面
![](https://i.imgur.com/hOwyYmv.png)

## Default Applications
 改變預設開啟位置
 
## 安裝deb檔
```bash=
sudo dpkg -i code_1.60.2-1632313585_amd64.deb
```
