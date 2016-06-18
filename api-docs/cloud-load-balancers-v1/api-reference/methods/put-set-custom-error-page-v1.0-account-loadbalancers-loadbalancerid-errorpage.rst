
.. _put-set-custom-error-page-v1.0-account-loadbalancers-loadbalancerid-errorpage:

Set custom error page
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/errorpage

Sets a custom error page for a specified load balancer.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|422                       |ImmutableEntity          |This fault is returned   |
|                          |                         |when a user attempts to  |
|                          |                         |modify an item that is   |
|                          |                         |not currently in a state |
|                          |                         |that allows              |
|                          |                         |modification. For        |
|                          |                         |example, load balancers  |
|                          |                         |in a status of           |
|                          |                         |PENDING_UPDATE,BUILD, or |
|                          |                         |DELETED may not be       |
|                          |                         |modified.                |
+--------------------------+-------------------------+-------------------------+
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String                   |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|content                   |String *(Required)*      |The HTML content for the |
|                          |                         |custom error page. Must  |
|                          |                         |be 65536 characters or   |
|                          |                         |fewer. See the request   |
|                          |                         |examples in this section |
|                          |                         |for the required XML and |
|                          |                         |JSON formats.            |
+--------------------------+-------------------------+-------------------------+





**Example Set custom error page: JSON request**


.. code::

    {"errorpage": 
    {"content":"\n<html>\n    DEFAULT ERROR PAGE\n</html>\n"}
    } 


**Example Set custom error page: XML request**


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
^^^^^^^^^^^^^










**Example Set custom error page: JSON response**


.. code::

    {"errorpage":
        {"content":"<html> DEFAULT ERROR PAGE</html>"}
    }


**Example Set custom error page: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <errorpage xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <content>
                   <html> DEFAULT ERROR PAGE
                   </html>
        </content>
    </errorpage>

