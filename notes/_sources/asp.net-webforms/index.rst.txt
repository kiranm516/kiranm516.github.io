================
ASP.NET WebForms
================

Best/Modern Practices
=====================

Turn off ViewState
------------------

- Most controls do not require ViewState

  - New techniques allow for controls to manage data without it

Disable on Page directive
~~~~~~~~~~~~~~~~~~~~~~~~~
``<%@ Page EnableViewState="false" %>``

Disable in web.config

<system.web>
    <pages enableViewState="false" />


Use Bundles
===========
Use bundles for configuring any javascript or css resources

- ``App_Start/BundleConfig.cs``
- ``/Bundle.config``

Take all your javascript, css and combine and minifies and serves as one file.
Benefit is as HTTP has waterfall model where requests are come one by one so all in a single request can make it load all at once

