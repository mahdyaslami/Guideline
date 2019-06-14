.. rst-class:: persian

استاندارد کد نویسی
******************

:doc:`English <standards-en>`

1. مقدمه
========

#. این استاندارد کد نویسی بر پایه استاندارد های `PSR-1`_، `PSR-2`_ و `PSR-4`_، 
   بنابراین بهتر هست که از آنها آگاهی داشته باشید.

2. هماهنگ کردن کد هایتان با استاندارد کد نویسی
==============================================

#. به غیر از بررسی کردن کد ها به صورت چشمی، سیمفونی یک راهکار ساده تر برای اینکه 
   از استاندارد بودن کد های خودتان مطمئن شوید ارائه داده است. اول ابزار
   `PHP CS Fixer`_ را نصب کنید و بعد دستورات زیر را اجرا کنید تا همه چیز 
   درست بشود:
   
.. code-block:: none

    $ cd your-project/
    $ php php-cs-fixer.phar fix -v

3. جزئیات استاندارد کد نویسی
============================

#. یک مثال کوتاه شامل بیشتر ویژگی هایی که در زیر توصیف شده است:

.. code-block:: php
    
    <?php
    
    /*
    * This file is part of the Symfony package.
    *
    * (c) Fabien Potencier <fabien@symfony.com>
    *
    * For the full copyright and license information, please view the LICENSE
    * file that was distributed with this source code.
    */

    namespace Acme;

    /**
    * Coding standards demonstration.
    */
    class FooBar
    {
       /**
        * This part is description about this constant. it isn't in orginal
        * document but i think it's neccesary.
        */
       const SOME_CONST = 42;

       /**
        * This part is description about this property. it isn't in orginal
        * document but i think it's neccesary.
        *
        * @var string
        */
       private $fooBar;

       /**
        * @param string $dummy Some argument description
        */
       public function __construct($dummy)
       {
           $this->fooBar = $this->transformText($dummy);
       }

       /**
        * @return string
        *
        * @deprecated
        */
       public function someDeprecatedMethod()
       {
           @trigger_error(sprintf(
               'The %s() method is deprecated since vendor-name/package-name 2.8 and will be removed in 3.0. Use Acme\Baz::someMethod() instead.',
               __METHOD__), E_USER_DEPRECATED);

           return Baz::someMethod();
       }

       /**
        * Transforms the input given as first argument.
        *
        * @param bool|string $dummy   Some argument description
        * @param array       $options An options collection to be used within the
        * transformation
        *
        * @return string|null The transformed input
        *
        * @throws \RuntimeException When an invalid option is provided
        */
       private function transformText($dummy, array $options = [])
       {
           $defaultOptions = [
               'some_default' => 'values',
               'another_default' => 'more values',
           ];

           foreach ($options as $option) {
               if (!in_array($option, $defaultOptions)) {
                   throw new \RuntimeException(sprintf(
                       'Unrecognized option "%s"', $option));
               }
           }

           $mergedOptions = array_merge(
               $defaultOptions,
               $options
           );

           if (true === $dummy) {
               return null;
           }

           if ('string' === $dummy) {
               if ('values' === $mergedOptions['some_default']) {
                   return substr($dummy, 0, 5);
               }

               return ucwords($dummy);
           }
       }

       /**
        * Performs some basic check for a given value.
        *
        * @param mixed $value     Some value to check against
        * @param bool  $theSwitch Some switch to control the method's flow
        *
        * @return bool|void The resultant check if $theSwitch isn't false, void
        * otherwise
        */
       private function reverseBoolean($value = null, $theSwitch = false)
       {
           if (!$theSwitch) {
               return;
           }

           return !$value;
       }
    }

3.2. ساختار
-----------

#. اضافه کردن یک space بعد از هر ویرگول (کاما)؛

#. اضافه کردن یک space قبل و بعد از هر عملگر دو دویی (``==``, ``&&``, ...)؛

#. قراردادن عملگر های یگانه (``!``, ``--``, ...) دقیقا چسبیده به متغیری که متاثر
   از آنها هست؛

#. همیشه از مقایسه ها و تطبیق های برابری `identical comparison`_ (``===``, ...) 
   استفاده کنید در غیر این صورت این موضوع دچار سردرگمی شما خواهد شد؛

#. از `Yoda conditions`_ () برای مقایسه یک متغیر با یک عبارت استفاده کنید تا از 
   اشتباه رایج مقدار دهی درون شرطها جلوگیری شود (برای عملگر های ``==``، ``!=``،
   ``===`` و ``!==`` از این شیوه استفاده کنید)؛

.. note::
    
    `Yoda conditions`_ به یک شیوه نوشتن شرط گفته می شود که در آن عبارت ثابت شرط
    در ابتدای شرط می آید و متغیر در انتها مثل::
    
        if ("42" === $variable)

#. یک ویرگول (comma) بعد از هر عنصر در تعریف یا استفاده از آرایه های در چند خط 
   قرار دهید حتی بعد از اخرین عنصر آرایه؛

#. بعد از هر خط ``return`` یک خط خالی قرار دهید. مگر اینکه ``return`` داخل یک 
   آکلاد یا یک خالی باشد مثل یک ``if``؛

.. code-block:: php

    <?php

    if ($condition)
    {
        return $value;
    }

    if ($condition)
    {
        /*
         * statements
         */

        return $value;

    }

#. از ``return null;`` وقتی استفاده کنید که تابع شما صریحا و به وضوح ``null``
   برگرداند و از ``return;`` وقتی استفاده کنید که تابع شما باید ``void`` 
   برگرداند؛

#. از پرانتز برای مشخص کردن ساختار های کنترلی استفاده کنید صرف نظر از تعداد 
   عبارت های تشکیل دهند آنها؛
   
#. درون هر فایل فقط یک کلاس تعریف شود - البته این کار شامل کلاس هایی که قرار نیست
   بیرون از این فایل مورد استفاده قرار گیرند نمی شود و آن کلاس ها مورد توجه
   استاندارد های `PSR-0`_ و `PSR-4`_ قرار نمی گیرد؛

#. تعریف ارث بری یک کلاس و نام تمام interface ها و class هایی که از آنها ارث می
   می برد را درون یک خط قرار بدهید؛

#. پراپرتی های کلاس ها را قبل از توابع آن تعریف کنید؛

#. ابتدا متد ها و توابع عمومی public را تعریف کنید سپس آنهایی که محافظت شده
   هستند protected و در نهایت متد های خصوص private. استثنا برای این قانون سازنده
   کلاس ها constructors و متد های ``setUp()`` و ``tearDown()`` در تست های PHPUnit
   هستند همیشه باید اول تعریف شوند تا خوانایی برنامه افزایش پیدا کند.

#. همه آرگومان های یک تابع یا متد را درون خطی که نام متد یا تابع قرار دارد تعریف
   کنید هیچ اهمیتی ندارد که چند آرگومان وجود دارد؛

#. در ساختن یک شیء از یک کلاس حتما از پرانتز استفاده کنید صرف نظر از تعداد
   آرگومان هایی که سازنده ها می گیرند؛
   
#. Exception ها و متن پیام های خطا باید با استفاده از تابع ``sprintf`` به هم
   متصل شوند.

#. صدا زدن ``trigger_error`` با نوع ``E_USER_DEPRECATED`` حتما باید از طریق
   عملگر ``@`` انجام گیرد. برای اطلاعات بیشتر 
   :ref:`منسوخ شده ها <contributing-code-conventions-deprecations>` را بخوانید؛

#. بعد از ``if`` ها و ``case`` هایی که مقداری بر می گردانند یا خطایی پرتاب می 
   کنند از ``else``، ``elseif`` و ``break`` استفاده نکنید.

#. در هنگام گرفتن مقادیر یک آرایه وقتی از براکت باز و بسته ``[]`` استفاده میکنیم
   نباید قبل و بعد از براکت ها space یا بگذاریم یا آنها را در چند خط تعریف کنیم؛

#. برای هر کلاسی که عضوی از فضای نامیه عمومی (global namespace) نیست از ``use``
   استفاده کنید؛

#. وقتی که تگ های PHPDoc مثل ``@param`` یا ``@return`` شامل ``null`` هستند، 
   همیشه ``null`` ها را در آخر لیست قرار دهید.
   
3.3. قرارداد های نام گذاری
--------------------------

#. از قرارداد نوشتاری `camelCase`_ برای نام متغیر ها، توابع و متد ها و آرگومان
   ها استفاده کنید (``$acceptableContentTypes``, ``hasSession()``)؛

#. از قرارداد نوشتاری `snake_case`_ پارامتر های تنظیمات و متغیر های Twig استفاده
   کنید (``framework.csrf_protection``, ``http_status_code``)؛

#. Use namespaces for all PHP classes and `UpperCamelCase`_ for
   their names (e.g. ``ConsoleLogger``);

#. برای نام namespace ها و همه کلاس ها در PHP از `UpperCamelCase`_ یا همان 
   Pascal Casing استفاده کنید (e.g. ``ConsoleLogger``)؛

#. همه کلاس های انتزاعی abstract با پیشوند ``Abstract`` شروع می شوند به استثنای
   PHPUnit ``*TestCase``؛

#. همه interface ها با پسوند ``Interface`` تمام می شوند؛

#. همه trait ها با پسوند ``Trait`` تمام می شوند؛

#. همه exception ها با پسوند ``Exception`` تمام می شوند؛

#. از قرارداد نوشتاری `UpperCamelCase`_ برای نام گذاری فایل های PHP استفاده می
   کنیم (``EnvVarProcessor.php``) و از قرار داد نوشتاری `snake_case`_ برای نام
   گذاری Twig template ها و همچنین asset ها؛

#. برای اشاره کردن به نوع داده ها در PHPDocs و تبدیل نوع ها، از ``bool`` به جای
   (``boolean`` یا ``Boolean``) استفاده کنید، از ``int`` به جای (``integer``)،
   از ``float`` به جای (``double`` یا ``real``)؛

#. فراموش نکنید که برای اینکه یک نگاه عمیق تر به نام گذاری داشته باشید به 
   :ref:`conventions` مراجعه کنید؛

3.4. Service Naming Conventions
-------------------------------

#. A service name must be the same as the fully qualified class name
   (FQCN) of its class (e.g. ``App\EventSubscriber\UserSubscriber``);

#. If there are multiple services for the same class, use the FQCN
   for the main service and use lowercased and underscored names for the rest of
   services. Optionally divide them in groups separated with dots (e.g.
   ``something.service_name``, ``fos_user.something.service_name``);

#. Use lowercase letters for parameter names (except when referring
   to environment variables with the ``%env(VARIABLE_NAME)%`` syntax);

#. Add class aliases for public services (e.g. alias
   ``Symfony\Component\Something\ClassName`` to ``something.service_name``).

3.5. Documentation
------------------

#. Add PHPDoc blocks for all classes, methods, and functions (though
   you may be asked to remove PHPDoc that do not add value);

#. Group annotations together so that annotations of the same type
   immediately follow each other, and annotations of a different type are
   separated by a single blank line;

#. Omit the ``@return`` tag if the method does not return anything;

#. The ``@package`` and ``@subpackage`` annotations are not used;

#. Don't inline PHPDoc blocks, even when they contain just one tag
   (e.g. don't put ``/** {@inheritdoc} */`` in a single line);

#. When adding a new class or when making significant changes to an
   existing class, an ``@author`` tag with personal contact information may be
   added, or expanded. Please note it is possible to have the personal contact
   information updated or removed per request to the
   doc:`core team </contributing/code/core_team>`.

3.6. License
------------

#. Symfony is released under the MIT license, and the license block
   has to be present at the top of every PHP file, before the namespace.

.. rubric:: References

`symfony coding standards <https://github.com/symfony/symfony-docs/blob/master/contributing/code/standards.rst>`_

.. _PHP CS Fixer: https://cs.symfony.com/
.. _PSR-0: https://www.php-fig.org/psr/psr-0/
.. _PSR-1: https://www.php-fig.org/psr/psr-1/
.. _PSR-2: https://www.php-fig.org/psr/psr-2/
.. _PSR-4: https://www.php-fig.org/psr/psr-4/
.. _identical comparison: https://php.net/manual/en/language.operators.comparison.php
.. _Yoda conditions: https://en.wikipedia.org/wiki/Yoda_conditions
.. _camelCase: https://en.wikipedia.org/wiki/Camel_case
.. _UpperCamelCase: https://en.wikipedia.org/wiki/Camel_case
.. _snake_case: https://en.wikipedia.org/wiki/Snake_case