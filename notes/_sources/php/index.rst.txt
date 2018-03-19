===
PHP
===


Check if array is empty
=======================

If you just need to check if there are ANY elements in the array

.. code:: php
   
   if (empty($playerlist)) {
     // list is empty.
   }

If you need to clean out empty values before checking (generally done to prevent explodeing weird strings):

..code :: php
  foreach ($playerlist as $key => $value) {
  	if (empty($value)) {
  		unset($playerlist[$key]);
  	}
  }

  if (empty($playerlist)) {
  	//empty array
  }


Session Handling in PHP
=======================

To use session:
- Start a session via session_start(). The session_start() starts a new session or resume the existing session.
- The superglobal associative array $_SESSION maintain data of the session.
- You can check if a key-value pair exists via isset($_SESSION['key']).
- You can set a key-value pair for this session via $_SESSION['key'] = value.
- You can retrieve value of a particular key via $_SESSION['key'].
- You can remove a key-value pair via unset($_SESSION['key']).
- You can use function session_id() to retrieve the session ID.
- To terminate the session explicitly, use session_write_close().

The procedure is:
1. Authenticate the user's credential.
2. Create a new session via session_start(), and place some tokens inside the session, e.g. $_SESSION['isLogin'] = TRUE.
3. On all the other pages, resume the session ALSO via session_start(), and check if $_SESSION['isLogin'] is there, which indicates a resumed session rather than a new session.


Session
=======
You need make sure to start the session at the top of every PHP file where you want to use the $_SESSION superglobal. Like this:

<?php
  session_start();
  echo $_SESSION['youritem'];
?>


Get the class name
==================
static::class


Install specific version of package in Composer
===============================================

composer require vendor/package:version

for example:

composer require refinery29/test-util:0.10.2


Alternative syntax for control structures
=========================================

Echo
----

.. code:: php
    
    <?= ?>
    
    e.g., 
    <?= $this->getName() ?>

    # instead of
    <?php echo $this->getName() ?>

IF
--

.. code:: php

   <?php if ($a == 5): ?>

   <?php elseif(bool): ?>

   <?php else: ?>

   <?php end if; ?>


For each
--------

.. code:: php
   
   <?php foreach($ibtsRespondedData as $record): ?>
   <?php endforeach ?>

