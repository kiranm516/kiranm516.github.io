=======================
Java Enterprise Edition
=======================

RequestDispatcher.forward() vs HttpServletResponse.sendRedirect() [001]_ [002]_
-------------------------------------------------------------------------------

**requestDispatcher - forward() method**

# When we use forward method, request is transfer to other resource within the same server for further processing.
# In case of forward, web container handle all process internally and client or browser is not involved.
# When forward is called on requestdispatcher object we pass request and response objects so our old request object is present on new resource which is going to process our request.
# Visually we are not able to see the forwarded address, it is transparent.
# Using forward () method is faster than send redirect.
# When we redirect using forward and we want to use same data in new resource we can use request.setAttribute () as we have request object available.

**SendRedirect**

# In case of sendRedirect, request is transfer to another resource to different domain or different server for further processing.
# When you use sendRedirect, container transfers the request to client or browser so URL given inside the sendRedirect method is visible as a new request to the client.
# In case of sendRedirect call, old request and response objects are lost because it’s treated as new request by the browser.
# In address bar, we are able to see the new redirected address. It’s not transparent.
# sendRedirect is slower because one extra round trip is required, because completely new request is created and old request object is lost. Two browser request required.
# But in sendRedirect, if we want to use we have to store the data in session or pass along with the URL.

**Which one is good?**
Its depends upon the scenario that which method is more useful.

If you want control is transfer to new server or context and it is treated as completely new task then we go for Send Redirect. Generally, forward should be used if the operation can be safely repeated upon a browser reload of the web page will not affect the result.

References
==========
.. [001] https://stackoverflow.com/questions/2047122/requestdispatcher-forward-vs-httpservletresponse-sendredirect
.. [002] http://javarevisited.blogspot.in/2011/09/sendredirect-forward-jsp-servlet.html