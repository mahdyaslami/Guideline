.. rst-class:: persian

قرارداد بزرگی و کوچکی حروف
===========================

:doc:`English <capitalization-conventions-en>`

این خط مشی ها در این فصل روشی را مطرح می کند که وقتی شما در یک نمونه کد به صورت
مداوم از آن استفاده کنید خواندن و درک نام نوع ها و اعضا و پارامتر ها برای شما 
راحت تر خواهد بود.

قوانین بزرگی و کوچکی حروف برای نام ها
---------------------------------------

برای متفاوت جلوه داده و قابل فهم کردن یک کلمه در یک نام حرف اول کلمه را با
حروف بزرگ بنویسید. در هیچ از زیر خط برای جدا کردن کردن کلمات و یا مهم نشان دادن 
آنها استفاده نکنید. دو راهکار مناسب برای بزرگ و کوچک کردن حروف یک نام وجود
دارد و استفاده از آن بسته به نوع آن مشخص دارد:

-  PascalCasing

-  camelCasing

قرارداد PascalCasing، برای همه نام ها از این قرارداد استفاده می شود به غیر از
نام پارامتر ها، حرف اول همه کلمات با حروف بزرگ و باقی حروف کلمات با حروف کوچک
(بزرگ نشان دادن حرف اول برای مخفف هایی با بیشتر از دو حرف هم به همین صورت است)،
همین طور که در مثال زیر نشان داده شده است:

| ``PropertyDescriptor``
| ``HtmlTag``

یک نمونه خاص که یک مخفف دو حرفی در ابتدای یک نام آمده است و ما هر دو حرف این 
مخفف را با حروف بزرگ می نویسیم، همان طور که در مثال زیر نمایش داده شده است:

``IOStream``

قرارداد camelCasing، تنها برای نام پارمتر ها استفاده می شود، حرف اول تمام کلمات
بزرگ نمایش داده می شوند به غیر از کلمه اول که همه حروف آن کوچک نمایش داده 
می شود. همین طور که در مثلا زیر می بینید حتی مخفف های با دو حرف طول هم با حروف
کوچک نمایش داده می شوند.

| ``propertyDescriptor``
| ``ioStream``
| ``htmlTag``

**✓ انجام دهید** از PascalCasing برای نام تمام اعضای عمومی public، انواع (type
ها) و فضاهای نامی (namespace ها) که از چندین کلمه تشکیل شده اند استفاده کنید.

**✓ انجام دهید** از camelCasing برای نام پارامتر ها استفاده کنید.

جدول زیر قوانین بزرگی و کوچکی حروف را در در انواع حالت های نام برای انواع 
مشخصه ها توصیف می کند.

.. rst-class:: ltr

+------------+--------+------------------------------------------------+
| Identifier | Casing | Example                                        |
+============+========+================================================+
| Namespace  | Pascal | ``namespace System.Security { ... }``          |
+------------+--------+------------------------------------------------+
| Type       | Pascal | ``public class StreamReader { ... }``          |
+------------+--------+------------------------------------------------+
| Interface  | Pascal | ``public interface IEnumerable { ... }``       |
+------------+--------+------------------------------------------------+
| Method     | Pascal | | ``public class Object {``                    |
|            |        | | ``public virtual string ToString();``        |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Property   | Pascal | | ``public class String {``                    |
|            |        | | ``public int Length { get; }``               |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Event      | Pascal | | ``public class Process {``                   |
|            |        | | ``public event EventHandler Exited;``        |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Field      | Pascal | | ``public class MessageQueue {``              |
|            |        | | ``public static readonly TimeSpan``          |
|            |        | | ``InfiniteTimeout;``                         |
|            |        | | ``}``                                        |
|            |        | | ``public struct UInt32 {``                   |
|            |        | | ``public const Min = 0;``                    |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Enum value | Pascal | | ``public enum FileMode {``                   |
|            |        | | ``Append,``                                  |
|            |        | | ``...``                                      |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Parameter  | Camel  | | ``public class Convert {``                   |
|            |        | | ``public static int ToInt32(string value);`` |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+

Capitalizing Compound Words and Common Terms
--------------------------------------------

Most compound terms are treated as single words for purposes of
capitalization.

**X DO NOT** capitalize each word in so-called closed-form compound
words.

These are compound words written as a single word, such as endpoint. For
the purpose of casing guidelines, treat a closed-form compound word as a
single word. Use a current dictionary to determine if a compound word is
written in closed form.

=============== =============== ======================
Pascal          Camel           Not
=============== =============== ======================
``BitFlag``     ``bitFlag``     ``Bitflag``
``Callback``    ``callback``    ``CallBack``
``Canceled``    ``canceled``    ``Cancelled``
``DoNot``       ``doNot``       ``Don't``
``Email``       ``email``       ``EMail``
``Endpoint``    ``endpoint``    ``EndPoint``
``FileName``    ``fileName``    ``Filename``
``Gridline``    ``gridline``    ``GridLine``
``Hashtable``   ``hashtable``   ``HashTable``
``Id``          ``id``          ``ID``
``Indexes``     ``indexes``     ``Indices``
``LogOff``      ``logOff``      ``LogOut``
``LogOn``       ``logOn``       ``LogIn``
``Metadata``    ``metadata``    ``MetaData, metaData``
``Multipanel``  ``multipanel``  ``MultiPanel``
``Multiview``   ``multiview``   ``MultiView``
``Namespace``   ``namespace``   ``NameSpace``
``Ok``          ``ok``          ``OK``
``Pi``          ``pi``          ``PI``
``Placeholder`` ``placeholder`` ``PlaceHolder``
``SignIn``      ``signIn``      ``SignOn``
``SignOut``     ``signOut``     ``SignOff``
``UserName``    ``userName``    ``Username``
``WhiteSpace``  ``whiteSpace``  ``Whitespace``
``Writable``    ``writable``    ``Writeable``
=============== =============== ======================

Case Sensitivity
----------------

Languages that can run on the CLR are not required to support
case-sensitivity, although some do. Even if your language supports it,
other languages that might access your framework do not. Any APIs that
are externally accessible, therefore, cannot rely on case alone to
distinguish between two names in the same context.

**X DO NOT** assume that all programming languages are case sensitive.
They are not. Names cannot differ by case alone.
