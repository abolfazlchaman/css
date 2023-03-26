# ‏راهنمای سبک Airbnb CSS / Sass 

*یک رویکرد عمدتا معقول به CSS و Sass*

## فهرست مطالب

1. [ترمینولوژی](#ترمینولوژی)
    - [اعلامیه قوانین](#اعلامیه-قوانین)
    - [انتخابگرها](#انتخابگرها)
    - [ویژگی ها](#ویژگی-ها)
1. [CSS](#css)
    - [قالب بندی](#قالب-بندی)
    - [توضیحات](#توضیحات)
    - [OOCSS و BEM](#oocss-و-bem)
    - [انتخابگرهای شناسه ای](#انتخابگرهای-شناسه-ای)
    - [قلاب های جاوا اسکریپتی](#قلاب-های-جاوا-اسکریپتی)
    - [حاشیه](#حاشیه)
1. [Sass](#sass)
    - [سینتکس](#سینتکس)
    - [مرتب سازی](#مرتب-سازی-ویژگی-ها)
    - [متغیر ها](#متغیر-ها)
    - [میکسین ها(Mixins)](#mixins)
    - [گسترش بخشنامه](#گسترش-بخشنامه)
    - [انتخابگرهای تو در تو](#انتخابگرهای-تو-در-تو)
1. [ترجمه ها](#ترجمه-ها)
1. [مجوز](#مجوز)

## ترمینولوژی

### اعلامیه قوانین

"اعلامیه قوانین" نامی است که به یک انتخابگر (یا گروهی از انتخابگرها) با گروهی از ویژگی ها داده می شود. برای مثال:

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}
```

### انتخابگرها

در یک اعلان قانون،  “انتخابگرها“ بیت‌هایی هستند که تعیین می‌کنند کدام عناصر در درخت DOM با ویژگی‌های تعریف‌شده استایل‌بندی شوند. انتخابگرها می توانند عناصر HTML و همچنین کلاس یک عنصر، شناسه یا هر یک از ویژگی های آن را مطابقت دهند. در اینجا چند نمونه از انتخابگرها آورده شده است:

```css
.my-element-class {
  /* ... */
}

[aria-hidden] {
  /* ... */
}
```

### ویژگی ها

در نهایت، ویژگی‌ها چیزی هستند که به عناصر انتخابی یک اعلان قانون سبک خود را می‌دهند. ویژگی ها جفت های کلید-مقدار هستند و یک اعلان قانون می تواند حاوی یک یا چند اعلان ویژگی باشد. تعریف ویژگی ها به شرح زیر است:

```css
/* some selector */ {
  background: #f1f1f1;
  color: #333;
}
```

**[⬆ بازگشت به بالا](#فهرست-مطالب)**

## ‏CSS

### قالب بندی

* از زبانه های نرم (2 فاصله) برای فرورفتگی استفاده کنید.
* در نام کلاس ها خط تیره را به camelCasing ترجیح دهید.
  - اگر از BEM استفاده می کنید، زیرخط و PascalCasing مشکلی ندارد (به [OOCSS and BEM](#oocss-و-bem) در زیر مراجعه کنید).
* از انتخابگرهای ID استفاده نکنید.
* هنگام استفاده از چند انتخابگر در یک اعلان قانون، به هر انتخابگر خط خاص خود را بدهید.
* قبل از بریس باز `{` در اعلان‌های قوانین یک فاصله قرار دهید.
* در ویژگی ها، یک فاصله بعد از کاراکتر `:` قرار دهید، اما نه قبل از آن.
* بریس بسته `}` اعلان‌های قوانین را در یک خط جدید قرار دهید.
* خطوط خالی بین اعلامیه های قوانین قرار دهید.

**بد**

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}
```

**خوب**

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}
```

### توضیحات

* برای بلوکی کردن نظرات، نظرات خط (`//` در Sass-land) را ترجیح دهید.
* نظرات را در خط خود ترجیح دهند. از اظهار نظرهای آخر خط خودداری کنید.
* برای کدهایی که مستندسازی نمی‌شوند، نظرات دقیق بنویسید:
  - موارد استفاده از z-index
  - سازگاری یا کد های خاص مرورگر

### ‏OOCSS و BEM

ما ترکیبی از OOCSS و BEM را به دلایل زیر تشویق می کنیم:

  * این به ایجاد روابط واضح و دقیق بین CSS و HTML کمک می کند
  * این به ما کمک می کند تا اجزای قابل استفاده مجدد و قابل ترکیب را ایجاد کنیم
  * این امکان لانه سازی کمتر و ویژگی کمتر را فراهم می کند
  * این به ساختن شیوه نامه های مقیاس پذیر کمک می کند

**OOCSS**، یا "CSS شی گرا"، رویکردی برای نوشتن CSS است که شما را تشویق می کند تا به شیوه نامه های خود به عنوان مجموعه ای از "اشیاء" فکر کنید: قطعات قابل استفاده مجدد و تکرار شونده که می توانند به طور مستقل در یک وب سایت استفاده شوند.

  * Nicole Sullivan's [راهنمای OOCSS](https://github.com/stubbornella/oocss/wiki)
  * Smashing Magazine's [مقدمه ای بر OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)

**BEM** یا "Block-Element-Modifier" یک قرارداد _نامگذاری_ برای کلاس های HTML و CSS است. این در ابتدا توسط Yandex با پایگاه های کد بزرگ و مقیاس پذیری در ذهن توسعه داده شد و می تواند به عنوان مجموعه ای محکم از دستورالعمل ها برای پیاده سازی OOCSS باشد.

  * CSS Trick's [BEM 101](https://css-tricks.com/bem-101/)
  * Harry Roberts' [مقدمه ای بر BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

ما یک نوع BEM را با "بلوک‌های PascalCased" توصیه می‌کنیم، که وقتی با کامپوننت‌ها (به عنوان مثال React) ترکیب می‌شود، به‌خوبی کار می‌کند. زیرخط و خط تیره هنوز برای اصلاح کننده ها و کودکان استفاده می شود.

**مثال ها**

```jsx
// ListingCard.jsx
function ListingCard() {
  return (
    <article class="ListingCard ListingCard--featured">

      <h1 class="ListingCard__title">Adorable 2BR in the sunny Mission</h1>

      <div class="ListingCard__content">
        <p>Vestibulum id ligula porta felis euismod semper.</p>
      </div>

    </article>
  );
}
```

```css
/* ListingCard.css */
.ListingCard { }
.ListingCard--featured { }
.ListingCard__title { }
.ListingCard__content { }
```

* ‏`.ListingCard` «بلوک» است و کامپوننت‌ سطح بالاتر را نشان می دهد
* ‏`.ListingCard__title` یک "عنصر" است و نشان دهنده نسل `.ListingCard` است که به ترکیب بلوک به عنوان یک کل کمک می کند.
* ‏`.ListingCard--featured` یک «تغییردهنده» است و وضعیت یا تغییر دیگری را در بلوک `.ListingCard` نشان می‌دهد.

### انتخابگرهای شناسه ای

در حالی که امکان انتخاب عناصر توسط ID در CSS وجود دارد، به طور کلی باید آن را یک ضد الگو در نظر گرفت. انتخابگرهای شناسه سطح غیرضروری بالایی از [ویژگی](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) را به اعلامیه‌های قوانین شما معرفی می‌کنند و قابل استفاده مجدد نیستند.

برای اطلاعات بیشتر در مورد این موضوع، [مقاله CSS Wizardry](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) را در مورد پرداختن به ویژگی بخوانید.

### قلاب های جاوا اسکریپتی

از اتصال به یک کلاس در CSS و JavaScript خودداری کنید. تلفیق این دو اغلب منجر به اتلاف زمان در طول بازسازی مجدد می شود، زمانی که یک توسعه دهنده باید به هر کلاسی که در حال تغییر است ارجاع دهد، و در بدترین حالت، توسعه دهندگان از ترس شکستن عملکرد می ترسند که تغییراتی ایجاد کنند.

توصیه می‌کنیم کلاس‌های اختصاصی جاوا اسکریپت را برای اتصال به آن‌ها با پیشوند `.js-` ایجاد کنید:

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

### حاشیه

از `0` به جای `none` استفاده کنید تا مشخص کنید یک سبک حاشیه ندارد.

**بد**

```css
.foo {
  border: none;
}
```

**خوب**

```css
.foo {
  border: 0;
}
```
**[⬆ بازگشت به بالا](#فهرست-مطالب)**

## ‏Sass

### سینتکس

* از نحو `.scss` استفاده کنید، نه از نحو اصلی `.sass`.
* اعلان‌های CSS معمولی و `@include` خود را به صورت منطقی ترتیب دهید (به زیر مراجعه کنید)

### مرتب سازی ویژگی ها

1. تعریف ویژگی ها

    همه تعریف ویژگی های استاندارد، هر چیزی که `@include` یا انتخابگر تودرتو نیست را لیست کنید.

```scss
    .btn-green {
      background: green;
      font-weight: bold;
      // ...
    }
```

2.‏`@include` تعریف

گروه بندی `@include` ها در پایان خواندن کل انتخابگر را آسان تر می کند.

```scss
    .btn-green {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);
      // ...
    }
```

3. انتخابگرهای تو در تو

    انتخابگرهای تودرتو، _اگر لازم باشد_، به آخر می‌روند، و هیچ چیز به دنبال آنها نمی‌رود. بین اعلان‌های قوانین و انتخابگرهای تودرتو و همچنین بین انتخابگرهای تودرتوی مجاور، فضای خالی اضافه کنید. همان دستورالعمل های بالا را برای انتخابگرهای تودرتو اعمال کنید.

```scss
    .btn {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);

      .icon {
        margin-right: 10px;
      }
    }
```

### متغیر ها

نام متغیرهای dash-cased (مانند `$my-variable`) را به نام متغیر camelCased یا snake_cased ترجیح دهید. پیشوند نام متغیرهایی که قرار است فقط در یک فایل مورد استفاده قرار گیرند با زیرخط (مثلاً `$_my-variable`) قابل قبول است.

### ‏Mixins

میکسین ها باید برای جلوگیری از تکرار کد شما، اضافه کردن وضوح یا پیچیدگی انتزاعی استفاده شوند - به همان روشی که توابع نام‌گذاری شده خوب هستند. ترکیب‌هایی که هیچ آرگومانی را نمی‌پذیرند می‌توانند برای این کار مفید باشند، اما توجه داشته باشید که اگر بار خود را فشرده نمی‌کنید (به عنوان مثال gzip)، ممکن است باعث تکرار کدهای غیرضروری در سبک‌های حاصل شود.

### گسترش بخشنامه

از `@extend` باید اجتناب شود، زیرا رفتار نامشهود و بالقوه خطرناکی دارد، به‌ویژه وقتی با انتخابگرهای تودرتو استفاده می‌شود. حتی اگر ترتیب انتخابگرها بعداً تغییر کند (مثلاً اگر در فایل‌های دیگر باشند و ترتیب بارگذاری فایل‌ها تغییر کند) می‌تواند باعث ایجاد مشکل شود. Gzipping باید بیشتر صرفه‌جویی‌هایی را که با استفاده از `@extend` به دست می‌آورید، انجام دهد، و می‌توانید با میکس‌ها تکرار کد در برگه‌های سبک خود را به خوبی کم کنید.

### انتخابگرهای تو در تو

**انتخابگرها را بیش از سه سطح در عمق قرار ندهید!**

```scss
.page-container {
  .content {
    .profile {
      // ‎!توقف کنید
    }
  }
}
```

وقتی انتخابگرها اینقدر طولانی می شوند، احتمالاً CSS می نویسید که:

* به شدت با HTML (شکننده) همراه است *— یا —*
* بیش از حد خاص (قدرتمند) *— یا —*
* قابل استفاده مجدد نیست


تاکید میکنیم: **هرگز انتخابگرهای شناسه را تودرتو نکنید**

اگر در وهله اول باید از انتخابگر ID استفاده کنید (و واقعاً باید سعی کنید از این کار استفاده نکنید)، آنها هرگز نباید تو در تو باشند. اگر متوجه شدید که این کار را انجام می‌دهید، باید دوباره به نشانه‌گذاری خود مراجعه کنید یا بفهمید که چرا به چنین ویژگی قوی نیاز است. اگر HTML و CSS خوب می نویسید، **هرگز** نباید این کار را انجام دهید.

**[⬆ بازگشت به بالا](#فهرست-مطالب)**

## ترجمه ها

  این راهنمای سبک به زبان های دیگر نیز موجود است:

  - ![id](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Indonesia.png) **باهاسا اندونزی**: [mazipan/css-style-guide](https://github.com/mazipan/css-style-guide)
  - ![tw](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Taiwan.png) **چینی (سنتی)**: [ArvinH/css-style-guide](https://github.com/ArvinH/css-style-guide)
  - ![cn](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/China.png) **زبان چینی ساده شده**: [Zhangjd/css-style-guide](https://github.com/Zhangjd/css-style-guide)
  - ![fr](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/France.png) **فرانسوی**: [mat-u/css-style-guide](https://github.com/mat-u/css-style-guide)
  - ![ka](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Georgia.png) **گرجی**: [DavidKadaria/css-style-guide](https://github.com/davidkadaria/css-style-guide)
  - ![ja](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Japan.png) **ژاپنی**: [nao215/css-style-guide](https://github.com/nao215/css-style-guide)
  - ![ko](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/South-Korea.png) **کره ای**: [CodeMakeBros/css-style-guide](https://github.com/CodeMakeBros/css-style-guide)
  - ![PT-BR](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Brazil.png) **پرتغالی (برزیل)**: [felipevolpatto/css-style-guide](https://github.com/felipevolpatto/css-style-guide)
  - ![pt-PT](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Portugal.png) **پرتغالی (پرتغال)**: [SandroMiguel/airbnb-css-style-guide](https://github.com/SandroMiguel/airbnb-css-style-guide)
  - ![ru](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Russia.png) **روسی**: [rtplv/airbnb-css-ru](https://github.com/rtplv/airbnb-css-ru)
  - ![es](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Spain.png) **اسپانیایی**: [ismamz/guia-de-estilo-css](https://github.com/ismamz/guia-de-estilo-css)
  - ![vn](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Vietnam.png) **ویتنامی**: [trungk18/css-style-guide](https://github.com/trungk18/css-style-guide)
  - ![vn](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Italy.png) **ایتالیایی**: [antoniofull/linee-guida-css](https://github.com/antoniofull/linee-guida-css)
  - ![de](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Germany.png) **آلمانی**: [tderflinger/css-styleguide](https://github.com/tderflinger/css-styleguide)

**[⬆ بازگشت به بالا](#فهرست-مطالب)**

## مجوز

(مجوز MIT)

Copyright (c) 2015 Airbnb

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[⬆ بازگشت به بالا](#فهرست-مطالب)**
