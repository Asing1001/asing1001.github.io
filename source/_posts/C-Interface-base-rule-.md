title: |
	C# Interface base rule 介面潛規則
date: 2014-11-07 10:31:00
tags: [C#]
---

<div>Interface是C#裡相當重要的概念，它可以完成多型，讓我們方便維護，本篇整理寫介面時的基本規則，如下：</div>

1.  Interface 會要求繼承的類別(class)必須實作interface裡面定義的方法,建議使用 <span style="color: #0b5394;">I</span> 開頭定義<a name="more"></a>
2.  Interface介面是不存放資料的,因此不能增加欄位(field),但可以增加特性(property),理由是set和get存取器只是方法 
3.  Interface內的東西都是公用(public)的  
    X=> Iobj i1 = new Iobj();  
    O=> Iobj[] i1 = new Iobj[3];  
4.  無法實例化一個介面(interface),但可以建立介面陣列(interface[])參考 
5.  Interface refference like Object refference,  
    介面參考就像物件參考一樣會讓物件持續存活  
    Iojb i1 = new obj();//但介面參考只能使用介面內所宣告的方法與屬性,  
    obj i1 = new obj();//物件可使用屬於自己與繼承interface的方法與屬性 
6.  可以用 is (關鍵字)來確定介面或其他型別,  
    ex:(obj1 is Iobj)=>true or false//表示obj是否為介面Iobj的實作 
7.  可以用 as (關鍵字)來轉型成為其他介面或型別,  
    ex:if(obj1 is Iobj)Iobj obj2 = obj1 as Iobj;  
    //前面為檢查介面是否型別可轉,確定後就使用as關繼字轉型,  
    若轉型失敗則傳回null,成功就可以使用Iobj的方法與特性
8.  在介面(interface)中放置特性(property),在實作介面後可以自行改寫,  
    只要有實作原介面設定的存或取(get or set),  
    ex: 原來public job{get;}=>實作後public job{get;private set;//自己加set並設為私有的} 
9.  介面繼承介面只會累積所繼承的方法與特性,除了實作自己的特性與方法還要實作繼承來的特性與方法 
10.  任何類別均可實作任何介面,只要他信守實作該介面所有的方法與特性的承諾 
11.  Interface可以向上轉型也可向下轉型,使用is來判別後再使用as來轉型,但是向上轉型後就只能使用父類別的方法與特性 
12.  傳入方法的Pattern只要是同型態的變數(同樣介面或物件)皆可傳入,  
    ex:  
    MonitorPower(Appliance appliance) CoffeeMaker misterCoffee = new CoffeeMaker();//CoffeeMaker為Appliance的子類別所以一定有繼承Appliance的屬性與方法 MonitorPower(misterCoffee);//所以可以帶入參數