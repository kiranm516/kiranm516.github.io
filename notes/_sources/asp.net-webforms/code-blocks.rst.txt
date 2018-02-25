===========
Code Blocks
===========

.. code:: aspx-cs

    # output
    <%= DateTime.Now.ToString() %>
    # this will auto encode html
    <%: DateTime.Now.ToString() %>

    # code, any valid C# code can be put in there
    <%
        {
            Response.Write(DateTime.Now.ToString());
        }
    %>

.. code:: aspx-cs

    # <% ... %>

    # <%= ... %>

    # <%# ... %>

    # <%$ ... %>

