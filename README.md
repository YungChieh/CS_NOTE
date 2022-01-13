# CS_NOTE
$ cd D:/OneDrive/桌面    #將目錄變換至桌面
$ pwd                    #顯示目前的目錄
$ mkdir temp             #建立一個新目錄temp
$ ls                     #顯示目錄下的所有內容
$ cat GPA.py             #查看檔案(GPA.py)內容
$ cd temp                #將目錄變換至temp

#nano編輯器
$ nano                   #利用nano編輯器開啟一個新檔案
  #Ctrl + O : 存檔
  #Ctrl + X : 跳出 Nano
  #Ctrl + C : 取消目前操作
$ nano test.txt          #利用nano編輯器開啟test.txt檔案

#vim編輯器
$ vim                    #利用vim編輯器開啟一個新檔案
  #I 鍵進入編輯模式
  #ESC 鍵退出編輯模式
  :q  #離開vim
  :q! #強制離開vim，不儲存檔案
  :w test2.txt   #將編輯的資料寫入test2.txt檔案中
  :w! test2.txt  #強制將編輯的資料寫入test2.txt檔案中
  :wq  #儲存檔案，離開vim
  :wq! #強制儲存檔案，離開vim
  :w[filename]   #將編輯的資料儲存成另一個新檔案（類似另存新檔）
  :r[filename]   #在編輯的資料中，讀入另一個檔案的資料
 $ vim test2.txt         #利用vim編輯器開啟test2.txt檔案

#Linux更改使用者權限
$ ls -al                 #查看每個檔案與目錄的擁有者與群組
$ chown                  #可修改檔案或目錄擁有者及群組
$ chmod [-cfvR] [--help] [--version] mode file…  # chmod可控制檔案如何被他人調用
                                     # mode許可權設定字串 [ugoa...][[+-=][rwxX]...][,...]
#身分類別
  # u：檔案擁有者
  # g：與該檔案的擁有者同一個群體者
  # o：其他以外的人
  # a：三者皆是
#許可權設定
  # +：增加許可權
  # -：取消許可權
  # =：唯一設定許可權
#許可權代號
  # r：可讀取(4)
  # w：可寫入(2) 
  # x：可執行(1)
  
$ chmod ugo+r file1.txt   #將檔案 file1.txt 設為所有人皆可讀取
$ chmod ug+w,o-w file1.txt file2.txt  
  #將檔案 file1.txt 與 file2.txt 設為該檔案擁有者，與其所屬同一個群體者可寫入，但其他以外的人則不可寫入 
$ chmod u+x ex1.py        #將 ex1.py 設定為只有該檔案擁有者可以執行 
$ chmod -R a+r *          #將目前目錄下的所有檔案與子目錄皆設為任何人可讀取 
$ chmod a=rwx file == chmod 777 file
$ chmod ug=rwx,o=x file ==  chmod 771 file

#Linux壓縮檔案
#gzip
  $ gzip FileName           #壓縮檔案
  $ gunzip FileName.gz      #解壓縮檔案
  $ gzip -d FileName.gz     #解壓縮檔案
#xz
  $ xz -z FileName          #壓縮
  $ xz -d FileName.xz       #解壓縮
#tar.gz
  $ tar -zcvf FileName.tar.gz DirName  #壓縮
  $ tar -zxvf FileName.tar.gz          #解壓縮

#Linux檔案搜尋
  $ find [path] [option] [action] filename
    #option
      *-size EX：找出大於500M的檔案 → -size +500M
      *-name EX：找出為照片的檔案 → -name "*.jpg"
      *-type EX：-type f → 一般檔案
                 -type d → 一般目錄
      *-user EX：同時找兩個擁有者的檔案 → -user user1 -o -user user2
    #action -exec
      *ls
      *print
    
    #which filename
      *-n<文件名长度>：指定文件名長度，指定的長度必須大於或等於所有文件中最長的文件名。
      *-p<文件名長度>：與-n参數相同，但此處的<文件名長度>包括了文件的路徑。
      *-w：指定輸出欄位的寬度。
      *-V：顯示版本訊息。
  
#Linux檔案內容查閱
  # cat：從第一行顯示檔案內容、形成新檔案
     $ cat -n file1 > file2    #把file1的檔案內容加上行號後輸入file2檔案
        * -n：由1開始對所有輸出的行數編號
        * >：將多個文件覆蓋到目標文件中
        * >>：將多個文件追加到目標文件中
  # tac：從最後一行開始顯示
     $ tac -r -s 'x\|[^x]' test.log    #一個接著一個字符的反轉一個文件
        * -r：將分隔符作為基礎正規表達是處理
        * -s：使用String作為分隔符代替默認的換行符
  # more：一頁一頁的顯示檔案內容
     $ more +20 testfile    #從第20行開始顯示testfile的文檔內容
        * ENTER：向下n行(default為1行)
        * Ctrl+F/SPACE：向下滾動一屏
        * Ctrl+B：返回上一屏
  # less 與 more 類似，顯示檔案室允許用戶既可以向前又可以向後翻頁閱讀檔案
     $ ps -ef |less    #ps查看進程信息並通過less分頁顯示	
        * j：下一行
        * k：上一行
        * G：移動到最後一行
        * g：移動到第一行
  # head/tail：只看頭/尾巴幾行
     $ head -n 20 state.txt | tail -10    #顯示11~20行的內容

#Linux網路相關
  # route
    * add : 新增一條路由規則
    * del : 刪除一條路由規則
    * -net : 目的地址是一個網路
    * -host : 目的地址是一個主機
    * target : 目的網路或主機
    * netmask : 目的地址的網路掩碼
    * gw : 路由資料包通過的閘道器
    * dev : 為路由指定的網路介面
  # ping：常用網路檢測工具，可藉由發送 ICMP ECHO_REQUEST 封包，檢查自己與特定設備之間的網路是否暢通，並同時測  量網路連線的來回通訊延遲時間（round-trip delay time）。
    * -n：參數指定封包數→EX：ping -n 10 blog.gtwang.org
    * -t：持續監看網路是否正常→EX：ping -t blog.gtwang.org
    * -4/-6：IPv4/IPv6
    * -c：指定Ping次數→EX：ping -c 4 blog.gtwang.org
    * -s：指定發送的數據字結數→EX：ping -s 1024 facebook.com
    * -i：指定收發資訊間隔時間→EX：ping -i 0.4 facebook.com
  # 影響網路速度的因素：
    * 延遲（Latency）：封包從來源端至目的端中間所花的時間
    * 頻寬（Bandwidth）：傳輸媒介的最大吞吐量
  # 網路延遲（Latency）的組成元素:
    * propagation delay：封包在網路線上傳輸所花費的時間，與網路線上電子訊號跑的速度有關，這個時間就是距離除以訊號傳送速度所得到的數值。
    * transmission delay：網路卡將資料傳送到網路線上所花的時間，與網路設備的傳送速度有關。
    * nodal processing delay：路由器處理封包表頭、檢查位元資料錯誤與尋找配送路徑等所花費的時間。
    * queuing delay：路由器因為某些因素無法立刻將封包傳送到網路上，造成封包暫存在佇列中等待的時間。
  # netstat
    * 查看端口是否被占用：netstat -a|grep 3306
    * 查看數據包統計信息：netstat -s
    * 查看路由信息：netstat -r
    
##期末考筆記

#awk語法
$ awk '$2 + $3 >= 160 {print 0}' people.txt
$ awk '($2 >6) && ($3 >= 150) {print 0}' people.txt
$ awk 'BEGIN{a="b";print a,a++,a--,++a}' 
$ awk '{if ($3 == 120)print 0}' people.txt

#sed語法
$sed -e 's/a/A/1' apple.txt
$sed -e 's/a/A/g' apple.txt
$sed -n 's/a/A/p' apple.txt
$sed -f apple_command.txt apple.txt
$sed '1a apple apple apple' apple.txt  #在第一行之後新增apple apple apple
$sed '2,3c hahaha' apple.txt  #將2,3行替換成hahaha
$sed 1,5d apple.txt  #將1,5行刪除
$sed 's/.e/E/g' apple.txt
$sed 's/pen/pencil/; s/have/had' apple.txt  #將pen替換成pencil；將have替換成had

#git 語法
$git config --global user.name "YungChieh"
$git config --global user.email "07112039@scu.edu.tw"
$git init
$git add .
$git status
$git commit -m"修改紀錄"
$git log
