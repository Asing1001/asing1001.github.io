---
title: Sublime Text 3 安裝常見問題(Package Control手動安裝、No packages available for installation、安裝Emmet出現錯誤)
date: 2014-10-15 01:44:00
tags: [開發工具]
---

[Sublime Text 3](http://www.sublimetext.com/3) 是開發前端極好用的IDE，保哥[這篇](http://blog.miniasp.com/post/2014/01/07/Useful-tool-Sublime-Text-3-Quick-Start.aspx)中介紹的很詳細，但安裝時由於Proxy的關係會遇到一些問題，在此分享問題解決方式。
<!-- more -->

### 一、安裝Package Control
按`View => show console`，於最下方`Console`裡貼上[Package Control網址](https://packagecontrol.io/installation)中的代碼按Enter即完成。

### 二、有Proxy因此需手動安裝[Package Control](https://sublime.wbond.net/installation)：

1.  點選 Preferences > Browse Packages… 
2.  回上一層點選 Installed Packages/ 資料夾
3.  下載 [Package Control.sublime-package](https://sublime.wbond.net/Package%20Control.sublime-package) 將其複製到 2\. 的資料夾中

安裝完後重新啟動可在Preference中看到多了Package Control即完成安裝，點下去如下圖：  

[![](http://3.bp.blogspot.com/-pv34B1MiHu8/VD1aQ2iM2pI/AAAAAAAAJSw/-1a94uNCJ9c/s1600/2014-10-15%2B01_15_03-Greenshot.jpg)](http://3.bp.blogspot.com/-pv34B1MiHu8/VD1aQ2iM2pI/AAAAAAAAJSw/-1a94uNCJ9c/s1600/2014-10-15%2B01_15_03-Greenshot.jpg)

### 三、因為Proxy使得按Install Package出現錯誤訊息(“No packages available for installation”)或沒反應

在此提供兩種解決方式：

#### 解決方法一、

1.  選擇 Preferences -> Package Settings -> package control -> settings - user 
2.  在文件中按如下格式添加Proxy設定，如：
```
"http_proxy": "http://proxy.domain.com:8080",  
"https_proxy": "http://proxy.domain.com:8080",
```
#### 解決方法二、
1.  打開IE 
2.  工具 →網際網路選項→ 進階標籤→ Security → Check for Server Certificate revocation 這個選項取消掉！
3.  重新啟動ST3

### 四、安裝Emmet出現錯誤訊息"Error while loading pyV8 binary............"
[![](http://2.bp.blogspot.com/-lKgBQt4eK7s/VD1fALHbLiI/AAAAAAAAJS8/GHRWQ8GQffs/s1600/7MmZZ.png)](http://2.bp.blogspot.com/-lKgBQt4eK7s/VD1fALHbLiI/AAAAAAAAJS8/GHRWQ8GQffs/s1600/7MmZZ.png)

解決方法：
1.  請至[https://github.com/emmetio/pyv8-binaries](https://github.com/emmetio/pyv8-binaries)拉到最下面下載正確版本的檔案
2.  解壓縮整個資料夾到 C:\Users\"你的username"\AppData\Roaming\Sublime Text 3\Installed Packages\PyV8
3.  請手動建立Installed Packages之下的PyV8資料夾！
4.  重新啟動後即解決

整理以上問題希望能幫助到大家！

