
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Custom Error Page -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Custom Error Page
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-custom-error-page-v1.0-account-loadbalancers-loadbalancerid-errorpage.html#request>`__
`Response <get-show-custom-error-page-v1.0-account-loadbalancers-loadbalancerid-errorpage.html#response>`__

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/errorpage

Shows the custom error page that is configured for a specified load balancer.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
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





Response
^^^^^^^^^^^^^^^^^^





**Example Show Custom Error Page: JSON response**


.. code::

    {"errorpage":
        {"content":"<html> DEFAULT ERROR PAGE</html>"}
    }


**Example Show Custom Error Page: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <errorpage xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <content>
                   <html> DEFAULT ERROR PAGE
                   </html>
        </content>
    </errorpage>

