==================
Front-end Security
==================

Usefule references
==================
* https://developer.mozilla.org/en-US/docs/Web/Security

HTML
====

Disable autocomplete for password fields [001]_
-----------------------------------------------
add ``autocomplete`` attribute and set it to ``off``

.. code:: html
   
   <form>
        <label>Password</label>
        <input type="password" autocomplete="off">
   </form>


References
==========

.. [001] https://developer.mozilla.org/en-US/docs/Web/Security/Securing_your_site/Turning_off_form_autocompletion