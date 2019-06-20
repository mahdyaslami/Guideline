HTML
====

:doc:`فارسی <html>`

1. HTML Style Rules
---------------------

1.1. Document Type
^^^^^^^^^^^^^^^^^^^^

Use HTML5.

HTML5 (HTML syntax) is preferred for all HTML documents: ``<!DOCTYPE html>``.

(It’s recommended to use HTML, as ``text/html``. Do not use XHTML. XHTML, as 
|application/xhtml+xml|_, lacks both browser and infrastructure support and 
offers less room for optimization than HTML.)

Although fine with HTML, do not close void elements, i.e. write ``<br>``, 
not ``<br />``.

1.2. HTML Validity
^^^^^^^^^^^^^^^^^^^^

Use valid HTML where possible.

Use valid HTML code unless that is not possible due to otherwise unattainable 
performance goals regarding file size.

Use tools such as the `W3C HTML validator`_ to test.

Using valid HTML is a measurable baseline quality attribute that contributes to 
learning about technical requirements and constraints, and that ensures proper 
HTML usage.

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

1.3. Semantics
^^^^^^^^^^^^^^^^

Use HTML according to its purpose.

Use elements (sometimes incorrectly called “tags”) for what they have been 
created for. For example, use heading elements for headings, ``p`` elements for 
paragraphs, ``a`` elements for anchors, etc.

Using HTML according to its purpose is important for accessibility, reuse, and 
code efficiency reasons.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <div onclick="goToRecommendations();">All recommendations</div>

.. code-block:: html

    <!-- Recommended -->
    <a href="recommendations/">All recommendations</a>

1.4. Multimedia Fallback
^^^^^^^^^^^^^^^^^^^^^^^^^^

Provide alternative contents for multimedia.

For multimedia, such as images, videos, animated objects via ``canvas``, make 
sure to offer alternative access. For images that means use of meaningful 
alternative text (``alt``) and for video and audio transcripts and captions, 
if available.

Providing alternative contents is important for accessibility reasons: A blind 
user has few cues to tell what an image is about without ``@alt``, and other 
users may have no way of understanding what video or audio contents are about 
either.

(For images whose ``alt`` attributes would introduce redundancy, and for images 
whose purpose is purely decorative which you cannot immediately use CSS for, use
no alternative text, as in ``alt=""``.)

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <img src="spreadsheet.png">

.. code-block:: html

    <!-- Recommended -->
    <img src="spreadsheet.png" alt="Spreadsheet screenshot.">

1.5. Separation of Concerns
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Separate structure from presentation from behavior.

Strictly keep structure (markup), presentation (styling), and behavior 
(scripting) apart, and try to keep the interaction between the three to an 
absolute minimum.

That is, make sure documents and templates contain only HTML and HTML that is 
solely serving structural purposes. Move everything presentational into style 
sheets, and everything behavioral into scripts.

In addition, keep the contact area as small as possible by linking as few style 
sheets and scripts as possible from documents and templates.

Separating structure from presentation from behavior is important for 
maintenance reasons. It is always more expensive to change HTML documents and 
templates than it is to update style sheets and scripts.

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

.. code-block:: html

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

Do not use entity references.

There is no need to use entity references like ``&mdash;``, ``&rdquo;``, or 
``&#x263a;``, assuming the same encoding (UTF-8) is used for files and editors 
as well as among teams.

The only exceptions apply to characters with special meaning in HTML (like ``<``
and ``&``) as well as control or “invisible” characters (like no-break spaces).

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    The currency symbol for the Euro is &ldquo;&eur;&rdquo;.

.. code-block:: html

    <!-- Recommended -->
    The currency symbol for the Euro is “€”.

1.7. Optional Tags
^^^^^^^^^^^^^^^^^^^^

Omit optional tags (optional).

For file size optimization and scannability purposes, consider omitting optional 
tags. The `HTML5 specification`_ defines what tags can be omitted.

(This approach may require a grace period to be established as a wider guideline 
as it’s significantly different from what web developers are typically taught. 
For consistency and simplicity reasons it’s best served omitting all optional 
tags, not just a selection.)

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

1.8. ``type`` Attributes
^^^^^^^^^^^^^^^^^^^^^^^^^^

Omit ``type`` attributes for style sheets and scripts.

Do not use ``type`` attributes for style sheets (unless not using CSS) and 
scripts (unless not using JavaScript).

Specifying ``type`` attributes in these contexts is not necessary as HTML5 
implies |text/css|_ and |text/javascript|_ as defaults. This can be safely 
done even for older browsers.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <link rel="stylesheet" href="https://www.google.com/css/maia.css"
        type="text/css">

.. code-block:: html

    <!-- Recommended -->
    <link rel="stylesheet" href="https://www.google.com/css/maia.css">

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <script src="https://www.google.com/js/gweb/analytics/autotrack.js"
        type="text/javascript"></script>

.. code-block::

    <!-- Recommended -->
    <script src="https://www.google.com/js/gweb/analytics/autotrack.js"></script>

2. HTML Formatting Rules
--------------------------

2.1. General Formatting
^^^^^^^^^^^^^^^^^^^^^^^^^

Use a new line for every block, list, or table element, and indent every such 
child element.

Independent of the styling of an element (as CSS allows elements to assume a 
different role per ``display`` property), put every block, list, or table 
element on a new line.

Also, indent them if they are child elements of a block, list, or table element.

(If you run into issues around whitespace between list items it’s acceptable to 
put all ``li`` elements in one line. A linter is encouraged to throw a warning 
instead of an error.)

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


2.2. HTML Line-Wrapping
^^^^^^^^^^^^^^^^^^^^^^^^^

Break long lines (optional).

While there is no column limit recommendation for HTML, you may consider 
wrapping long lines if it significantly improves readability.

When line-wrapping, each continuation line should be indented at least 4 
additional spaces from the original line.

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^

When quoting attributes values, use double quotation marks.

Use double (``""``) rather than single quotation marks (``''``) around attribute
values.

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