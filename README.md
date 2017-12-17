# gitea
#### 一、下載安裝並啟動
<pre>
docker-compose up -d
</pre>

#### 二、可執行，確認執行完成，再進入第三步
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

#### 注意事項:

我的DB contianer預設root無密碼，需必碼，請於第一次啟動時可在docker-compose.yml檔設定。

或是啟動後要設定mysql root密碼，可進入db的container內的mysql指令進行設定。
<pre>
docker-compose exec db mysql
</pre>



如果要自行編譯image，到至
https://github.com/go-gitea/gitea
