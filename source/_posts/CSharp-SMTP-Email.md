---
title: C# 使用 SMTP 寄送 Email
date: 2014-11-02 05:01:00
tags: [C#]
---

依據要使用的Mail服務更改smtpAddress、portNumber以及enableSSL三個變數

|主機名稱	|SMTP Address	|Port|	SSL|
|:------------- |-------------| -----|
|Yahoo!	|smtp.mail.yahoo.com	|587	|True|
|GMail	|smtp.gmail.com	|587	|True|
|Hotmail	|smtp.live.com	|587	|True|


```Csharp
using System.Net;
using System.Net.Mail;

public void SendEmail()
{    
    //設定smtp主機
    string smtpAddress = "smtp.mail.yahoo.com";
    //設定Port
    int portNumber = 587;
    bool enableSSL = true;
    //填入寄送方email和密碼
    string emailFrom = "email@gmail.com";
    string password = "abcdefg";
    //收信方email
    string emailTo = "someone@domain.com";
    //主旨
    string subject = "Hello";
    //內容
    string body = "Hello, I'm just writing this to say Hi!";
 
    using (MailMessage mail = new MailMessage())
    {
        mail.From = new MailAddress(emailFrom);
        mail.To.Add(emailTo);
        mail.Subject = subject;
        mail.Body = body;
        // 若你的內容是HTML格式，則為True
        mail.IsBodyHtml = false;
 
        //夾帶檔案
        mail.Attachments.Add(new Attachment("C:\\SomeFile.txt"));
        mail.Attachments.Add(new Attachment("C:\\SomeZip.zip"));
 
        using (SmtpClient smtp = new SmtpClient(smtpAddress, portNumber))
        {
            smtp.Credentials = new NetworkCredential(emailFrom, password);
            smtp.EnableSsl = enableSSL;
            smtp.Send(mail);
        }
    }
}
```