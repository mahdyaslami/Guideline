.. rst-class:: persian

کلیات
=====

:doc:`English <general-en>`

1. قوانین کلی شکل کد
----------------------

1.1. پروتکل
^^^^^^^^^^^^^

تا جایی که امکان دارد از پروتکل HTTPS برای بکار بردن و بهره بردن از منابع 
استفاده کنید.

همیشه از HTTPS (``https:``) برای بکار بردن عکس ها، فیلم ها و صدا ها و فایل های
رسانه ای، style ها، و script ها استفاده کنید.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended: omits the protocol -->
    <script src="//ajax.googleapis.com/ajax/libs/jquery/3.4.0/jquery.min.js"></script>

    <!-- Not recommended: uses HTTP -->
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/3.4.0/jquery.min.js"></script>

.. code-block:: html

    <!-- Recommended -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.0/jquery.min.js"></script>


.. code-block:: css
   :class: not-recommended

    /* Not recommended: omits the protocol */
    @import '//fonts.googleapis.com/css?family=Open+Sans';

    /* Not recommended: uses HTTP */
    @import 'http://fonts.googleapis.com/css?family=Open+Sans';

.. code-block:: css

    /* Recommended */
    @import 'https://fonts.googleapis.com/css?family=Open+Sans';

2. قوانین عمومی قالب بندی
---------------------------

2.1. فضاهای خالی
^^^^^^^^^^^^^^^^^^

برای ایجاد فضاهای خالی در مرتب کردن کد ها به اصطلاح کنگره ها از دو space استفاده
کنید.

از tab و یا ترکیب tab و space در ایجاد کنگره ها استفاده نکنید.

.. code-block:: html

    <ul>
      <li>Fantastic
      <li>Great
    </ul>


.. code-block:: css

    .example {
      color: blue;
    }


2.2. بزرگی و کوچکی حروف
^^^^^^^^^^^^^^^^^^^^^^^^^

همیشه از حروف کوچک استفاده کنید.

تمام کد باید با حروف کوچک باشد: این قانون روی نام همه عناصر HTML، همه attribute 
ها و مقادیر آنها (بغیر از ``text/CDATA``)، CSS selector ها، همه پراپرتی ها و 
مقادیر آنها (به استثنای متونی که درون فایل می نویسیم) اعمال می شود.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <A HREF="/">Home</A>

.. code-block:: html

    <!-- Recommended -->
    <img src="google.png" alt="Google">


.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    color: #E5E5E5;

.. code-block:: css

    /* Recommended */
    color: #e5e5e5;

2.3. پشت سرهم آوردن فضا های خالی
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

فضا های خالی (whitespace) هایی که پشت سر هم آورده شده اند را حذف کنید.

فضا های خالی پشت سر هم ضرورتی ندارند و فقط بررسی تفاوت فایل را دشوار می کنند.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <p>What?_

.. code-block:: html

    <!-- Recommended -->
    <p>Yes please.

3. قوانین کلی در Meta
-----------------------

3.1. Encoding
^^^^^^^^^^^^^^^

همیشه از UTF-8 (no BOM) استفاده کنید.

مطمئن شوید که ویرایشگر شما از UTF8 (without a byte order mark - BOM) پشتیبانی 
می کند.

این encoding را در فایل های HTML و مستندات از طریق ``<meta charset="utf-8">``
انجام دهید. دقت کنید برای هیچ فایل CSS ای encoding مشخص نکنید و فرض را بر این 
قرار دهید که از UTF8 استفاده می کند.

(می توانید اطلاعات بیشتری راجع به مشخص کردن encoding فایل ها در لینک 
`Handling character encodings in HTML and CSS`_ مشاهده کنید.)

3.2. توضیحات
^^^^^^^^^^^^^^

تا جایی که احتیاح هست و هرجایی که ممکن هست کد ها را توضیح دهید.

از توضیحات برای شرح دادن کد ها استفاده کنید: چه چیزی را پوشش می دهند، برای چه 
کاری نوشته شده اند، چرا این راه حل استفاده شده یا به راه حل های دیگر ترجیح داده
شده.

(نوشتن توضیحات اختیاری است و این یک انتظار واقع گرایانه نیست که همیشه یک کد پر 
از توضیحات داشته باشیم، توضیحات نوشته شده در HTML و CSS می تواند بسیار متفاوت
باشد و این کاملا بستگی به پیچیدگی پروژه دارد).

3.3. عنصر های اجرایی
^^^^^^^^^^^^^^^^^^^^^^

کارهایی که باید انجام گیرد و عنصر های اجرایی و عملی را با ``TODO`` علامت بگذارید.

کارهایی که باید انجام گیرد را با ``TODO`` مشخص کنید و از شکل های متداول دیگر 
استفاده نکنید مثل ``@@``.

اطلاعات مخاطب را هم داخل پرانتز اضافه کنید (نام کاربری یا ایمیل - رایانامه) به
شکل ``TODO(contact)``.

عناصر و اطلاعات اجرایی را بعد از دو نقطه قرار دهید ``TODO: action item``.

.. code-block:: html

    {# TODO(john.doe): revisit centering #}
    <center>Test</center>

.. code-block:: html

    <!-- TODO: remove optional tags -->
    <ul>
      <li>Apples</li>
      <li>Oranges</li>
    </ul>

.. _Handling character encodings in HTML and CSS: https://www.w3.org/International/tutorials/tutorial-char-enc/
