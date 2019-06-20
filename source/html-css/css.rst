.. rst-class:: persian

CSS
===

:doc:`English <css-en>`

1. قوانین شکل دهی CSS
---------------------

1.1. اعتبار سنجی CSS
^^^^^^^^^^^^^^^^^^^^

از CSS معتبر استفاده کنید.

مگر اینکه با مشکلات CSS سرکار داشته باشید یا یه ساختار اختصاصی مد نظر داشته باشید
در غیر اینصورت از CSS معتبر استفاده کنید.

از ابزار هایی مثل `W3C CSS Validator`_ استفاده کنید.

استفاده از CSS معتبر یک خط کیفی قابل اندازه گیری است که به ما در پیدا کردن کد 
های CSS ای که موثر نیستند کمک می کند تا بتوانیم حذفشان کنیم، و این اطمینان را 
می دهند که از CSS به طور مناسب استفاده می کنیم.

1.2. نام ID ها و Class ها
^^^^^^^^^^^^^^^^^^^^^^^^^

از نام های عمومی و معمول برای ID ها و Class ها استفاده کنید.

به جای نامی که شیوه ارائه را نشان می دهد یا یک نام مرموز، همیشه از نامی برای ID 
ها و Class ها استفاده کنید که نشان دهنده هدف عنصر مورد نظر است. و یا اینکه یک
نام عمومی است.

نام های خاصی که هدف یک عنصر را منعکس می کنند باید ترجیج داده شوند چرا هم قابل 
فهم هستند و هم احتمال تغییر آنها کمتر است.

نام های عمومی نام های مناسبی برای عناصری هستند که خاص نیستند و تفاوت مفهومی با 
برادران خود ندارند. آنها معمولا به عنوان یک کمک کننده (header) مورد استفاده 
هستند.

استفاده از نام های عمومی و عملیاتی نیاز به توضیحات اضافی را کاهش می دهد.

.. code-block:: css
   :class: not-recommended

    /* Not recommended: meaningless */
    #yee-1901 {}

    /* Not recommended: presentational */
    .button-green {}
    .clear {}

.. code-block:: css

    /* Recommended: specific */
    #gallery {}
    #login {}
    .video {}

    /* Recommended: generic */
    .aux {}
    .alt {}

1.3. شکل نام ID ها و Class ها
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

نام ID ها و Class ها را تا حد امکان کوتاه و در حد ضرورت طولانی در نظر بگیرید.

سعی کنید آن چیزی که یک ID یا Class می رساند به خلاصه ترین شکل ممکن بنویسید.

از نام هایی استفاده کنید که سطح قابل پذیریش از قابل فهم بودن و تاثیر گذاری روی 
کد را داشته باشد.

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    #navigation {}
    .atr {}

.. code-block:: css

    /* Recommended */
    #nav {}
    .author {}

1.4. انواع Selector ها
^^^^^^^^^^^^^^^^^^^^^^

از پیشوند کردن نوع Selector در نام Class ها و ID ها اجتناب کنید.

مگر اینکه ضرورت داشته باشد (برای مثلا کلاس های کمکی)، از نام عنصر که با خط تیره 
جدا شده در نام Class ها و ID ها استفاده نکنید.

`به دلیل کارایی`_ از Selector والدین در شرایط غیر ضروری استفاده نکنید.

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    ul#example {}
    div.error {}

.. code-block:: css

    /* Recommended */
    #example {}
    .error {}

1.5. Shorthand Properties
^^^^^^^^^^^^^^^^^^^^^^^^^

از پراپرتی هایی که مختصر نویس و کوتاه هستند استفاده کنید.

CSS پراپرتی های `مختصر نویس`_ مختلفی را پیشنهاد می دهد (مثل ``font``) که باید هر
جایی که امکان دارد از اینها استفاده شود حتی در مواردی صریحا یک مقدار میگیرند.

استفاده از این مختصر نویس ها هم بهروری با بالا میبرد و هم قابل فهم بودن کد را.

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    border-top-style: none;
    font-family: palatino, georgia, serif;
    font-size: 100%;
    line-height: 1.6;
    padding-bottom: 2em;
    padding-left: 1em;
    padding-right: 1em;
    padding-top: 0;

.. code-block:: css

    /* Recommended */
    border-top: 0;
    font: 100%/1.6 palatino, georgia, serif;
    padding: 0 1em 2em;

1.6. صفر و واحد ها
^^^^^^^^^^^^^^^^^^

واحد های بعد از مقدار ``0`` را حذف کنید، مگر اینکه ضرورت داشته باشد.

مگر در صورت ضرورت از واحد بعد از مقدار ``0`` استفاده نکنید.

.. code-block:: css

    flex: 0px; /* This flex-basis component requires a unit. */
    flex: 1 1 0px; /* Not ambiguous without the unit, but needed in IE11. */
    margin: 0;
    padding: 0;

1.7. صفر های قبل اعشار
^^^^^^^^^^^^^^^^^^^^^^

صفرهای قبل اعشار را حذف کنید.

رقم ``0`` را در اعدادی که بین ۱ و ۱- در پشت اعشار قرار میگیردند نگذارید.

.. code-block:: css

    font-size: .8em;

1.8. نشانه گذاری اعداد بر مبنای 16
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

تا جایی که امکان دارد از سه کاراکتر برای اعداد بر مبنای ۱۶ استفاده کنید.

در رنگ ها که این امکان وجود دارد، از سه کارکتر برای اعداد بر مبنای ۱۶ استفاده 
کنید که هم کوتاه تر است و هم مختصر تر.

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    color: #eebbcc;

.. code-block:: css

    /* Recommended */
    color: #ebc;

1.9. پیشوند ها
^^^^^^^^^^^^^^

به Selector ها نام برنامه خاصی که برای آن هستند به عنوان پیشوند اضافه کنید.

برای پروژه ها بزرگ که کد شما ممکن است داخل پروژ های دیگر هم استفاده شود یا سایت
های دیگر از پیشوند (به عنوان فضای نامی) برای ID ها و Class ها استفاده کنید. از
یک نام کوتاه مشخص و واحد که با خط تیره جدا شده است.

استفاده از فضاهای نامی از تلاقی اسم ها جلوگیری و می کند و امکان نگهداری کد را 
راحت تر خواهد کرد، برای کار هایی مثل جستجو کردن و جایگزین کردن.س

.. code-block:: css

    .adw-help {} /* AdWords */
    #maia-note {} /* Maia */

1.10 جدا کنند در نام ID ها و Class ها
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

کلمات را در نام ID ها و Class ها با خط تیره جدا کنید.

کلمات و اختصارات را در Selector ها به هر هیچ کاراکتری ترکیب نکنید به جز خط تیره
زیرا خوانایی و قابل فهم بودن برنامه را بالا می برد.

.. code-block:: css
   :class: not-recommended

    /* Not recommended: does not separate the words “demo” and “image” */
    .demoimage {}

    /* Not recommended: uses underscore instead of hyphen */
    .error_status {}

.. code-block:: css

    /* Recommended */
    #video-id {}
    .ads-sample {}

1.11 Hack ها
^^^^^^^^^^^^

از Hack های CSS و برنامه های بازرسی کاربران استفاده نکنید. از راهکار های دیگر 
برای رفع مشکلات استفاده کنید.

این خیلی وسوسه انگیز است که از ابزار هایی که کاربران را بازرسی می کنند، یا فیلتر 
های خاص CSS، راهکار های خاص و یا Hack ها استفاده کنید. همه این رویکرد ها باید 
آخرین راه حل باشند تا بتوان به یک کد قابل نگهداری موثر و قابل مدیریت دست یافت. 
از راهکار های دیگر استفاده کنید، استفاده از هک ها به پروژه شما آسیب می زند و 
باعث ناپایداری پروژه می شود. استفاده از هک ها کار آسانی است اما یک بار استفاده 
از آنها باعث تکرار آنها می شود و تکرار آنها در کد کار درست نیست.

2. قوانین قالب بندی CSS
-----------------------

2.1. دستورات تعریفی
^^^^^^^^^^^^^^^^^^^

تعاریف را به ترتیب حروف الفبا مرتب کنید.

مرتب کردن تعاریف بر حسب حروف القبا کمک می کند تا یک کد ثابت و قابل نگهداری و 
یاد آوری داشته باشید.

پیشوند های خاص نام کتابخانه را در مرتب سازی در نظر نگیرید. اگر چه بعضی از پیشوند 
های کتابخانه ها در CSS در بین خودشان می توانند مرتب شوند (مثال ``-moz`` که قبل 
از ``-webkit`` می آید).

.. code-block:: css

    background: fuchsia;
    border: 1px solid;
    -moz-border-radius: 4px;
    -webkit-border-radius: 4px;
    border-radius: 4px;
    color: black;
    text-align: center;
    text-indent: 2em;

2.2. کنگره های محتوای بلاک
^^^^^^^^^^^^^^^^^^^^^^^^^^

محتوای هر بلاک را با فضای خالی جلو ببرید و کنگره ایجاد کنید.

همه `محتوای بلاک ها`_ را جلو ببرید، بصورت سلسه مراتبی این کار را انجام دهید.

.. code-block:: css

    @media screen, projection {

      html {
        background: #fff;
        color: #444;
      }

    }

2.3. نقطه پایان تعاریف
^^^^^^^^^^^^^^^^^^^^^^

بعد از هر تعریف از نقطه ویرگول استفاده کنید.

استفاده از نقطه ویرگول در انتهای هر تعریف هم در ثبات کد اهمیت دارد و هم دلایل 
برای توسعه پذیری کد دارد.

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    .test {
      display: block;
      height: 100px
    }

.. code-block:: css

    /* Recommended */
    .test {
      display: block;
      height: 100px;
    }

2.4. نقطه پایان پراپرتی ها
^^^^^^^^^^^^^^^^^^^^^^^^^^

بعد از دونقطه نام پراپرتی یک space بگذارید.

همیشه یک space بین پراپرتی و مقدارش بگذارید (نه بین پراپرتی و دو نقطه).

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    h3 {
      font-weight:bold;
    }

.. code-block:: css

    /* Recommended */
    h3 {
      font-weight: bold;
    }

2.5. جدا کردن بلاک های تعاریف
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

یک space بین آخرین Selector و بلاک تعاریف بگذارید.

همیشه یک space بین آخرین Selector و براکت باز شده برای شروع `بلاک تعاریف`_ بگذارید.

براکت باز شده بلااک تعاریف باید در همان خطی باش که آخرین Selector قرار دارد.

.. code-block:: css
   :class: not-recommended

    /* Not recommended: missing space */
    #video{
      margin-top: 1em;
    }

    /* Not recommended: unnecessary line break */
    #video
    {
      margin-top: 1em;
    }

.. code-block:: css

    /* Recommended */
    #video {
      margin-top: 1em;
    }

2.6. جدا کردن تعریف Selector ها
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Selector ها را از یک دیگر با خط جدید جدا کنید.

همیشه Selector را در یک خط جدید شروع کنید.

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    a:focus, a:active {
      position: relative; top: 1px;
    }

.. code-block:: css

    /* Recommended */
    h1,
    h2,
    h3 {
      font-weight: normal;
      line-height: 1.2;
    }

2.7. جدا کردن قوانین (Style ها)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

قوانین را با یک خط جدید جدا کنید.

همیشه یک خط خالی بین دو قانون قرار دهید.

.. code-block:: css

    html {
      background: #fff;
    }

    body {
      margin: auto;
      width: 50%;
    }

2.8. CSS Quotation Marks
^^^^^^^^^^^^^^^^^^^^^^^^^^

از تک ``''`` به جای دو ``""`` در تعاریف و مقادیر ویژگی ها و پراپرتی ها استفاده 
کنید.

از quotation در آدرس ``url()`` استفاده نکنید.

**استثنا:** اگر نیاز دارید که از ``@charset`` استفاده کنید از ``""`` استفاده 
کنید - `اجازه استفاده از تک quotation را ندارید`_.

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    @import url("https://www.google.com/css/maia.css");

    html {
      font-family: "open sans", arial, sans-serif;
    }

.. code-block:: css

    /* Recommended */
    @import url(https://www.google.com/css/maia.css);

    html {
      font-family: 'open sans', arial, sans-serif;
    }

3. قوانین Meta در CSS
---------------------

3.1. توضیحات بخش  ها
^^^^^^^^^^^^^^^^^^^^

از کامنت ها برای بخش بند استفاده کنید (اختیاری).

اگر امکانش هست sytle ها را بخش بندی کنید و با توضیحات از یکدیگر جدا کنید.

.. code-block:: css

    /* Header */

    #adw-header {}

    /* Footer */

    #adw-footer {}

    /* Gallery */

    .adw-gallery {}


.. _W3C CSS validator: https://jigsaw.w3.org/css-validator/
.. _به دلیل کارایی: http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/
.. _مختصر نویس: https://www.w3.org/TR/CSS21/about.html#shorthand
.. _محتوای بلاک ها: https://www.w3.org/TR/CSS21/syndata.html#block
.. _بلاک تعاریف: https://www.w3.org/TR/CSS21/syndata.html#rule-sets
.. _اجازه استفاده از تک quotation را ندارید: https://www.w3.org/TR/CSS21/syndata.html#charset