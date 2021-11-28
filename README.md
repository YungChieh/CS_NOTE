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



