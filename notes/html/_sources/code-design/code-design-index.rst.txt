===========
Code Design
===========

Exception vs Boolean [CD001]_
=============================
Exceptions are generally the way to go for things where failure is not expected as an option. Boolean return values are the way to go for things where failure might be an expected result sometimes.

.. [CD001] https://stackoverflow.com/questions/2972307/when-to-return-bool-throw-an-exception-and-which-exception-to-throw
