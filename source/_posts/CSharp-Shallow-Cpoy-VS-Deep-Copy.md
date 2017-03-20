---
title: C# Shallow Cpoy VS Deep Copy
date: 2014-11-14 11:44:00
tags: [C#]
---

## 淺層拷貝於深層拷貝差別 

有時需要拷貝物件時到底該怎樣視自己需要來做拷貝?  
差別在於拷貝的class內部的參考物件是否只<span style="color: blue;">拷貝參考指標</span>  
或是拷貝完整獨立物件(<span style="color: blue;">連參考物件一起拷貝</span>)  
補充：  

*   序列化(<span style="color: blue;">Serialize</span>)的意義是把物件變成類似binary的資料,通常用來做資料傳輸,例如網路的資料傳輸
*   反序列化(<span style="color: blue;">DeSerialize</span>)表示把類似binary的資料還原回物件狀態

```Csharp
using System;  
using System.Collections.Generic;  
using System.IO;   
using System.Linq;  
using System.Runtime.Serialization;  
using System.Runtime.Serialization.Formatters.Binary;  
using System.Text;   
using System.Threading.Tasks;  

namespace ShallowCopy_VS_DeepCopy  
{  
     [Serializable]//標記表示可序列化   
     public class A : Object  
     {  
         private int  _IntProperty;  
         public int  IntProperty  
         {  
             get  
             {  
                     return this._IntProperty;  
             }  

             set   
             {   
                     this._IntProperty = value;  
             }  
         }  

     private  bool   _BoolProperty;  
     public  bool   BoolProperty  
     {  

         get   
         {  
                 return  this._BoolProperty;  
         }  

         set  
         {  
                this._BoolProperty = value;  
         }  

     }  

     private  B  _ReferenceProperty;//參考物件欄位  
     public  B  ReferenceProperty  
     {  
         get  
         {  
                 return  this._ReferenceProperty;  
         }  
         set   
         {  
                 this._ReferenceProperty = value;  
         }  
      }  

      //Constructor  

     public  A(int  intvalue, bool  boolvalue, decimal  decimalvalue, short shortvalue)  
     {  

         _IntProperty = intvalue;   

         _BoolProperty = boolvalue;  

         _ReferenceProperty = new B (decimalvalue, shortvalue);  

     }  

     /// 重點在這使用BinaryFormetter的序列化方法通過資料流轉換此物件並還原物件///  

     public A DeepCopy()  
     {   
         //此為把物件序列化後拷貝至資料流並且在還原序列化回物件狀態   

         //所以拷貝的物件包含其參考物件也一併序列化   

         //所以參考物件內的資料也一併拷貝,故為獨立物件非參考指標   

         MemoryStream ms = new MemoryStream();   

         BinaryFormatter bf = new BinaryFormatter();//重點在這  

         bf.Serialize(ms, this);//序列化this物件   

         ms.Position = 0;   

         return  (A)bf.Deserialize(ms); //還原序列化  

     }   

     public Object Clone()   
     {   

           using (MemoryStream ms = new MemoryStream())  
           {  

                //同上意思   

                IFormatter format = new BinaryFormatter();   

                format.Serialize(ms, this);   

                ms.Position = 0;   

                return format.Deserialize(ms);   

            }   
     }  

     public A ShallowCopy()   
     {   

           //這是原生的淺層拷貝,拷貝的物件內的參考物件只有拷貝指標,   

           //所以參考物件改變則此拷貝的物件內容也跟者改變   

           return (A)this.MemberwiseClone();  

      }   
   }   

   [Serializable]   

   public class B : object   
   {   

        private decimal  _DecimalProperty;   

        public decimal  DecimalProperty;  
        {   

            get   
            {   

                   return  _DecimalProperty;   

            }   

            set  
            {   

                   _DecimalProperty = value;  

            }   

        }   

        private short  _ShortProperty;   

        //Constructor  

        public B(decimal  decimalvalue, short  shortvalue)   
        {  

             _DecimalProperty = decimalvalue;  

             _ShortProperty = shortvalue;   

        }   

        public short ShortProperty   
        {   

              get   
              {   

                       return  _ShortProperty;   

              }  

              set   
              {   

                       _ShortProperty = value;  

              }  

         }  

     }   

}  
```