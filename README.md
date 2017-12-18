# gitea
#### 一、下載安裝並啟動，並且在背影執行
<pre>
docker-compose up -d
</pre>

#### 二、可執行如下命令，確認logs狀態，啟動完成後，再進入第三步
<pre>
docker-compose logs -f
</pre>


#### 三、開啟網頁
<pre>
loclahost:10080

/app/gitea/gitea (gitea程式)

/etc/app.ini (環境設定)

/data  (mysql資料庫)

/repository (git倉庫)
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
