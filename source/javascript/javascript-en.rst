Javascript
==========

1. Introduction
---------------

This document serves as the complete definition of Google's coding standards for 
source code in the Java™ Programming Language. A Java source file is described 
as being in Google Style if and only if it adheres to the rules herein.

Like other programming style guides, the issues covered span not only aesthetic 
issues of formatting, but other types of conventions or coding standards as 
well. However, this document focuses primarily on the hard-and-fast rules that 
we follow universally, and avoids giving advice that isn't clearly enforceable 
(whether by human or tool).

1.1. Terminology notes
^^^^^^^^^^^^^^^^^^^^^^

In this document, unless otherwise clarified:

The term class is used inclusively to mean an "ordinary" class, enum class, 
interface or annotation type (@interface).

The term member (of a class) is used inclusively to mean a nested class, field, 
method, or constructor; that is, all top-level contents of a class except 
initializers and comments.

This Style Guide uses `RFC 2119`_ terminology when using the phrases must, must 
not, should, should not, and may. The terms prefer and avoid correspond to 
should and should not, respectively. Imperative and declarative statements are 
prescriptive and correspond to must.

1.2. Guide notes
^^^^^^^^^^^^^^^^

Example code in this document is non-normative. That is, while the examples are 
in Google Style, they may not illustrate the only stylish way to represent the 
code. Optional formatting choices made in examples should not be enforced as 
rules.

.. toctree:: 
   :maxdepth: 2
   :caption: Table of Contents
   
   source-file-basics-en.rst
   source-file-structure-en.rst
   
.. _RFC 2119: http://tools.ietf.org/html/rfc2119