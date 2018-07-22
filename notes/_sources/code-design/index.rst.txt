===========
Code Design
===========

Generic
=======

Exception vs Boolean [CD001]_
-----------------------------
Exceptions are generally the way to go for things where failure is not expected as an option. Boolean return values are the way to go for things where failure might be an expected result sometimes.

Java
====

Single Abstract Method Interface (SAM) [CD002]_
-----------------------------------------------

.. code:: java
   
   public class SamInteraceExample  {
        public static void main(String[] args)  {
            // This is using anonymous class
            new Thread(new Runnable()   {
                @Override
                public void run()   {
                    System.out.println("Running using anonymous classes");
                }
            }).start();

            // This is using lambda expression
            new Thread(
                () -> System.out.println("Running using lambda expression")
            ).start();
        }
   }


References
==========

.. [CD001] https://stackoverflow.com/questions/2972307/when-to-return-bool-throw-an-exception-and-which-exception-to-throw
.. [CD002] https://dzone.com/articles/introduction-functional-1
