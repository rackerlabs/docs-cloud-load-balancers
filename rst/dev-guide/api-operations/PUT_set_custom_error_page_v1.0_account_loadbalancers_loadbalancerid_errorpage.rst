=============================================================================
Set Custom Error Page -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Set Custom Error Page
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <PUT_set_custom_error_page_v1.0_account_loadbalancers_loadbalancerid_errorpage.rst#request>`__
`Response <PUT_set_custom_error_page_v1.0_account_loadbalancers_loadbalancerid_errorpage.rst#response>`__

.. code-block:: javascript

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/errorpage

Sets a custom error page for a specified load balancer.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|413                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |xsd:string               |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |xsd:string *(Required)*  |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|content                   |xsd:string *(Required)*  |The HTML content for the |
|                          |                         |custom error page. Must  |
|                          |                         |be 65536 characters or   |
|                          |                         |fewer. See the request   |
|                          |                         |examples in this section |
|                          |                         |for the required XML and |
|                          |                         |JSON formats.            |
+--------------------------+-------------------------+-------------------------+





**Example Set Custom Error Page: JSON request**


.. code::

    {"errorpage": 
    {"content":"\n<html>\n    DEFAULT ERROR PAGE\n</html>\n"}
    } 


**Example Set Custom Error Page: XML request**


.. code::

    <errorpage xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <content>
                  <![CDATA[
                   <html> DEFAULT ERROR PAGE
                   </html>
           ]]>
        </content>
    </errorpage>


Response
^^^^^^^^^^^^^^^^^^





**Example Set Custom Error Page: JSON request**


.. code::

    {"errorpage":
        {"content":"<html> DEFAULT ERROR PAGE</html>"}
    }


**Example Set Custom Error Page: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <errorpage xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <content>
                   <html> DEFAULT ERROR PAGE
                   </html>
        </content>
    </errorpage>

