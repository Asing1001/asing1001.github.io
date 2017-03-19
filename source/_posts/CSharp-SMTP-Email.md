---
title: C# 使用 SMTP 寄送 Email
date: 2014-11-02 05:01:00
tags: [C#]
---

依據要使用的Mail服務更改smtpAddress、portNumber以及enableSSL三個變數<span style="background-color: white;"></span>  

<pre style="background-attachment: initial; background-clip: initial; background-image: initial; background-origin: initial; background-position: initial; background-repeat: initial; background-size: initial; font-family: Consolas; font-size: 14px !important; line-height: 1.4em;">  

<table class="ArticleTable">

<thead>

<tr>

<td>主機名稱</td>

<td>SMTP Address</td>

<td>Port</td>

<td>SSL</td>

</tr>

</thead>

<tbody>

<tr>

<td>Yahoo!</td>

<td>smtp.mail.yahoo.com</td>

<td>587</td>

<td>True</td>

</tr>

<tr>

<td>GMail</td>

<td>smtp.gmail.com</td>

<td>587</td>

<td>True</td>

</tr>

<tr>

<td>Hotmail</td>

<td>smtp.live.com</td>

<td>587</td>

<td>True</td>

</tr>

</tbody>

</table>

<a name="more"></a>  
<span style="color: blue; font-family: Verdana, sans-serif;">using</span><span style="font-family: Verdana, sans-serif;"> System.Net;  
</span><span style="color: blue; font-family: Verdana, sans-serif;">using</span><span style="font-family: Verdana, sans-serif;"> System.Net.Mail;  

</span><span style="color: blue; font-family: Verdana, sans-serif;">public</span><span style="font-family: Verdana, sans-serif;"> </span><span style="color: blue; font-family: Verdana, sans-serif;">void</span><span style="font-family: Verdana, sans-serif;"> SendEmail()  
</span><span style="font-family: Verdana, sans-serif;">{</span><span style="font-family: Verdana, sans-serif;">      
 <span style="color: green;">//設定smtp主機</span>  
    <span style="color: blue;">string</span> smtpAddress = <span style="color: #a31515;">"smtp.mail.yahoo.com"</span>;  
    <span style="color: green;">//設定Port</span>  
    <span style="color: blue;">int</span> portNumber = 587;  
    <span style="color: blue;">bool</span> enableSSL = <span style="color: blue;">true</span>;  
    <span style="color: green;">//填入寄送方email和密碼</span>  
    <span style="color: blue;">string</span> emailFrom = <span style="color: #a31515;">"email@gmail.com"</span>;  
    <span style="color: blue;">string</span> password = <span style="color: #a31515;">"abcdefg"</span>;  
    <span style="color: green;">//收信方email</span>  
    <span style="color: blue;">string</span> emailTo = <span style="color: #a31515;">"someone@domain.com"</span>;  
    <span style="color: green;">//主旨</span>  
    <span style="color: blue;">string</span> subject = <span style="color: #a31515;">"Hello"</span>;  
    <span style="color: green;">//內容</span>  
    <span style="color: blue;">string</span> body = <span style="color: #a31515;">"Hello, I'm just writing this to say Hi!"</span>;  

    <span style="color: blue;">using</span> (<span style="color: #2b91af;">MailMessage</span> mail = <span style="color: blue;">new</span> <span style="color: #2b91af;">MailMessage</span>())  
    {  
        mail.From = <span style="color: blue;">new</span> <span style="color: #2b91af;">MailAddress</span>(emailFrom);  
        mail.To.Add(emailTo);  
        mail.Subject = subject;  
        mail.Body = body;  
        <span style="color: green;">// 若你的內容是HTML格式，則為True</span>  
        mail.IsBodyHtml = <span style="color: blue;">false</span>;  

        <span style="color: green;">//夾帶檔案</span>  
        mail.Attachments.Add(<span style="color: blue;">new</span> <span style="color: #2b91af;">Attachment</span>(<span style="color: #a31515;">"C:\\SomeFile.txt"</span>));  
        mail.Attachments.Add(<span style="color: blue;">new</span> <span style="color: #2b91af;">Attachment</span>(<span style="color: #a31515;">"C:\\SomeZip.zip"</span>));  

        <span style="color: blue;">using</span> (<span style="color: #2b91af;">SmtpClient</span> smtp = <span style="color: blue;">new</span> <span style="color: #2b91af;">SmtpClient</span>(smtpAddress, portNumber))  
        {  
            smtp.Credentials = <span style="color: blue;">new</span> <span style="color: #2b91af;">NetworkCredential</span>(emailFrom, password);  
            smtp.EnableSsl = enableSSL;  
            smtp.Send(mail);  
        }  
    }  
}  

</span></pre>