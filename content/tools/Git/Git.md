---
title: "git"
date: 2021-09-17T14:20:01+04:30
tags: ['git', 'VCS', ]
draft: false
---


<div dir='rtl'>

### فهرست

> - [مقدمه](#مقدمه)
> - [ساختار کامند های گیت](#ساختار-کامند-های-گیت)
> - [وارد کردن گیت به داخل پروژه](#وارد-کردن-گیت-به-داخل-پروژه)
> - [بررسی فایل های پروژه](#بررسی-فایل-های-پروژه)
> - [اضافه کردن تغییرات به حالت stage](#اضافه-کردن-تغییرات-به-حالت-stage)
> - [کامیت کردن تغییرات](#کامیت-کردن-تغییرات)
> - [مشاهده تاریخچه کامیت ها](#مشاهده-تاریخچه-کامیت-ها)
> - [بررسی عمیق تر تغییرات پروژه](#بررسی-عمیق-تر-تغییرات-پروژه)
> - [ساخت برنچ جدید در پروژه](#ساخت-برنچ-جدید-در-پروژه)
> - [رفتن به کامیت های گذشته](#رفتن-به-کامیت-های-گذشته)
> - [تغییر برنچ پروژه](#تغییر-برنچ-پروژه)
> - [مرج کردن برنچ](#مرج-کردن-برنچ)
> - [حذف کردن برنچ](#حذف-کردن-برنچ)
> - [حذف کردن برنچ بدون مرج کردن](#حذف-کردن-برنچ-بدون-مرج-کردن)
> - [کلون کردن پروژه از اینترنت](#کلون-کردن-پروژه-از-اینترنت)
> - [وصل کردن پروژه به فضای ابری](#وصل-کردن-پروژه-به-فضای-ابری)
> - [فرستادن پروژه به فضای ابری](#فرستادن-پروژه-به-فضای-ابری)
> - [مرچ کردن کامیت های پروژه در فضای ابری و سیستم لوکال](#مرچ-کردن-کامیت-های-پروژه-در-فضای-ابری-و-سیستم-لوکال)
> - [Author or Authors](#author-or-authors)

</div>

---

<div dir='rtl'>

### مقدمه

گیت یک سیستم کنترل ورژن
(VCS)
میباشد.ما سیستم های کنترل ورژن زیادی داریم اما در این بین امروزه گیت محبوبترین آنهاست. گیت در سال 2005 توسط لینوس توروالدز خالق کرنل لینوکس ساخته و بصورت اوپن سورس منتشر شد.

گیت را مثل یک سیستم بکاپ گیری در نظر بگیرید. در این سیستم به هر بکاپ
*commit*
می‌‌‌گویند.

فایل ها قبل از اینکه
*commit*
بشوند وارد حالتی به اسم
stage
می‌شوند، فایل هایی که
stage
شدند با یک دستور
*commit*
می‌شوند
و فایل هایی که در حالت
*stage*
نیستند به کامیت ها اضافه نمی‌شوند.

---

### ساختار کامند های گیت

به یاد داشته باشید که ساختار دستور گیت به این شکل است

<div dir='ltr'>


> git **switch** *--option* **args**

</div>

درواقع بعد از کامند 
*git*
شما یک سوییچ را برای انجام یک وظیفه خاص انتخاب می‌کنید
هر سوییچ دارای یک سری اپشن ها هستند که به نسبت اون اپشن نحوه عملکرد
سوییچ را تغییر می‌دهد.

مثلا برای دیدن لاگ ها 
از اپشن
`graph--`
استفاده کنید تا یک گراف بصری از برنچ ها به شما نمایش داده شود.

و در آخر ممکن است یک آپشن گزینه ورودی هایی هم بگیرد
مانند
<div dir='ltr'>

`git commit -m "message"`
</div>
که توضیحات شما را به کامیت اضافه می‌کند.

---

### وارد کردن گیت به داخل پروژه

در این مرحله ابتدا با دستور 
[cd](/posts/cd/cd/)
وارد پوشه پروژه‌ای شوید که می‌خواهید گیت را به آن اضافه کنید.

برای کار کردن و استفاده از گیت ابتدا باید آن را وارد پروژه کرد. با دستور زیر در دایرکتوری پروژه شما یک پوشه
`git.`
ساخته میشود و به این ترتیب گیت وارد پروژه شما میشود.
</div>
    
```bash
$ git init
# Initialized empty Git repository in <your folder path>/.git/
```
 
---

<div dir='rtl'>

### بررسی فایل های پروژه

برای اینکه وضعیت پروژه را بررسی کنیم از نظر اینکه چه فایل های جدیدی به پروژه اضافه شدند یا فایل هایی که از قبل در پروژه بودند محتوایشان تغغیری کرده یا نه از دستور
`git status`
استفاده می‌کنیم.

</div>
    
    $ git status                       
    # On branch main
    Your branch is up to date with 'origin/main'.

    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
            modified:   <file name>

    Untracked files:
      (use "git add <file>..." to include in what will be committed)
            <file name>

    no changes added to commit (use "git add" and/or "git commit -a")
 
---

<div dir='rtl'>
    
### اضافه کردن تغییرات به حالت stage

با دستور زیر میتوانید تغییرات پروژه از اضافه شدن فایل های جدید تا تغییرات فایل های قبلی را اصطلاحا به حالت stage ببرید و برای کامیت کردن و ثبت تغییرات آنها را آماده کنید. کافی است پس از کامند زیر اسم فایل مورد نظر را بنویسید تا وضعیت آن به stage تغییر کند.

اینکار برای این است که شما انتخاب کنید که چه فایل هایی کامیت بشوند و چه فایل هایی به کامیت اضافه نشوند.
    
</div>

    $ git add <file name>                    
<div dir='rtl'>
همچنین با سوییچ -a این دستور میتوانید تمام فایل ها را به حالت stage ببرید
</div>

    $ git add -a

---

<div dir='rtl'>

### کامیت کردن تغییرات

با دستور زیر میتوانید تمامی تغییراتی که با دستور قبل به حالت stage بردید را کامیت و ثبت کنید. پس از وارد کردن دستور زیر ادیتور دیفالت سیستم شما فایلی به نام
```COMMIT_EDITSMG```
را باز میکند و شما باید یک پیغام برای این کامیت بنویسید و با ذخیره کردن و بستن فایل مربوطه تمام تغییرات پروژه شما ثبت میشود.
    
</div>

    $ git commit
<div dir='rtl'>

همچنین با سوییچ
`m-`
میتوانید بدون باز شدن ادیتور، پیغام مربوطه را بنویسید و تغییرات پروژه را ثبت کنید
</div>

    $ git commit -m "<your message>"
---

<div dir='rtl'>

### مشاهده تاریخچه کامیت ها

گاهی ما میخواهیم بررسی کنیم که روی پروژه خودمان چندبار کامیت کرده ایم و تغییرات پروژه را ببینیم و ببینیم
**چه کسی**
و در
**چه تاریخی**
این کامیت را انجام داده است. با دستور زیر میتوانیم این تاریخچه را ببینیم.توجه کنید در پیامی که بعد از این دستور مشاهده میکنید کامیتی که جلو آن عبارت  
HEAD
را میبینید، این یعنی
**آخرین کامیتی**
که روی این پروژه انجام شده
</div>

    $ git log
    #commit <commit unic code> (HEAD -> <branch name>
    #Author: <Author name>
    #Date: <commit date>
    #             <commit message>
    
---

<div dir='rtl'>

### بررسی عمیق تر تغییرات پروژه

در دستور قبلی فهمیدیم که چگونه میتوانیم تغییرات گذشته پروژه را ببینیم. حال اگر بخواهیم بصورت جزئی تر این تفاوت هر کامیت
با یک کامیت دیگر را مشاهده کنیم میتوانیم از دستور زیر استفاده کنیم.
</div>

    $ git diff <commit unic code>
    
---

<div dir='rtl'>

### ساخت برنچ جدید در پروژه
    
ما در یک پروژه برنچ ها یا شاخه های مختلفی میتوانیم ایجاد کنیم و بخش های مختلف پروژه را در شاخه های مختلف گسترش دهیم. برای دیدن برنچ های موجود در پروژه خودمان کافی است دستور زیر را وارد کنیم تا لیستی از برنچ های موجود در پروژه ببینیم

</div>

    $ git branch
    #*master

<div dir='rtl'>
برای ساخت برنچ جدید کافی است به دستور بالا اسم مورد نظر خودمان را اضافه کنیم
تا یک شاخه جدیدی از پروژه با همان نامی که دادیم بسازد
</div>

    $ git branch  <branch name>
---

<div dir='rtl'>

### تغییر برنچ پروژه

اگر بخواهیم برنچ پروژه را تغییر دهیم و بخواهیم بخشی از یک پروژه را در شاخه ای دیگر توسعه دهیم میتوانیم با دستور زیر تغییر برنچ را انجام دهید. یادتان باشد که تغییرات هر برنچ در خود آن برنچ ذخیره میشود نه در برنچ اصلی پروژه.به عنوان مثال وقتی شما در یک برنچی از پروژه یک فایل را حذف میکنید وقتی دوباره به برنچ اصلی یا یک برنچ دیگر بروید شما این فایل را خواهید دید زیرا آن فایل در یک برنچ دیگر حذف شده است.
</div>

    $ git checkout <branch name>
    #Switched to branch '<branch name>'

---

<div dir='rtl'>

### رفتن به کامیت های گذشته

در برخی زمان ها ممکن است  که ما در پروژه به مشکلی برخورد کنیم که نیاز باشد به سراغ کامیت های قدیمی پروژه برویم و تغییراتی در آن بدهیم.
برای اینکه بتوانیم وارد یکی از کامیت های قبلی پروژه شویم مانند دستوری که در بخش قبلی گفتیم عمل میکنیم با این تفاوت که باید بجای اسم بخشی از آیدی آن کامیت را بنویسیم.
با انجام این دستور یک برنچ جدید ساخته میشود که مانند برنچ های عادی پروژه است با این تفاوت که کامیت مد نظر ما آخرین کامیت آن برنچ است.
</div>

    $ git checkout <A part of the unic commit>
    #Note: switching to '&lt;A part of the unic commit code&gt;'.
    #You are in 'detached HEAD' state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this state without   impacting any branches by switching back to a branch.
    #If you want to create a new branch to retain commits you create, you may
    #do so (now or later) by using -c with the switch command. Example:
    #
    #  git switch -c <new-branch-name>
    #
    #Or undo this operation with:
    #
    #  git switch -
    #
    #Turn off this advice by setting config variable advice.detachedHead to false
    #
    #HEAD is now at 58a652e add hello

---

<div dir='rtl'>

### مرج کردن برنچ

اگر بخواهیم تغییرات یک برنچ را در برنچ های دیگر نیز اعمال کنیم میتوانیم آن دو برنچ را مرج کنیم. فرض کنید یک برنچ به اسم x داریم و میخواهیم تغییرات آن را بر روی برنچ master که برنچ اصلی پروژه ما است اعمال کنیم. برای این کار باید وارد برنچ master شویم و دستور زیر را وارد کنیم
</div>

    $ git merge x

---

<div dir='rtl'>

### حذف کردن برنچ

در صورتی که بخواهیم یک برنچ را که دیگر نیازی به آن را نداریم حذف کنیم میتوانیم با دستور زیر برنچ مربوطه را حذف کنیم((برای این کار نباید روی برنچی که میخواهید حذف کنید باشید))
</div>

    $ git branch -d <branch name>
    #Deleted branch <branch name>.

---

<div dir='rtl'>

### حذف کردن برنچ بدون مرج کردن

درصورتی که بخواهیم مثل بخش بالایی برنچی که مرج نشده را پاک کنیم به یک ارور برمیخوریم که برنچ مورد نظر مرج نشده است. درصورتی که بخواهیم برنچی را بدون مرج کردن پاک کنیم باید از سوییچ
`-D`
استفاده کنیم
</div>

    $ git branch -D <branch name>
---

<div dir='rtl'>

### کلون کردن پروژه از اینترنت

یکی از قابلیت های جذاب گیت این است که شما با استفاده از گیت میتوانید یکسری فایل از فضای اینترنتی مانند گیت هاب دریافت یا اصطلاحا کلون کنید. البته این کار درصورتی انجام میشود که گیت اجازه دسترسی به ریپازیتوری(مخزن) مربوطه داشته باشد یا آن فضا در اینترنت  وجود داشته باشد. برای کلون کردن یک پروژه از اینترنت بر روی سیستم خودمان کافی است به دایرکتوری که پروژه را میخواهیم قرار دهیم برویم و در آنجا دستور زیر را وارد کنیم. درصورتی که این کار موفقیت آمیز باشد شما فایل های پروژه را در یک فولدر با نام مخزن خواهید دید.

</div>

    $ git clone <project url>

---

<div dir='rtl'>

### وصل کردن پروژه به فضای ابری

اگر بخواهیم یک پروژه را به یک فضای ابری مانند یک ریپازیتوری گیت هاب متصل کنیم اصطلاحا پروژه را به آن ریپازیتوری ریموت میکنیم.ما میتوانیم یک پروژه ره به چندین لینک و فضای مختلف ریموت کنیم و این یعنی عدم محدودیت در تعداد ریموت های یک پروژه , همچنین هر لینکی را میتوانید برای ریموت کردن قرار دهید حتی لینک گوگل. برای این کار میتوانید با دستور زیر یک ریموت اضافه کنید((مرسوم است ریموت اصلی پروژه اسمش origin باشد))
</div>

    $ git remote add <remote name> <remote url>
<div dir='rtl'>
همچنین برای مشاهده کردن تمام ریموت های موجود در یک پروژه با دستور زیر میتوانید ریموت های مختلف را ببینید و همچنین با دستور بعدی آن لینک هایی که در هر ریموت قرار دادید را میتوانید مشاهده کنید.
</div>

    $ git remote
    #origin
    #...
    
    #for see remote link
    $git remote get-url <name>

---

<div dir='rtl'>

### فرستادن پروژه به فضای ابری

اگر بخواهیم تغییرات پروژه خودمان یا کل پروژه را به فضای ابری یکی از ریموت هایی که ساختیم بفرستیم از 
سوییچ
`push`
 استفاده میکنیم. درصورتی که گیت ما دسترسی لازم به آن فضایی که ریموت کردیم داشته باشد یا فضای مربوطه در اینترنت وجود داشته باشد این کار انجام خواهد شد. همچنین ما میتوانیم هر برنچی را که میخواهیم را به ریموت ارسال کنیم و الزامی نیست که حتما برنچ اصلی ارسال شود.
</div>

    $ git push <remote name> <branch name>
    # for example 
    $ git push origin master

---

<div dir='rtl'>

### مرچ کردن کامیت های پروژه در فضای ابری و سیستم لوکال

گاهی وقتها ممکن است ما تغییراتی را در پروژه ایجاد کنیم اما نه در سیستم لوکال خودمان بلکه در فضای ابری که پروژه قرار دارد. 
یا ممکن است که کسی روی ریموت تغیراتی ایجاد کرده باشد. 
این باعث میشود تعداد کامیت های پروژه و تغییرات آن بین فضای ابری و سیستم لوکال یکی نباشد که اگر این اتفاق بیفتد در آینده اگر ما در سیستم لوکال در پروژه تغییراتی ایجاد کردیم و میخواستیم پروژه را به فضای ابری push کنیم با اروری مبنی بر عدم هماهنگی کامیت ها بین فضای ریموت و سیستم خودمان مواجه میشویم. برای اینکه این مشکل رفع شود و کامیت های بین دو فضایی که پروژه قرار دارد سینک و مچ شود کافی است دستور زیر را وارد کنیم تا کامیت های انجام شده در فضای ابری بر روی پروژه در فضای لوکال سیستم ما نیز اعمال شود.
</div>

```bash
$ git pull <remote name> <branch name>
```


---

### Author or Authors

- *[Shahriar](https://github.com/shahriaarrr)* | **<shahriaarrr@gmail.com>**
- *[Arya](https://github.com/shabane)* | **<m.mohamadshabane@gmail.com>**