=====================
Java Standard Edition
=====================

Parse date string
-----------------

**Java 6**

.. code:: java
   
   String dateString = "31/05/2018";
   DateFormat format = new SimpleDateFormat("dd/MM/yyyy");

   // Parse will throw an Exception
   Date date = format.parse(dateString);

