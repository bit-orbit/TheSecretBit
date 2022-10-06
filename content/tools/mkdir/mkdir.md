---
title: "mkdir"
date: 2022-03-13T17:30:52+03:30
draft: false
---

<div dir='rtl'>

### فهرست

> - [مقدمه](#مقدمه)
> - [ایجاد یک یا چند دایرکتوری به شکل همزمان](#ایجاد-یک-یا-چند-دایرکتوری-به-شکل-همزمان)
> - [تنظیم مد دایرکتوری](#تنظیم-مد-دایرکتوری)
> - [نمایش جزئیات عملیات](#نمایش-جزئیات-عملیات)
> - [ایجاد دایرکتوری های تو در تو](#ایجاد-دایرکتوری-های-تو-در-تو)
> - [Author or Authors](#author-or-authors)
</div>




---
<div dir='rtl'>

### مقدمه
برای ایجاد دایرکتوری در ترمینال میتوانید از ابزار mkdir استفاده کنید.
با استفاده از این ابزار میتوانید در کمتر از چند ثانیه هر تعداد دایرکتوری که نیاز دارید را ایجاد کنید.
</div>




---
<div dir='rtl'>

### ایجاد یک یا چند دایرکتوری به شکل همزمان
اگر میخواهید که یک یا چند دایرکتوری به شکل همزمان ایجاد کنید، کافیست که از دستور mkdir استفاده کنید و نام دایرکتوری ها را با فاصله از هم دیگر جدا کنید.
</div>

    $ mkdir dir1

    Or 

    $ mkdir dir1 dir2 dir3 dir4

---
<div dir='rtl'>

### تنظیم مد دایرکتوری
میتوانید با استفاده از سوییچ m- برای یک یا چند دایرکتوری به شکل همزمان مد تنظیم کنید. در مثال زیر یک دایرکتوری با مجوز 700 را ایجاد میکنیم . مجوز 700 به این معناست که فقط کاربری که این دایرکتوری را ایجاد کرده حق و اجازه دسترسی به آن را دارد. لازم به ذکر است بدانید که نحوه اختصاص دادن مجوزها همانند دستور chmod است. و بهتر است بدانید که هنگامی که از سوییچ m- استفاده نمی شود دایرکتوری هایی که ایجاد میشوند معمولا دارای مجوزهای 755 یا 775 هستند.
</div>

    mkdir -m 700 test.txt

---
<div dir='rtl'>

### نمایش جزئیات عملیات
با استفاده از سوییچ v- میتوانید جزئیات عملیات را به شکل کامل مشاهده کنید.
</div>

    $ mkdir -v dir1

---
<div dir='rtl'>

### ایجاد دایرکتوری های تو در تو
اگر بخواهید به شکل تک به تک درون هر دایرکتوری جا به جا شوید و درون هر دایرکتوری دستور mkdir را استفاده کنید . قطعا خسته و کلافه خواهید شد. برای ایجاد دایرکتوری های تو در تو کافیست وارد دایرکتوری مورد نظر شوید و از سوییچ p- برای ایجاد دایرکتوری هایی که وجود ندارند استفاده کنید.
فقط توجه داشته باشید که این سوییچ درصورت وجود نداشتن دایرکتوری اقدام به ساخت آن خواهد کرد. در غیر اینصورت به ارور خواهید خورد. 
</div>

    $ mkdir -p amir/amir1/amir2/amir3


---
### Author or Authors

- *[Amirhosein](https://github.com/amirhoseinsb)* | **<amirhoseinsohrabi.official@gmail.com>**