=================
High Level Desing
=================

Abstraction
===========

* There need to be a balance of how much abstraction required

Task: Make a couse video

Usuall steps:

1. Choose a topic
2. Develop some material
3. Go to studio
4. Record
5. Reshoot if any changes
6. Post-production
7. Upload/Post video

A professor is concerned with steps 1-5
Studio is concerned with steps 3-5
Producer is concerned with 3-7

Decomposition
=============
Process of breaking down into manageable tasks

==========
API Design
==========

High Level API Design
=====================

* Maximise their utility
* Minimize technical debt
* It is an iterative process

**4 design principles**

1. Do on thing and do it well
2. Never expose internal implementation details (Information hiding)
3. Small as possible
4. Usability

Low level API desing
====================

* Avoid long parameter list
* Return descriptive objects
  * Instead of returning primitives return an object

* Avoid exceptional returns
  * Instead of returning null return empty list

* Handle exceptional circumstances
  * Try to give a descriptive error message while throwing exceptions. Can include link for more info regarding the exception/error
  * It should be understandable without giving implementation details

* Favour immutability
* Favour private classes, fields & methods

API design process
==================

Questions to think before designing APIs:
1. What is the goal of this API?
* Help makes decision in language, protocols, platforms, formats

2. Who is this API consumer?
* Helps in deciding concerns for versoning, licensing, authentication

Process:
1. Start with short specification
2. Solicit feedback from potential customers
3. Prototype clients that use the API
* Help us understand how user use API
* Can give insight into error handling, boiler plate code and any other improvements

4. Document the API
   * Include examples for users

API usability
=============

* How easy for usage
* Naming, actions, protocols
* Easy to use correctly, hard to use incorrectly

1. Visibility
   * Easy to look and understand
   * Prioritize what are the important parts of the API

e.g., 
Sorting method within an online store
.. code:: java
   
   // Sort items based on their clearance
   items.sort('clearance');

   // Transform to make it hard to use improperly
   // use Filter enum for enforcing proper usage and
   // no out bound paramters
   items.sort(Filter.CLEARANCE);

2. Model
   * Can give proper abstraction for model
   * Matching their view of the domain model with the API model

e.g.,
Online store

.. code:: java

   // get doesn't make sense
   store.get(productId: String)

    // provide a descriptive name
    store.getProduct(productId: String);

    // Need to think the amount of abstraction can be provided
    // user might not care about departements or shelf's
    // only requires products
    store.getDept(deptId: String).getShelf(shelfID: String).getProduct(productID: String)

3. Mapping
   * Related to mental model

.. code:: java
   
   // No proper type declaration
   store.getProduct(productId: String): String

   // provide more detail
   store.getProduct(productId: String): Product

4. Feedback
   * Constant and early feedback as fast as possible

e.g.,
.. code:: java
   
   // typo in parameter
   items.sort('clearamce');

   // check parameter makes sense
   // if not throw an exception giving descriptive message

API platforms and summary
=========================
Other things to consider:
* Autentication
* Versioning
* Migration: backward/forward compatibility
* Get the design right

================
REST development
================

