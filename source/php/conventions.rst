.. rst-class:: persian

قرارداد ها
==========

:doc:`English <conventions-en>`

1. مقدمه
--------

#. در بخش :doc:`standards` به توصیف استاندارد کد نویسی برای یک پروژه PHP 
   پرداختیم. اما در این بخش استاندارد ها و قرار داد های کد نویسی رو بررسی می 
   کنیم که به ما کمک می کنه تا یک پروژه با چهار چوب محکم و قابل پیش بینی و فهم
   داشته باشیم.

2. نام متد ها
-------------

#. وقتی یک شیء ارتباطات اصلی و با بقیه چیز ها (اشیاء، پارمتر ها، ...) دارد نام 
   متد ها و توابع باید به شیوه مناسبی اصلاح شود:

    #. ``get()``
    #. ``set()``
    #. ``has()``
    #. ``all()``
    #. ``replace()``
    #. ``remove()``
    #. ``clear()``
    #. ``isEmpty()``
    #. ``add()``
    #. ``register()``
    #. ``count()``
    #. ``keys()``

#. تنها زمانی از این متد ها استفاده کنید که مطمئن باشید که یک ارتباط اصلی و کلی
   وجود دارد:

    #. یک ``CookieJar`` تعداد زیادی ``Cookie`` دارد؛

    #. برای خیلی از روابط که این قرارداد جوابگو نیست، متد های زیر میتواند مورد 
       استفاده قرار بگیرد (به جای ``XXX`` نام رابطه را استفاده کنید):

+----------------+-------------------+
| Main Relation  | Other Relations   |
+================+===================+
| ``get()``      | ``getXXX()``      |
+----------------+-------------------+
| ``set()``      | ``setXXX()``      |
+----------------+-------------------+
| n/a            | ``replaceXXX()``  |
+----------------+-------------------+
| ``has()``      | ``hasXXX()``      |
+----------------+-------------------+
| ``all()``      | ``getXXXs()``     |
+----------------+-------------------+
| ``replace()``  | ``setXXXs()``     |
+----------------+-------------------+
| ``remove()``   | ``removeXXX()``   |
+----------------+-------------------+
| ``clear()``    | ``clearXXX()``    |
+----------------+-------------------+
| ``isEmpty()``  | ``isEmptyXXX()``  |
+----------------+-------------------+
| ``add()``      | ``addXXX()``      |
+----------------+-------------------+
| ``register()`` | ``registerXXX()`` |
+----------------+-------------------+
| ``count()``    | ``countXXX()``    |
+----------------+-------------------+
| ``keys()``     | n/a               |
+----------------+-------------------+


.. note:: 
    از انجایی که ``setXXX`` و ``replaceXXX`` خیلی شبیه هستند، یک نکته راجع به 
    تفات آنها وجود دارد که قابل توجه است. متد ``setXXX`` ممکن هست یک مقدار رو 
    جایگزین کند و یا یک عنصر جدید به رابطه اضافه کند. از طرف دیگر ``replaceXXX``
    نمی تواند عنصر جدید اضافه کند و در صورتی که کلیدی که به ``replaceXXX`` داده
    شد اشتباه باشد باید یک استثنا پرتاب بشود.

.. _php-conventions-deprecations:

3. منسوخ شده ها
---------------

#. در طول زمان بعضی کلاس ها و یا متد ها درون پروژه ممکن است منسوخ شوند؛ این حالت 
   زمانی اتفاق می افتد که می خواهید یک ویژگی جدید به سیستم خود اضافه کنید اما به
   خاطر مشکل عدم سازگاری با پشت زمینه کد شما امکان تغییر وجود ندارد، اما در عین 
   حال شما قصد رسیدن به یک ساختار سازگار تر و دارید که در این وضعیت پیاده سازی 
   های قدیم شما **منسوخ** خواهند شد.

#. وقتی که تگ ``@deprecated`` به توضیحات یک عنصر اضافه شود آن عنصر منسوخ شده است
   که می تواند یک کلاس، یک متد و یا یک پراپرتی باشد:

.. code-block:: php

    <?php
    
    /**
     * @deprecated since vendor-name/package-name 2.8, to be removed in 3.0. Use
     * XXX instead.
     */

#. پیام منسوخ شدن باید شامل شماره نسخه این که در آن کلاس یا متد مورد نظر منسوخ 
   شده است باشد و همچنین شماره نسخه ای که در آن عنصر مورد نظر حذف خواهد شد به 
   علاوه اگر ممکن باشد باید ویژگی جدیدی که جایگزین آن شده است هم معرفی بشود.

#. همیشه باید یک خطای ``E_USER_DEPRECATED`` شلیک شود تا کاربران بدانند که در یک
   یا دو نسخه دیگر تغییرات صورت خواهد گرفت و قبل از اینکه تغییرات صورت بگیرد از
   ویژگی های جدید استفاده کند (البته بستگی به حیاتی بودن تغییرات دارد):
   
.. code-block:: php

    <?php
    
    @trigger_error('XXX() is deprecated since vendor-name/package-name 2.8 and
    will be removed in 3.0. Use XXX instead.', E_USER_DEPRECATED);

#. بدون `عملگر سکوت @`_، کاربر ها نمی توانند خطا هایی که به منسوخ شدن ارتباط 
   دارد را رد کنند. بی صدا کردن این خطا ها به کاربر اجازه می دهد که این انتخاب 
   را داشته باشد و هر زمانی که مناسب بود تغییرات برای مهاجرت به ویژگی های جدید 
   را انجام بدهد. (شما می تواند این کار رو با اضافه کردن یک مدیریت کننده خطا مثل
   آن چیزی که در Web Debug Toolbar با استفاده از PHPUnit bridge انجام گرفته است 
   انجام دهید).

#. وقتی که کل یک کلاس منسوخ می شود ``trigger_error()`` باید بین تعریف کلاس و فضای 
   نامی قرار بگیرد شبیه این مورد مثال `ArrayParserCache`_:

.. code-block:: php

    <?php

    namespace Symfony\Component\ExpressionLanguage\ParserCache;

    @trigger_error('The '.__NAMESPACE__.'\ArrayParserCache class is deprecated
    since version 3.2 and will be removed in 4.0. Use the
    Symfony\Component\Cache\Adapter\ArrayAdapter class instead.', E_USER_DEPRECATED);

    use Symfony\Component\ExpressionLanguage\ParsedExpression;

    /**
    * @author Adrien Brault <adrien.brault@gmail.com>
    *
    * @deprecated ArrayParserCache class is deprecated since version 3.2 and
    * will be removed in 4.0. Use the Symfony\Component\Cache\Adapter\ArrayAdapter
    * class instead.
    */
    class ArrayParserCache implements ParserCacheInterface

.. _عملگر سکوت @: https://php.net/manual/en/language.operators.errorcontrol.php
.. _ArrayParserCache: https://github.com/symfony/symfony/blob/3.2/src/Symfony/Component/ExpressionLanguage/ParserCache/ArrayParserCache.php

.. rubric:: منابع

`symfony coding convention <https://github.com/symfony/symfony-docs/blob/master/contributing/code/conventions.rst>`_