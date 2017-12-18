# 私有的git服務gogs

這個repo提供了一個簡易的方式快速啟動gogs服務，並且規劃好了需要掛載的目錄及資料庫設定。

資料庫及gogs完全使用官方的image樣版來產container，您可檢示docker-compose.yml設定檔。

開箱即用(ootb)。

## 目錄結構
<pre>
/app/gitea/gitea (gitea程式)

/etc/app.ini (環境設定)

/data  (mysql資料庫)

/repository (git倉庫)
</pre>

## 關於Linux環境

container執行的使用者uid為1000，如果不是請自行調整了，這裡不多做介紹。

## 安裝於啟動
#### 一、下載安裝並啟動，並且在背影執行
<pre>
docker-compose up -d
</pre>

在Synlogy Nas您可能需要手動建立data的資料夾後，再執行一次docker-compose up -d，
在我的MacOs不需要，可正常產生。

#### 二、可執行如下命令，確認logs狀態，啟動完成後，再進入第三步
<pre>
docker-compose logs -f
</pre>


#### 三、開啟網頁

註冊第一個使用者即是管理者
<pre>
loclahost:10080
</pre>




#### 關於設定

請查看官方的說明，提醒一下，如果您有big5編碼的檔案，可透過ANSI_CHARSET = big5的設定，
就可讓他正常顯示了，不過big5的檔，請勿線上編輯，檔案編碼會被自動轉utf8，就跟github一樣。


https://gogs.io/docs/advanced/configuration_cheat_sheet

#### 注意事項:

如果您並非在自己的本機執行，請確定您的/etc/app.ini中的設定是正確的，目前預設為localhost。

我的DB contianer預設root無密碼，需要碼，請於第一次啟動時可在docker-compose.yml檔設定。

或是啟動後要設定mysql root密碼，可進入db的container內的mysql指令進行設定。
<pre>
docker-compose exec db mysql
</pre>



如果要自行編譯image，到至
https://github.com/go-gitea/gitea
