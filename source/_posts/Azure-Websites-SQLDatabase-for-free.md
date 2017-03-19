---
title: 利用 SQL Compact Edition 免費建立擁有 DataBase 的 Azure Websites [ Azure Websites + Database for free ]
date: 2014-09-17 03:15:00
tags: [ASP.NET MVC,Azure]
---

在<strike>只有免費服務才使用</strike>的這個世代，如果只是一個Demo用的小型網站自然不想使用到雲端的SQL DB來做為DataBase (其實只是不想花一個月150左右的DB費用XD)  

鑑於想要使用免費Azure Websites，但又想要連接資料庫的人要怎麼做呢？  
只能每個月砸150台幣買DB了嗎！？  

<span style="font-size: large;">答案當然是<span style="color: red;">NO！</span></span>  
<span style="font-size: large;"><span style="color: red;"></span></span>  
<a name="more"></a>  
<span style="font-size: large;"><span style="color: red;">  
</span></span>今天就來教大家利用SQL Compact Edition不花一毛錢使用擁有 DataBase 的 Azure Websites 吧！  

以下看圖說故事開始：  

###   
**第一步：安裝Nuget套件**

<span style="font-weight: normal;">為你的專案加入兩個Nuget套件，</span><span style="font-weight: normal;">分別是</span>  
<span style="font-weight: normal;">  
</span><span style="font-weight: normal;">1\. EntityFrame.SqlServerCompact </span>  
<span style="font-weight: normal;">2\. Microsoft SQL Server Compact Edition</span>  
<span style="font-weight: normal;">  
</span>  

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;">

<tbody>

<tr>

<td style="text-align: center;">[![](http://2.bp.blogspot.com/-cr8g6oMLi48/VBiC7cc6auI/AAAAAAAAJNU/3Tpl8VdYwzk/s1600/2014-09-17%2B02_15_56-Greenshot.jpg)](http://2.bp.blogspot.com/-cr8g6oMLi48/VBiC7cc6auI/AAAAAAAAJNU/3Tpl8VdYwzk/s1600/2014-09-17%2B02_15_56-Greenshot.jpg)</td>

</tr>

</tbody>

</table>

### ** 第二步：**加入以下連線字串至Web.Config<span style="color: blue; font-family: Arial; font-size: 16px;"> </span><span style="color: blue; font-family: Arial; font-size: 16px;"> <</span><span style="color: #a31515; font-family: Arial; font-size: 16px;">connectionStrings</span><span style="color: blue; font-family: Arial; font-size: 16px;">> </span><span style="color: blue; font-family: Arial; font-size: 16px;"></</span><span style="color: #a31515; font-family: Arial; font-size: 16px;">connectionStrings</span><span style="color: blue; font-family: Arial; font-size: 16px;">>區段中</span>

<span style="color: blue; font-family: Arial; font-size: 16px;">  
</span><span style="color: blue; font-family: Arial; font-size: 16px;"><</span><span style="color: #a31515; font-family: Arial; font-size: 16px;">add</span><span style="color: blue; font-family: Arial; font-size: 16px;"> </span><span style="color: red; font-family: Arial; font-size: 16px;">name</span><span style="color: blue; font-family: Arial; font-size: 16px;"> =</span><span style="background-color: white; font-family: Arial; font-size: 16px;">"</span><span style="color: blue; font-family: Arial; font-size: 16px;">DefaultConnection</span><span style="background-color: white; font-family: Arial; font-size: 16px;">"</span><span style="color: blue; font-family: Arial; font-size: 16px;"> </span><span style="color: red; font-family: Arial; font-size: 16px;">connectionString</span><span style="color: blue; font-family: Arial; font-size: 16px;"> =</span><span style="background-color: white; font-family: Arial; font-size: 16px;">"</span><span style="color: blue; font-family: Arial; font-size: 16px;">Data Source=|DataDirectory|CompactDB.sdf</span><span style="background-color: white; font-family: Arial; font-size: 16px;">"</span><span style="color: blue; font-family: Arial; font-size: 16px;"> </span><span style="color: red; font-family: Arial; font-size: 16px;">providerName</span><span style="color: blue; font-family: Arial; font-size: 16px;"> =</span><span style="background-color: white; font-family: Arial; font-size: 16px;">"</span><span style="color: blue; font-family: Arial; font-size: 16px;">System.Data.SqlServerCe.4.0</span><span style="background-color: white; font-family: Arial; font-size: 16px;">"</span><span style="color: blue; font-family: Arial; font-size: 16px;"> /></span>  
<span style="color: blue; font-family: Arial; font-size: 16px;">  
</span><span style="color: blue; font-family: Arial; font-size: 16px;">其中</span>  
<span style="color: blue; font-family: Arial; font-size: 16px;">Data Source=|DataDirectory|CompactDB.sdf 可得到相對路徑的</span><span style="color: red; font-family: Arial; font-size: 16px;">App_Data</span><span style="background-color: white; font-family: Arial; font-size: 16px;">\</span><span style="color: red; font-family: Arial; font-size: 16px;">CompactDB.sdf</span>  

<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-csbMF-FZkkY/VBiC7WrFk5I/AAAAAAAAJNM/N_krMRacyow/s1600/2014-09-17%2B02_23_09-Greenshot.jpg)](http://1.bp.blogspot.com/-csbMF-FZkkY/VBiC7WrFk5I/AAAAAAAAJNM/N_krMRacyow/s1600/2014-09-17%2B02_23_09-Greenshot.jpg)</div>

### **第三步：在App_Data中右鍵加入→新增項目→Sql Server 資料庫**

<span style="color: red;">注意：這裡我將檔名改為.sdf檔，因為.sdf 很適合小型專案使用，不需要用到.mdf</span>  

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-PdLKruVk110/VBiC7TKW0TI/AAAAAAAAJNQ/Uy8oVtWTFKY/s1600/2014-09-17%2B02_25_11-Greenshot.jpg)](http://4.bp.blogspot.com/-PdLKruVk110/VBiC7TKW0TI/AAAAAAAAJNQ/Uy8oVtWTFKY/s1600/2014-09-17%2B02_25_11-Greenshot.jpg)</div>

若你用的和我一樣是MVC的CodeFirst則是改掉你的連線字串後，讓DB自己產生出來，但是這之後有一個很重要的步驟！真的很重要！我卡在這邊很久！操作如下：  

<span style="color: red;">產生DB後→點選右上角顯示所有檔案→找到你的CompactDB.sdf→右鍵加入至專案</span>  

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-VPUidFCACLo/VBiC8MrDexI/AAAAAAAAJNk/Mu8SOe6g4D0/s1600/2014-09-17%2B02_26_04-Greenshot.jpg)](http://3.bp.blogspot.com/-VPUidFCACLo/VBiC8MrDexI/AAAAAAAAJNk/Mu8SOe6g4D0/s1600/2014-09-17%2B02_26_04-Greenshot.jpg)</div>

### **第四步：**到你的Azure建立WebSites

左下新增→接著如圖選擇建立網站  

<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-PCQxb6lyHZQ/VBiIyyO_qpI/AAAAAAAAJN4/cZZP-FtUahA/s1600/2014-09-17%2B02_51_13-Greenshot.jpg)](http://1.bp.blogspot.com/-PCQxb6lyHZQ/VBiIyyO_qpI/AAAAAAAAJN4/cZZP-FtUahA/s1600/2014-09-17%2B02_51_13-Greenshot.jpg)</div>

### **第五步：**

建好網站後，點選你的網站，點選上方設定，拉到下面，填入剛剛的連接字串，選擇"自訂"，按下方儲存。  

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-4pcMGsaswSc/VBiIy7ttAUI/AAAAAAAAJN0/05jkhA66dPE/s1600/2014-09-17%2B02_53_53-Greenshot.jpg)](http://4.bp.blogspot.com/-4pcMGsaswSc/VBiIy7ttAUI/AAAAAAAAJN0/05jkhA66dPE/s1600/2014-09-17%2B02_53_53-Greenshot.jpg)</div>

### 第六步：

<div>到儀表板，點選下載發行設定檔，將其儲存在電腦中</div>

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-8IdBGmmLFck/VBiIy9wsA-I/AAAAAAAAJN8/zsJHWX112LI/s1600/2014-09-17%2B02_55_48-Greenshot.jpg)](http://3.bp.blogspot.com/-8IdBGmmLFck/VBiIy9wsA-I/AAAAAAAAJN8/zsJHWX112LI/s1600/2014-09-17%2B02_55_48-Greenshot.jpg)</div>

### 第七步：

<div>對你的專案按右鍵→發行→匯入→選到剛剛的設定檔→確定→發行</div>

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-eZbZi08Ibv8/VBiIz6WwzxI/AAAAAAAAJOM/H-cYk1uFFlE/s1600/2014-09-17%2B02_57_08-Greenshot.jpg)](http://2.bp.blogspot.com/-eZbZi08Ibv8/VBiIz6WwzxI/AAAAAAAAJOM/H-cYk1uFFlE/s1600/2014-09-17%2B02_57_08-Greenshot.jpg)</div>

### 然後就發行成功囉！[完成網址參考](http://websitewithdbforfree.azurewebsites.net/)

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-PRmNlwla-UA/VBiLkiYWj8I/AAAAAAAAJOY/ROfIeHFUTww/s1600/2014-09-17%2B03_10_20-Greenshot.jpg)](http://4.bp.blogspot.com/-PRmNlwla-UA/VBiLkiYWj8I/AAAAAAAAJOY/ROfIeHFUTww/s1600/2014-09-17%2B03_10_20-Greenshot.jpg)</div>

<div>**<span style="color: blue;">希望有幫助到大家<strike>的錢包</strike>！XD</span>**</div>