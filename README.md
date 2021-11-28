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
$ nano test.txt          #開啟test檔案

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
  :w[filename]  #將編輯的資料儲存成另一個新檔案（類似另存新檔）
  :r[filename]  #在編輯的資料中，讀入另一個檔案的資料
