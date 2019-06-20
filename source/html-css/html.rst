.. rst-class:: persian

HTML
====

:doc:`English <html-en>`

1. قوانین شکل کد های HTML
---------------------------

1.1. Document Type
^^^^^^^^^^^^^^^^^^^^

از HTML5 استفاده کنید.

HTML5 و syntax آن برای همه سند ها ترجیج داده می شود: ``<!DOCTYPE html>``.

(توصیه می شود که از HTML به عنوان ``text/html`` استفاده شود به جای استفاده از
XHTML. در XHTML به عنوان |application/xhtml+xml|_، نه پشتیبانی مرورگر ها وجود 
دارد و نه از زیر ساخت آن پشتیبانی می شود و نسبت به HTML هم بهینه سازی کمتری
دارد).

همچنین در نوشتار HTML از عناصر خالی را نبندید بعنوان مثال بنویسید ``<br>`` به 
جای اینکه بنویسید ``<br />``.

1.2. اعتبار سنجی HTML
^^^^^^^^^^^^^^^^^^^^^^^

تا جایی که امکان دارد از HTML معتبر استفاده کنید.

تا جایی که امکان دارد از HTML معتبر استفاده کند مگر اینکه ممکن نباشد و شما 
کارایی در اندازه فایل ها را از دست بدهید.

از ابزار هایی مثل `W3C HTML validator`_ برای بررسی استفاده کنید.

استفاده از HTML معتبر مثل یک خط قابل اندازه گیری ویژگی های کیفی است که در 
یادگیری درباره تکنیک های نیازمندی و محدودیت ها مورد استفاده قرار میگیرد و این 
اطمینان را می دهد که از HTML استفاه شده است.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <title>Test</title>
    <article>This is only a test.

.. code-block:: html

    <!-- Recommended -->
    <!DOCTYPE html>
    <meta charset="utf-8">
    <title>Test</title>
    <article>This is only a test.</article>

1.3. معانی
^^^^^^^^^^^^

با توجه به اهدافی که HTML دارد از آن استفاده کنید.

از عناصر (که به اشتباه «تگ» گفته می شوند) در کاری که برای آن ساخته شده اند 
استفاده کنید. برای مثل از تیتر heading برای تیتر ها، از عنصر ``p`` برای پاراگراف 
ها، از ``a`` برای لنگر ها و لینک ها و ...

استفاده از HTML در جهت هدفی که ساخته شده است برای دسترسی و سهل الوصول بودن و 
قابل استفاده مجدد بودن و تاثیر گذاری کد بسیار مهم است.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <div onclick="goToRecommendations();">All recommendations</div>

.. code-block:: html

    <!-- Recommended -->
    <a href="recommendations/">All recommendations</a>

1.4. جایگزین های Multimedia
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

همیشه یک محتوای جایگزین برای multimedia ها داشته باشید.

اطمینان پیدا کنید که برای multimedia ها مثل عکس ها، فیلم ها، اشیاء متحرکی که با 
``convas`` متحرک شده اند، محتوای جایگزین در دسترس است. برای عکس یک متن جایگزین 
که معنای عکس را برساند ``alt`` بگذارید، برای فیلم ها و صدا ها یک رونوشت به همراه
عنوان قرار دهید.

فراهم کردن یک محتوای جایگزین از لحاظ دسترسی بسیار مهم است: یک کاربر نابینا نشانه
ها و امکانات کمی برای این دارد که بفهمد محتوای عکس چیست (بدون ``@alt``)، و 
کاربران دیگر ممکن است راهی برای فهمیدن محتوای یک صوت یا فیلم را نداشته باشند.

(برای تصاویر ویژگی ``alt`` یک توضیح اضافی راجع به تصویر می دهد، برای تصاویری که 
تنها برای زیبایی استفاه شده اند و امکان استفاده مستقیم آنها در css وجود نداشته
است از متن جایگزین استفاده نکنید به این صورت ``alt=""``).

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <img src="spreadsheet.png">

.. code-block:: html

    <!-- Recommended -->
    <img src="spreadsheet.png" alt="Spreadsheet screenshot.">

1.5. جدا کردن بخش های مهم
^^^^^^^^^^^^^^^^^^^^^^^^^^^

ساختار و ارائه و رفتار از از یکدیگر جدا کنید.

بسیار سخت گیرانه ساختار ها (markup)، شیوه ارائه (styling)، و رفتار ها 
(scripting) را از یکدیگر جداکنید و ارتباط بین این سه بخش را به حداقل ممکن
برسانید.

این یعنی مطمئن شوید که صفحات اسناد و قالب ها فقط شامل HTML هستند و HTML منحصرا 
برای شکل و ساختار مورد استفاده قرار گرفته است. هر چیزی که مربوط به شیوه ارائه و 
شکل و ظاهر است به style ها انتقال دهید و هر چیزی که مربوطه به رفتار است به 
script ها انتقال دهید.

به علاوه ناحیه تماس آنها را به حداقل برسانید و در حد لینک کردن چند style و script
در اسناد و قالب ها قراردهید.

جدا کردن ساختار ها و شیوه ارائه و رفتار ها به دلایل استفاده نگهداری بسیار مهم است
زیرا تغییر دادن یک سند HTML و قالب بسیار هزینه بر تر از بروزرسانی style ها و 
script هاست.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <!DOCTYPE html>
    <title>HTML sucks</title>
    <link rel="stylesheet" href="base.css" media="screen">
    <link rel="stylesheet" href="grid.css" media="screen">
    <link rel="stylesheet" href="print.css" media="print">
    <h1 style="font-size: 1em;">HTML sucks</h1>
    <p>I’ve read about this on a few sites but now I’m sure:
      <u>HTML is stupid!!1</u>
    <center>I can’t believe there’s no way to control the styling of
      my website without doing everything all over again!</center>

.. code-block::

    <!-- Recommended -->
    <!DOCTYPE html>
    <title>My first CSS-only redesign</title>
    <link rel="stylesheet" href="default.css">
    <h1>My first CSS-only redesign</h1>
    <p>I’ve read about this on a few sites but today I’m actually
      doing it: separating concerns and avoiding anything in the HTML of
      my website that is presentational.
    <p>It’s awesome!

1.6. Entity References
^^^^^^^^^^^^^^^^^^^^^^^^

از entity reference ها استفاده نکنید.

احتیاجی به استفاده از entity reference ها مثل ``&mdash;`` و ``&rdquo;`` و یا 
``&#x263a;`` نیست. فرض کنید برای همه فایل ها و ویرایشگر ها از یک encoding ثابت 
(UTF-8) استفاده شده است.

تنها استثنا برای کاراکتر هایی است که در HTML معنای خاصی دارند (مثل ``>`` و 
``&``) همچنین کنترل یا کاراکتر های غیر نمایشی (مثل no-break space).

.. code-block:: html
   :class: not-recommended

   <!-- Not recommended -->
    The currency symbol for the Euro is &ldquo;&eur;&rdquo;.

.. code-block:: html

    <!-- Recommended -->
    The currency symbol for the Euro is “€”.

1.7. تگ های اختیاری
^^^^^^^^^^^^^^^^^^^^^

تگ های اختیاری را حذف کنید.

برای بهینه کردن حجم فایل ها و بالا بردن خوانایی آنها، تگ های اختیاری را حذف کنید.
`HTML5 specification`_ تگ هایی را که قابل حذف هستند مشخص کرده است.

(این رویکرد نیاز به زمان زیادی دارد تا بعنوان یک راهنمای جامع به کاربرده شود 
زیرا به طور قابل توجهی با طرز فکر بسیاری از توسعه دهندگان وب متفاوت است).

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <!DOCTYPE html>
    <html>
      <head>
        <title>Spending money, spending bytes</title>
      </head>
      <body>
        <p>Sic.</p>
      </body>
    </html>

.. code-block:: html

    <!-- Recommended -->
    <!DOCTYPE html>
    <title>Saving money, saving bytes</title>
    <p>Qed.

1.8. ویژگی ``type``
^^^^^^^^^^^^^^^^^^^^^

ویژگی ``type`` را در style ها و script ها حذف کنید.

از ویژگی ``type`` برای style ها استفاده نکنید (مگر اینکه از CSS استفاده نمی 
کنید) و همچنین برای script ها هم از این ویژگی استفاده نکنید (مگر اینکه از 
Javascript استفاده نمی کنید).

استفاده از ویژگی ``type`` ضرورتی ندارد بر طبق HTML5 مقدار پیش فرض این ویژگی 
|text/css|_ و |text/javascript|_ است. این کار را می توانید با خیال راحت برای 
مرورگر های قدیمی تر هم انجام دهید.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <link rel="stylesheet" href="https://www.google.com/css/maia.css"
        type="text/css">

.. code-block: html

    <!-- Recommended -->
    <link rel="stylesheet" href="https://www.google.com/css/maia.css">

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <script src="https://www.google.com/js/gweb/analytics/autotrack.js"
        type="text/javascript"></script>

.. code-block:: html

    <!-- Recommended -->
    <script src="https://www.google.com/js/gweb/analytics/autotrack.js"></script>

2. قوانین قالب بندی HTML
--------------------------

2.1. قالب بندی عمومی
^^^^^^^^^^^^^^^^^^^^^^

از یک خط جدید برای هر بلاک، لیست، یا عنصر جدول استفاده کنید و همه برای همه عناصر
فرزند از کنگره ها (فضا های خالی برای مرتب سازی) استفاده کنید.

براساس style ای که عناصر دارند برای آنها کنگره بگذارید (CSS اجازه می دهد شیوه 
نمایش یک عنصر را با استفاده از ``display`` تغییر دهید)، هر بلاک، یا لیست، یا عنصر
جدول را در خط جدیدی قرار دهید.


همچنین آنها را جلوتر ببرید و کنگره دار کنید اگر درون یک لیست یا بلاک یا جدول قرار
گرفته اند.

(اگر شما به فضاهای خالی whitespace های اطراف آیتم های لیست مشکل دارید این قابل
قبول است که همه عناصر ``li`` را درون یک خط قرار دهید. برنامه هایی که این ها راجع
بررسی می کنند معمولا به جای خطا یک اخطار می دهند).

.. code-block:: html

    <blockquote>
      <p><em>Space</em>, the final frontier.</p>
    </blockquote>

.. code-block:: html

    <ul>
      <li>Moe
      <li>Larry
      <li>Curly
    </ul>

.. code-block:: html

    <table>
      <thead>
        <tr>
          <th scope="col">Income
          <th scope="col">Taxes
      <tbody>
        <tr>
          <td>$ 5.00
          <td>$ 4.50
    </table>


2.2. شکستن خطوط در HTML
^^^^^^^^^^^^^^^^^^^^^^^

خطوط طولانی را بشکنید. (اختیاری)

با اینکه در HTML محدودیت در تعداد کاراکتر های یک خط وجود ندارد اما ممکن است شما
بخواهید جهت افزایش خوانایی کد های آنها را به چند خط بشکنید.

وقتی یک خط شکسته می شود ادامه آن خط با چهار space قبل خود جلوتر از مکان واقعی خط
می ایستد و کنگره ایجاد می کند.

.. code-block:: html

    <md-progress-circular md-mode="indeterminate" class="md-accent"
        ng-show="ctrl.loading" md-diameter="35">
    </md-progress-circular>

.. code-block:: html

    <md-progress-circular
        md-mode="indeterminate"
        class="md-accent"
        ng-show="ctrl.loading"
        md-diameter="35">
    </md-progress-circular>

.. code-block:: html

    <md-progress-circular md-mode="indeterminate"
                          class="md-accent"
                          ng-show="ctrl.loading"
                          md-diameter="35">
    </md-progress-circular>

2.3. HTML Quotation Marks
^^^^^^^^^^^^^^^^^^^^^^^^^

وقتی ویژگی های یک عنصر HTML را مقدار دهی میکنید از double quotation استفاده 
کنید.

به جای استفاده از ``''``، از double quotation (``""``) در اطراف مقادیر ویژگی ها 
استفاده کنید.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <a class='maia-button maia-button-secondary'>Sign in</a>

.. code-block:: html

    <!-- Recommended -->
    <a class="maia-button maia-button-secondary">Sign in</a>


.. _W3C HTML validator: https://validator.w3.org/nu/
.. _HTML5 specification: https://html.spec.whatwg.org/multipage/syntax.html#syntax-tag-omission
.. |application/xhtml+xml| replace:: ``application/xhtml+xml``
.. _application/xhtml+xml: https://hixie.ch/advocacy/xhtml
.. |text/css| replace:: ``text/css``
.. _text/css: https://html.spec.whatwg.org/multipage/obsolete.html#attr-style-type
.. |text/javascript| replace:: ``text/javascript``
.. _text/javascript: https://html.spec.whatwg.org/multipage/scripting.html#attr-script-type