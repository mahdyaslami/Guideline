CSS
===

:doc:`فارسی <css>`

1. CSS Style Rules
--------------------

1.1. CSS Validity
^^^^^^^^^^^^^^^^^^^

Use valid CSS where possible.

Unless dealing with CSS validator bugs or requiring proprietary syntax, use 
valid CSS code.

Use tools such as the `W3C CSS validator`_ to test.

Using valid CSS is a measurable baseline quality attribute that allows to spot 
CSS code that may not have any effect and can be removed, and that ensures 
proper CSS usage.

1.2. ID and Class Naming
^^^^^^^^^^^^^^^^^^^^^^^^^^

Use meaningful or generic ID and class names.

Instead of presentational or cryptic names, always use ID and class names that 
reflect the purpose of the element in question, or that are otherwise generic.

Names that are specific and reflect the purpose of the element should be 
preferred as these are most understandable and the least likely to change.

Generic names are simply a fallback for elements that have no particular or no 
meaning different from their siblings. They are typically needed as “helpers.”

Using functional or generic names reduces the probability of unnecessary 
document or template changes.

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

1.3. ID and Class Name Style
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use ID and class names that are as short as possible but as long as necessary.

Try to convey what an ID or class is about while being as brief as possible.

Using ID and class names this way contributes to acceptable levels of 
understandability and code efficiency.

.. code-block:: css
   :class: not-recommended

    /* Not recommended */
    #navigation {}
    .atr {}

.. code-block:: css

    /* Recommended */
    #nav {}
    .author {}

1.4. Type Selectors
^^^^^^^^^^^^^^^^^^^^^

Avoid qualifying ID and class names with type selectors.

Unless necessary (for example with helper classes), do not use element names 
in conjunction with IDs or classes.

Avoiding unnecessary ancestor selectors is useful for `performance reasons`_.

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use shorthand properties where possible.

CSS offers a variety of `shorthand`_ properties (like font) that should be used 
whenever possible, even in cases where only one value is explicitly set.

Using shorthand properties is useful for code efficiency and understandability.

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

1.6. 0 and Units
^^^^^^^^^^^^^^^^^^

Omit unit specification after “0” values, unless required.

Do not use units after ``0`` values unless they are required.

.. code-block:: css

    flex: 0px; /* This flex-basis component requires a unit. */
    flex: 1 1 0px; /* Not ambiguous without the unit, but needed in IE11. */
    margin: 0;
    padding: 0;

1.7. Leading 0s
^^^^^^^^^^^^^^^^^

Omit leading “0”s in values.

Do not put ``0`` s in front of values or lengths between -1 and 1.

.. code-block:: css

    font-size: .8em;

1.8. Hexadecimal Notation
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use 3 character hexadecimal notation where possible.

For color values that permit it, 3 character hexadecimal notation is shorter and 
more succinct.

.. code-block:: css

    /* Not recommended */
    color: #eebbcc;

    /* Recommended */
    color: #ebc;

1.9. Prefixes
^^^^^^^^^^^^^^^

Prefix selectors with an application-specific prefix (optional).

In large projects as well as for code that gets embedded in other projects or on 
external sites use prefixes (as namespaces) for ID and class names. Use short, 
unique identifiers followed by a dash.

Using namespaces helps preventing naming conflicts and can make maintenance 
easier, for example in search and replace operations.

.. code-block:: css

    .adw-help {} /* AdWords */
    #maia-note {} /* Maia */

1.10 ID and Class Name Delimiters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Separate words in ID and class names by a hyphen.

Do not concatenate words and abbreviations in selectors by any characters 
(including none at all) other than hyphens, in order to improve understanding 
and scannability.

.. code-block:: css

    /* Not recommended: does not separate the words “demo” and “image” */
    .demoimage {}

    /* Not recommended: uses underscore instead of hyphen */
    .error_status {}

    /* Recommended */
    #video-id {}
    .ads-sample {}

1.11 Hacks
^^^^^^^^^^^^^
Avoid user agent detection as well as CSS “hacks”—try a different approach 
first.

It’s tempting to address styling differences over user agent detection or 
special CSS filters, workarounds, and hacks. Both approaches should be 
considered last resort in order to achieve and maintain an efficient and 
manageable code base. Put another way, giving detection and hacks a free pass 
will hurt projects in the long run as projects tend to take the way of least 
resistance. That is, allowing and making it easy to use detection and hacks 
means using detection and hacks more frequently—and more frequently is too 
frequently.

2. CSS Formatting Rules
-------------------------

2.1. Declaration Order
^^^^^^^^^^^^^^^^^^^^^^^^
Alphabetize declarations.

Put declarations in alphabetical order in order to achieve consistent code in a 
way that is easy to remember and maintain.

Ignore vendor-specific prefixes for sorting purposes. However, multiple 
vendor-specific prefixes for a certain CSS property should be kept sorted 
(e.g. -moz prefix comes before -webkit).

.. code-block:: css

    background: fuchsia;
    border: 1px solid;
    -moz-border-radius: 4px;
    -webkit-border-radius: 4px;
    border-radius: 4px;
    color: black;
    text-align: center;
    text-indent: 2em;

2.2. Block Content Indentation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Indent all block content.

Indent all `block content`_, that is rules within rules as well as declarations, so 
to reflect hierarchy and improve understanding.

.. code-block:: css

    @media screen, projection {

      html {
        background: #fff;
        color: #444;
      }

    }

2.3. Declaration Stops
^^^^^^^^^^^^^^^^^^^^^^^^

Use a semicolon after every declaration.

End every declaration with a semicolon for consistency and extensibility 
reasons.

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

2.4. Property Name Stops
^^^^^^^^^^^^^^^^^^^^^^^^^^

Use a space after a property name’s colon.

Always use a single space between property and value (but no space between 
property and colon) for consistency reasons.

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

2.5. Declaration Block Separation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use a space between the last selector and the declaration block.

Always use a single space between the last selector and the opening brace that 
begins the `declaration block`_.

The opening brace should be on the same line as the last selector in a given rule.

.. code-block:: css
   :class: not-implemented

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

2.6. Selector and Declaration Separation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Separate selectors and declarations by new lines.

Always start a new line for each selector and declaration.

.. code-block:: css
   :class: not-implemented

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

2.7. Rule Separation
^^^^^^^^^^^^^^^^^^^^^^

Separate rules by new lines.

Always put a blank line (two line breaks) between rules.

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

Use single (``''``) rather than double (``""``) quotation marks for attribute 
selectors and property values.

Do not use quotation marks in URI values (``url()``).

Exception: If you do need to use the ``@charset`` rule, use double quotation 
marks—`single quotation marks are not permitted`_.

.. code-block:: css
   :class: not-implemented

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

3. CSS Meta Rules
-------------------

3.1. Section Comments
^^^^^^^^^^^^^^^^^^^^^^^

Group sections by a section comment (optional).

If possible, group style sheet sections together by using comments. Separate 
sections with new lines.

.. code-block:: css

    /* Header */

    #adw-header {}

    /* Footer */

    #adw-footer {}

    /* Gallery */

    .adw-gallery {}


.. _W3C CSS validator: https://jigsaw.w3.org/css-validator/
.. _performance reasons: http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/
.. _shorthand: https://www.w3.org/TR/CSS21/about.html#shorthand
.. _block content: https://www.w3.org/TR/CSS21/syndata.html#block
.. _declaration block: https://www.w3.org/TR/CSS21/syndata.html#rule-sets
.. _single quotation marks are not permitted: https://www.w3.org/TR/CSS21/syndata.html#charset