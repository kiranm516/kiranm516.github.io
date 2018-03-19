=====
MySQL
=====

.. code:: sql
   
   STR_TO_DATE(str,format)

   e.g.,

   mysql> SELECT STR_TO_DATE('01,5,2013','%d,%m,%Y');
   	-> '2013-05-01'
   mysql> SELECT STR_TO_DATE('May 1, 2013','%M %d,%Y');
   	-> '2013-05-01'
   
   format:
   %d - dd
   %m - MM
   %Y - yyyy