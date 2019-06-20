General
=======

:doc:`فارسی <general>`

1. General Style Rules
------------------------

1.1. Protocol
^^^^^^^^^^^^^^^^

Use HTTPS for embedded resources where possible.

Always use HTTPS (``https:``) for images and other media files, style sheets, and 
scripts, unless the respective files are not available over HTTPS.

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

2. General Formatting Rules
-----------------------------

2.1. Indentation
^^^^^^^^^^^^^^^^^^

Indent by 2 spaces at a time.

Don’t use tabs or mix tabs and spaces for indentation.

.. code-block:: html

    <ul>
      <li>Fantastic
      <li>Great
    </ul>


.. code-block:: css

    .example {
      color: blue;
    }


2.2. Capitalization
^^^^^^^^^^^^^^^^^^^^^

Use only lowercase.

All code has to be lowercase: This applies to HTML element names, attributes, 
attribute values (unless ``text/CDATA``), CSS selectors, properties, and property 
values (with the exception of strings).

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

2.3. Trailing Whitespace
^^^^^^^^^^^^^^^^^^^^^^^^^^

Remove trailing white spaces.

Trailing white spaces are unnecessary and can complicate diffs.

.. code-block:: html
   :class: not-recommended

    <!-- Not recommended -->
    <p>What?_

.. code-block:: html

    <!-- Recommended -->
    <p>Yes please.

3. General Meta Rules
-----------------------

3.1. Encoding
^^^^^^^^^^^^^^^

Use UTF-8 (no BOM).

Make sure your editor uses UTF-8 as character encoding, without a byte order 
mark.

Specify the encoding in HTML templates and documents via 
``<meta charset="utf-8">``. Do not specify the encoding of style sheets as these
assume UTF-8.

(More on encodings and when and how to specify them can be found in 
`Handling character encodings in HTML and CSS`_.)

3.2. Comments
^^^^^^^^^^^^^^^

Explain code as needed, where possible.

Use comments to explain code: What does it cover, what purpose does it serve, 
why is respective solution used or preferred?

(This item is optional as it is not deemed a realistic expectation to always 
demand fully documented code. Mileage may vary heavily for HTML and CSS code and
depends on the project’s complexity.)

3.3. Action Items
^^^^^^^^^^^^^^^^^^^

Mark todos and action items with ``TODO``.

Highlight todos by using the keyword ``TODO`` only, not other common formats 
like ``@@``.

Append a contact (username or mailing list) in parentheses as with the format 
``TODO(contact)``.

Append action items after a colon as in ``TODO: action item``.

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
