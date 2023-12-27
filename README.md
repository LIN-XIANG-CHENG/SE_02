# 個人資訊管理系統 （個人日記模組） 軟體工程課程設計實驗報告
# 第一章 個人信息管理系統可行性研究
  1.1 問題描述
  
  設計個人信息管理系統，提高個人信息的效率，保證信息的準確規範，使個人管理工作真正做到科學、合理的規劃，系統高效的實施。
  
  1.2 開發背景
  
  開發軟件的名稱：個人信息管理系統
  
  項目的任務提出者：長治學院計算機系的0801班
  
  開發者：技科0801班第十組

  1.3 意義

  通過對此系統的設計，更方便於的對個人信息進行管理。

  1.4 開發環境

  Windows XP 和 Power Builder 9.0 以及 Microsoft SQL Server 2000 數據庫

  1.5 應用範圍

  本系統應用於廣大群體對個人信息進行管理，適用於各種人群使用
  
# 第二章 個人信息管理系統需求分析

  2.1 問題現況

  目前要解決的問題是設計出個人信息管理系統的需求分析，對各個模塊進行詳細的分析。

  2.2 用戶對系統的功能需求

  2.2.1 性能需求

  (1)系統易操作性，所開發的系統應做到操作簡單，盡量使系統操作不受用戶對電腦知識水平的限制。

  (2)系統具有可維護性。由於系統涉及的信息比較廣，數據庫中的數據需定期修改，系統可利用的空間及性能也隨之下降，
為了使性能更好的運轉，學院可以對系統數據及一些簡單的功能進行獨立的維護及調整。

  (3)系統具有開放性。該系統能夠在開放的硬件體系結構中運行，並且能與其他系統順利連接，不會因外部系統的不同而要做在量的修改

  2.2.2 接口需求

  運行本系統的硬件和軟件基本要求如下：

  CPU：Intel P3及以上

  內存：256 MB及以上

  硬碟：10 GB及以上

  Net框架：Mircosoft .Net Flamework V1.1版本及以上

  數據庫服務器：Mircosoft SQL Server 2000 及以上

  2.3 系統的數據流圖

  圖 系統的數據流圖

  2.4 系統的數據字典

  圖 通訊錄、備忘錄、個人日記和個人財務的數據字典

  2.5 系統的E-R圖

  圖 系統的E-R圖

  2.6 個人日記模塊的E-R圖

  圖 個人日記模塊的E-R圖

# 第三章 個人信息系統概要設計

  3.1 系統的模塊劃分

  個人信息管理系統包括四個模塊，分別為通訊錄模塊、備忘錄模塊、個人日記模塊和個人財務模塊。

  根據系統中所包含的內容，該系統可以分為兩個子系統，分別為查詢系統和管理子系統。查詢又分別為通訊錄的查詢、備忘錄的查詢、個人日記的查詢和個人財物的查詢。管理子系統又包刮通訊錄、備忘錄、個人日記的和個人財物的錄入、刪除和顯示。

  圖 個人日記模塊結構圖

  3.2 系統功能模塊設計圖

  詳細的功能模塊設計圖如圖所示：

  圖 詳細介紹功能模塊

# 第四章 個人信息管理系統詳細設計

  4-1 數據庫設計

  根據設計要求設計出各個表結構

  表 各個表結構如下所示

  用戶表：

  通訊錄表：

  備忘錄表：

  日記表：

  個人財務表：

  4.2 個人日記交互介面

  系統登錄介面以及個人日記的管理介面如下圖所示：

  圖 系統的登入介面

  圖 個人日記交互介面

  4.3 個人日記模塊的關係模式

  用戶(用戶帳號，用戶姓名，密碼)

  用戶帳號->用戶姓名，用戶帳號->密碼。第四范式

  日記(用戶帳號，時間，地點，人物，事情)

  時間->地點，時間->人物。時間->事情。第四范式

# 第五章 個人日記模塊主要源代碼

  5.1 登入介面的源代碼

  登入介面主函數：

    SetPointer(hourglass!)

    IF PARENT.load_connet(sle_1.text,sle_2.text)=-1 THEN

      MessageBox("連接數據庫錯誤"，"連接失敗"+sqlca.sqlerrtext)

      HALT

    ELSE

      messagebox("恭喜!"，"密碼正確，已批准登錄系統!")

    close(parent)

      Open(w_cxselect)

    END IF

  5.2 管理個人日記模塊的源代碼

  5.2.1 查詢模塊的源代碼：

    string 用戶帳號

    用戶帳號 = trim(sle_1.text)

      if 用戶帳號 = "" then

        messagebox("沒有輸入用戶帳號"，"請輸入正確的查詢條件!")

        else

        dw_1.Retrieve(用戶帳號)

          else if

          sle_1.setFocus()

  
  5.2.2 管理個人日記源代碼

    管理功能主函數： 
    
    添加(錄入)主函數：Long row

                    row = dw_1.InserRow(0)

                    dw_1.SetRow = (row)

                    dw_1.ScrollToRow = (row)

                    dw_1.SetFocus = (row)

    插入主函數：     Long row

                    row = dw_1.InserRow(dw_1.GetRow())

                    dw_1.SetRow = (row)

                    dw_1.ScrollToRow = (row)

                    dw_1.SetFocus = (row)

    顯示主函數：     dw_1.Retrieve = ()

    更新主函數：     dw_1.UpDate = ()

                    dw_1.ReSet = ()

    刪除主函數：     dw_1.DeleteRow(dw_1.GetRow())

# 第六章 個人日記模塊測試

  6.1 測試概念

  本模塊的測試內容如下表：  要求各個測試內容必須按照嚴格的字符類型，輸入其他格式將報錯： 字符長度按照下表給出的嚴格測試，超出範圍報錯：
 用戶


