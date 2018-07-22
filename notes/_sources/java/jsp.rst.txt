=================
Java Server Pages
=================

JSP
===

page directive
==============

.. code:: jsp
   
   // Set encoding of the response
   <%@ page contentType="text/html; charset=UTF-8" %>

   <%@ page errorPage="errorpage.jsp" %>

   <%@ page isErrorPage="true" %>

   // To set the source encoding of the page itself
   <%@ page pageEncoding="UTF-8" %>


Import classes in JSP
---------------------

.. code:: jsp
   
   <%@ page import="java.util.List" %>
   
   <%-- If you want to import multiple classes --%>
   <%@ page import="package1.myClass1,package2.myClass2,....,packageN.myClassN" %>

JSTL
====

if
---

.. code:: jsp
   
   <c:if test="${empty someFlag}">
    ...
   </c:if>

   <!-- not case -->
   <!-- can also be done !empty -->
   <c:if test="${not empty someFlag}">
    ...
   </c:if>

For testing null and boolean property

.. code:: jsp
   
   <c:if test="${isDataSet != null && isDataSet}">
      <!-- Do something if isDataSet is available and set to true -->
   </c:if>

if else / choose
-----------------

.. code:: jsp
   
   <c:choose>
     <c:when test="${condition1}">
       ...
     </c:when>
     <c:when test="${condition2}">
       ...
     </c:when>
     <c:otherwise>
       ...
     </c:otherwise>
   </c:choose>

Conditional operator (?)
------------------------

.. code:: jsp
   
   <c:out value="" />

Get index in forEach [002]_
---------------------------

.. code:: jsp
   
   <c:forEach items="${itemsList}" var="item"  varStatus="loop">
      <p>Item: ${item} had Index: ${loop.index}</p>
   </c:forEach>

Iterate Map [001]_
------------------

For accessing Map<Key, Value>

.. code:: jsp
   
   <c:forEach items="${list}" var="map">
      <c:forEach items="${map}" var="entry">
        Key: ${entry.key}<br>
        Value: ${entry.value}<br>
      </c:forEach>
   </c:forEach>

empty operator [003]_
---------------------

**1.10 Empty Operator - empty A**

The empty operator is a prefix operator that can be used to determine if a value is null or empty.

To evaluate ``empty A``

* If A is null, return true
* Otherwise, if ``A`` is the empty ``string``, then return ``true``
* Otherwise, if ``A`` is an empty ``array``, then return ``true``
* Otherwise, if ``A`` is an empty ``Map`, return ``true``
* Otherwise, if ``A`` is an empty ``Collection``, return ``true``
* Otherwise return ``false``

EL not being evaluated
======================

If Expression Languages is not being evaluated and getting the same expression. Need to set ``isELIgnored="false"``

This can be set at page level or in web.xml for entire web application.

Templating using Tag files
==========================

**Tag declaration**

.. code:: jsp
   
   <%@ taglib tagdir="/WEB-INF/tags/my" prefix="my" %>

Here ``my`` can be whatever you want

**Tag structure**

.. code:: jsp
   
   <prefix:name [attribute=value] ... />

   <% -- OR --%>

   <prefix:name [attribute=value] ... />

   // Any body element nested within the tag

   </prefix:name>

Here ``prefix`` is user assigned namespace

* Tag files need to have suffix/extension ``.tag``
* Can only be placed in ``/WEB-INF/tags/``
* TLD is not mandatory for tag files. But, are recommended
* if the tag file name is ``userdetail.tag`` then the tag name is ``userdetail``
* request, session, application had same scope as the page invocking the tag
* A fresh, clean page scope is setup for each invocation of the tag, and does not affect the invoking JSP page

example:

.. code:: jsp
   
   <%@ taglib prefix="my" tagdir="/WEB-INF/tags/m" %>

   <my:sample />

Here ``<my:sample />`` refers to ``/WEB-INF/tags/m/sample.tag``


References
==========

.. [001] https://stackoverflow.com/questions/2148658/iterate-over-elements-of-list-and-map-using-jstl-cforeach-tag
.. [002] http://www.bmchild.com/2012/03/jstl-cforeach-varstatus-properties.html
.. [003] https://stackoverflow.com/questions/14185031/how-does-el-empty-operator-work-in-jsf/
