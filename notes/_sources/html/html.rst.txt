====
HTML
====


Special characters codes
========================

.. csv-table::

   **Character**,**Code**
   &, ``&amp;``


Submitting readonly fields
==========================
Adding a hidden field with the same name will sends the data when the form is submitted.

.. code:: html
  
  <input type="hidden" name="my_name" value="blablabla" />
  <input type="text" name="my_name" value="blablabla" disabled="disabled" />