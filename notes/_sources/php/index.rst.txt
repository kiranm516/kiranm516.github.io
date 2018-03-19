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

.. code :: php
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

.. code:: php

   <?php
     session_start();
     echo $_SESSION['youritem'];
   ?>

Install specific version of package in Composer
===============================================

composer require vendor/package:version

for example:

composer require refinery29/test-util:0.10.2


PHP Short Forms
===============

.. code:: php

   <?php if ($expression == true): ?>
     This will show if the expression is true.
   <?php else: ?>
     Otherwise this will show.
   <?php endif; ?>

   <?php for ($i = 0; $i < 5; ++$i): ?>
   Hello, there!
   <?php endfor; ?>

   <? foreach($DATA as $row): ?>
   <li><a href="<?=$row['link']?>" target="_blank"><?=$row['name']?></a></li>
   <? endforeach ?>

   echo empty($address['street2']) ? "Street2 is empty!" : $address['street2'];


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

IF & ELSE IF
------------
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


the built-in function htmlentities(str) (or htmlspecialchars(str)) converts all the special characters to HTML entities (e.g., > to &gt;, < to &lt;, " to &quot;, & to &amp;). It is important to convert special characters, in particular, < and >, before echoing back to the client to prevent the so-called Cross-Site Scripting attack (XSS).

String Functions
================

strlen(str): returns the length of the given string.
substr(str, start [, length]): returns the substring from start position of length.
strtoupper(str), strtolower(str): return the uppercase/lowecase of the given string.
trim(str): trim whitespaces from the beginning and end of the given string.
rtrim(str): trim whitespaces from the end of the given string.

Checking Variables
==================
You can use the following built-in functions:
isset($var): return TRUE is $var is set and is not NULL.
unset($var): unset the $var.
is_null($var): return TRUE if the $var is NULL.
empty($var): return TRUE if the $var does not exist (i.e. !isset($var)) or its value is equivalent to boolean FALSE (e.g., NULL, 0, 0.0, '', '0', empty array and object).

Type Casting and Conversion
===========================
As an example, there are 3 ways to cast a string to an integer:
intval(): The function intval($str) returns an equivalent integer or 0 if $str does not contain an valid integer. Take note that it cannot handle '0', as the result is ambiguous.
Casting operator (int): same as intval().
settype($var, 'integer'): convert $var to integer type, and return either TURE/FALSE.

PHP Design
==========

Layout Page
-----------
- You're assuming that header.php would be called on the every page call. That's wrong.
- You're assuming that header.php will always be static. That's wrong.
- You forgot to create a template for the page itself.
- The main rule everyone have to learn by heart: Not a single character has to be sent into browser, until all data gets ready.

Why?
----
It's 2018 today. AJAX era. What if your code will have to send JSONed data instead of whole HTML page?
there is a thing called HTTP header. Sometimes we have to send them. And it's gets impossible if you already have your ornate HTML header sent.
it's for just 4-page site. Okay. Imagine you've got lucky and got a request for another 4-page site. You will have to change only templates and don't touch engine files. That's really great benefit.
Imagine you're going to make a custom <title> tag for your pages, based on the page content. Isn't it extremely common thing? But you can't make it without using templates.
So, you have to have one common site template containing header and footer and also dedicated templates for the every php script.

An example layout is going to be like this:

1. Page Itself
--------------
it outputs nothing but only gather required data and calls a template:

.. code:: php

   <?
      //include our settings, connect to database etc.
      include dirname($_SERVER['DOCUMENT_ROOT']).'/cfg/settings.php';
      
      //getting required data
      $DATA=dbgetarr("SELECT * FROM links");
      $pagetitle = "Links to friend sites";
      
      //etc
      //and then call a template:
      $tpl = "links.tpl.php";
      include "template.php";
   ?>

2. template.php which is your main site template
------------------------------------------------
Consists of your header and footer

.. code:: php

   <html>
      <head>
         <title>My site. <?=$pagetitle?></title>
      </head>
      <body>
         <div id="page">
            <? include $tpl ?>
         </div>
      </body>
   </html>

3. and finally links.tpl.php is the actual page template:
---------------------------------------------------------
.. code:: php

   <h2><?=$pagetitle?></h2>
   <ul>
      <? foreach($DATA as $row): ?>
         <li><a href="<?=$row['link']?>" target="_blank"><?=$row['name']?></a></li>
      <? endforeach ?>
   <ul>

easy, clean and maintainable.

Passing php form validate error message back to submit form
===========================================================
On a quick glance try this

Session way
-----------
Make sure to start the session by doing session_start(); at the top of the file where saveComment is and the isset checked.

.. code:: php

   function saveComment(){
       $id = isset($_POST["articleId"]) ? $_POST["articleId"] : '';

       if ( isset( $_POST['saveChanges'] ) ) {
          if ( $_POST['name'] == "" ){
               $_SESSION['errorMessage'] = "Please fill out your name.";
               header( "Location:".HOME_PATH."/.?action=viewArticle&articleId=".$_POST['articleID']."");
          }

      if ( isset( $_SESSION['errorMessage'] ) ) {
          echo $_SESSION['errorMessage'];
      }
   }

or you can try

POST way
--------
.. code:: php

   function saveComment(){
      $id = isset($_POST["articleId"]) ? $_POST["articleId"] : '';

      if ( isset( $_POST['saveChanges'] ) ) {
         if ( $_POST['name'] == "" ){
            $error = urlencode('Please fill out your name');
            header( "Location:".HOME_PATH."/.?action=viewArticle&articleId=".$_POST['articleID']. "&error=" . $error);
         }
         if ( isset( $_GET['error'] ) ) {
            echo urldecode($_GET['error']);
         }
      }
   }

Note
----
You're setting a variable $validate for your currently executing script. Afterwards, you send a redirect header. This will cause your browser to issue a new request, thus ending the currently executing script and scrapping the variable. The new request will trigger another script invocation, where the variable is not known anymore since it only existed for the duration of the first request.

HTTP is stateless, so every variable you set on the server side will only exist until you finish your current request and respond to the client. What you need is a way to pass this variable to the script handling the second request. There are several ways to do so:

Pass a GET parameter. You could append something like "&validationError=" . $validate['errorMessage'] to the URL you're passing to the Location header, and then in the display page access it via $_GET.
Save the validation status in the $_SESSION. The PHP manual contains a lot of information about sessions (maybe you're already using them?)
Restructure your code in a way that you don't redirect on error, but on success.
Some more information on the 3rd proposal: You write one PHP-Script which displays the form and handles the form post request. If validation fails, you simply redisplay, and insert the echo statement you already have. If it suceeds, you redirect to some success page. This way, the variable will remain accessible, since it's still the same request.

the built-in function htmlentities(str) (or htmlspecialchars(str)) converts all the special characters to HTML entities (e.g., > to &gt;, < to &lt;, " to &quot;, & to &amp;). It is important to convert special characters, in particular, < and >, before echoing back to the client to prevent the so-called Cross-Site Scripting attack (XSS).

Redirect to another page
========================
header("Location: home.php");

Check query parameters
======================
$slide = ( isset($_GET["id"]) && trim($_GET["id"]) == 'link1' ) ? trim ($_GET["id"]) : '';

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
-------
You need make sure to start the session at the top of every PHP file where you want to use the $_SESSION superglobal. Like this:

.. code:: php

   <?php
     session_start();
     echo $_SESSION['youritem'];
   ?>

Get the class name
==================
static::class