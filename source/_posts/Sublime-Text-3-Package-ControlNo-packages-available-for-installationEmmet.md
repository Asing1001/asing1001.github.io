---
title: Sublime Text 3 安裝常見問題(Package Control手動安裝、"No packages available for installation"、安裝Emmet出現錯誤)
date: 2014-10-15 01:44:00
tags: [開發工具]
---

[Sublime Text 3](http://www.sublimetext.com/3) 是身為前端工程師必安裝的工具，在保哥[Sublime Text 3 新手上路：必要的安裝、設定與基本使用教學](http://blog.miniasp.com/post/2014/01/07/Useful-tool-Sublime-Text-3-Quick-Start.aspx) 這篇中都介紹的很詳細，但是在公司安裝時，由於使用Proxy的關係常常會遇到一些問題，以下整理安裝方法及問題解決方式：  

※請先至 [Sublime Text 3](http://www.sublimetext.com/3) 網頁選擇適合自己的版本下載安裝  

安裝完後首先要做的是安裝最重要的[Package Control](https://sublime.wbond.net/installation)！  
一般安裝方式為：  
打開View→show console，在最下方的Console裡面貼上網址中的代碼如下，再按Enter等待執行完即完成安裝程序。  
```
import urllib.request,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

### 常見問題(一)、在公司裡有Proxy因此需手動安裝[Package Control](https://sublime.wbond.net/installation)：

1.  點選 Preferences > Browse Packages… 
2.  回上一層點選 Installed Packages/ 資料夾
3.  下載 [Package Control.sublime-package](https://sublime.wbond.net/Package%20Control.sublime-package) 將其複製到 2\. 的資料夾中

安裝完後重新啟動可在Preference中看到多了Package Control即完成安裝，點下去如下圖：  

[![](http://3.bp.blogspot.com/-pv34B1MiHu8/VD1aQ2iM2pI/AAAAAAAAJSw/-1a94uNCJ9c/s1600/2014-10-15%2B01_15_03-Greenshot.jpg)](http://3.bp.blogspot.com/-pv34B1MiHu8/VD1aQ2iM2pI/AAAAAAAAJSw/-1a94uNCJ9c/s1600/2014-10-15%2B01_15_03-Greenshot.jpg)

### 常見問題(二)、因為使用Proxy使得按Install Package後出現錯誤訊息(“No packages available for installation”)或沒反應

在此提供兩種解決方式：

解決方法一、

1.  選擇 Preferences -> Package Settings -> package control -> settings - user 
2.  在文件中按如下格式添加Proxy設定，如：
```
"http_proxy": "http://proxy.domain.com:8080",  
"https_proxy": "http://proxy.domain.com:8080",
```
解決方法二、
1.  打開IE 
2.  工具 →網際網路選項→ 進階標籤→ Security → Check for Server Certificate revocation 這個選項取消掉！
3.  重新啟動ST3

### 常見問題(三)、安裝Emmet出現錯誤訊息"Error while loading pyV8 binary............"
[![](http://2.bp.blogspot.com/-lKgBQt4eK7s/VD1fALHbLiI/AAAAAAAAJS8/GHRWQ8GQffs/s1600/7MmZZ.png)](http://2.bp.blogspot.com/-lKgBQt4eK7s/VD1fALHbLiI/AAAAAAAAJS8/GHRWQ8GQffs/s1600/7MmZZ.png)

解決方法：
1.  請至[https://github.com/emmetio/pyv8-binaries](https://github.com/emmetio/pyv8-binaries)拉到最下面下載正確版本的檔案
2.  解壓縮整個資料夾到 C:\Users\"你的username"\AppData\Roaming\Sublime Text 3\Installed Packages\PyV8
3.  請手動建立Installed Packages之下的PyV8資料夾！
4.  重新啟動後即解決

整理以上問題希望能幫助到大家！

