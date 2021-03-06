---
title: 利用 SQL Compact Edition 免費建立擁有 DataBase 的 Azure Websites
date: 2014-09-17 03:15:00
tags: [ASP.NET MVC,Azure]
---

在<strike>只有免費服務才使用</strike>的這個時代，如果只是一個小型網站自然不想月花150使用Azure SQL Server，但自己也沒有Server怎麼辦呢？
<!-- more -->

今天就來教大家利用`SQL Compact Edition`不花一毛錢來建立使用SQL DB的Azure Websites吧！

## 第一步：安裝Nuget套件

為你的專案加入兩個Nuget套件，分別是
  
1. EntityFrame.SqlServerCompact   
2. Microsoft SQL Server Compact Edition  
  
 [![](https://2.bp.blogspot.com/-cr8g6oMLi48/VBiC7cc6auI/AAAAAAAAJNU/3Tpl8VdYwzk/s1600/2014-09-17%2B02_15_56-Greenshot.jpg)](https://2.bp.blogspot.com/-cr8g6oMLi48/VBiC7cc6auI/AAAAAAAAJNU/3Tpl8VdYwzk/s1600/2014-09-17%2B02_15_56-Greenshot.jpg)

## 第二步：加入以下連線字串至Web.Config<connectionStrings></connectionStrings>區段中
```xml
<add name ="DefaultConnection" connectionString ="Data Source=|DataDirectory|CompactDB.sdf" providerName ="System.Data.SqlServerCe.4.0" />
```
其中`Data Source=|DataDirectory|CompactDB.sdf`可得到相對路徑的App_Data\CompactDB.sdf  

[![](https://1.bp.blogspot.com/-csbMF-FZkkY/VBiC7WrFk5I/AAAAAAAAJNM/N_krMRacyow/s1600/2014-09-17%2B02_23_09-Greenshot.jpg)](https://1.bp.blogspot.com/-csbMF-FZkkY/VBiC7WrFk5I/AAAAAAAAJNM/N_krMRacyow/s1600/2014-09-17%2B02_23_09-Greenshot.jpg)

## 第三步：在App_Data中右鍵加入→新增項目→Sql Server 資料庫  
注意：這裡我將檔名改為.sdf檔，因為.sdf 很適合小型專案使用，不需要用到.mdf  

[![](https://4.bp.blogspot.com/-PdLKruVk110/VBiC7TKW0TI/AAAAAAAAJNQ/Uy8oVtWTFKY/s1600/2014-09-17%2B02_25_11-Greenshot.jpg)](https://4.bp.blogspot.com/-PdLKruVk110/VBiC7TKW0TI/AAAAAAAAJNQ/Uy8oVtWTFKY/s1600/2014-09-17%2B02_25_11-Greenshot.jpg)

若你用使用MVC的CodeFirst讓DB檔案自己產生出來，這之後一定要記得將產生的DB檔加入至專案：
點選右上角顯示所有檔案→找到你的CompactDB.sdf→右鍵加入至專案 

[![](https://3.bp.blogspot.com/-VPUidFCACLo/VBiC8MrDexI/AAAAAAAAJNk/Mu8SOe6g4D0/s1600/2014-09-17%2B02_26_04-Greenshot.jpg)](https://3.bp.blogspot.com/-VPUidFCACLo/VBiC8MrDexI/AAAAAAAAJNk/Mu8SOe6g4D0/s1600/2014-09-17%2B02_26_04-Greenshot.jpg)

## 第四步：到你的Azure建立WebSites

左下新增→接著如圖選擇建立網站  

[![](https://1.bp.blogspot.com/-PCQxb6lyHZQ/VBiIyyO_qpI/AAAAAAAAJN4/cZZP-FtUahA/s1600/2014-09-17%2B02_51_13-Greenshot.jpg)](https://1.bp.blogspot.com/-PCQxb6lyHZQ/VBiIyyO_qpI/AAAAAAAAJN4/cZZP-FtUahA/s1600/2014-09-17%2B02_51_13-Greenshot.jpg)

## 第五步：儲存連線字串至Azure websites

建好網站後，點選你的網站，點選上方設定，拉到下面，填入剛剛的連接字串，選擇"自訂"，按下方儲存。  

[![](https://4.bp.blogspot.com/-4pcMGsaswSc/VBiIy7ttAUI/AAAAAAAAJN0/05jkhA66dPE/s1600/2014-09-17%2B02_53_53-Greenshot.jpg)](https://4.bp.blogspot.com/-4pcMGsaswSc/VBiIy7ttAUI/AAAAAAAAJN0/05jkhA66dPE/s1600/2014-09-17%2B02_53_53-Greenshot.jpg)

## 第六步：下載發行設定檔

到儀表板，點選下載發行設定檔，將其儲存在電腦中

[![](https://3.bp.blogspot.com/-8IdBGmmLFck/VBiIy9wsA-I/AAAAAAAAJN8/zsJHWX112LI/s1600/2014-09-17%2B02_55_48-Greenshot.jpg)](https://3.bp.blogspot.com/-8IdBGmmLFck/VBiIy9wsA-I/AAAAAAAAJN8/zsJHWX112LI/s1600/2014-09-17%2B02_55_48-Greenshot.jpg)

## 第七步：發行

對你的專案按右鍵→發行→匯入→選到剛剛的設定檔→確定→發行

[![](https://2.bp.blogspot.com/-eZbZi08Ibv8/VBiIz6WwzxI/AAAAAAAAJOM/H-cYk1uFFlE/s1600/2014-09-17%2B02_57_08-Greenshot.jpg)](https://2.bp.blogspot.com/-eZbZi08Ibv8/VBiIz6WwzxI/AAAAAAAAJOM/H-cYk1uFFlE/s1600/2014-09-17%2B02_57_08-Greenshot.jpg)

### 發行成功！[完成網址參考](http://websitewithdbforfree.azurewebsites.net/)

[![](https://4.bp.blogspot.com/-PRmNlwla-UA/VBiLkiYWj8I/AAAAAAAAJOY/ROfIeHFUTww/s1600/2014-09-17%2B03_10_20-Greenshot.jpg)](https://4.bp.blogspot.com/-PRmNlwla-UA/VBiLkiYWj8I/AAAAAAAAJOY/ROfIeHFUTww/s1600/2014-09-17%2B03_10_20-Greenshot.jpg)

希望有幫助到大家<strike>的錢包</strike>！