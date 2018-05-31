======
PL/SQL
======

Block
-----

A PL/SQL block is made up of three sections
- Declaration (optional)
	
    - Allows variables, types, procedures and functions to be defined for use within the block
    
- Executable
- Exception (optional)

.. code:: sql

   [DECLARE --declarations]
   -- declare any local variabled
   BEGIN

   	-- statements
   
   [EXCEPTION -- handlers]
   -- handle exceptions

   END;


Notes
-----

``PL/SQL: ORA-00904: : invalid identifier
PLS-00231: function 'GET_RATIO_NAME' may not be used in SQL``

- For using function in a SQL statement in a stored procedure in a package. It need to be declared in the package specification