
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

Update load balancer properties
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}

Updates the properties for a specified load balancer.

This operation asynchronously updates the attributes for a specified load balancer. Upon successful validation of the request, the service returns a 202 (Accepted) response code. A caller can poll the load balancer with its ID to wait for the changes to be applied and the load balancer to return to an ``ACTIVE`` status.

.. note::
   The load balancer's ID and status are immutable attributes and cannot be modified by the caller. Supplying an unsupported attribute results in a 400 (badRequest) fault.
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------+-------------------+-------------------------------------+
|Name                |Type               |Description                          |
+====================+===================+=====================================+
|name                |String *(Optional)*|Name of the load balancer to update. |
|                    |                   |The name must be 128 characters or   |
|                    |                   |fewer in length, and all UTF-8       |
|                    |                   |characters are valid. See `          |
|                    |                   |http://www.utf8-chartable.de/        |
|                    |                   |<http://www.utf8-chartable.de/>`__   |
|                    |                   |for information about the UTF-8      |
|                    |                   |character set.                       |
+--------------------+-------------------+-------------------------------------+
|protocol            |String *(Optional)*|Protocol of the service that is      |
|                    |                   |being load balanced.                 |
+--------------------+-------------------+-------------------------------------+
|halfClosed          |Boolean            |Enables or disables Half-Closed      |
|                    |*(Optional)*       |support for the load balancer. Half- |
|                    |                   |Closed support provides the ability  |
|                    |                   |for one end of the connection to     |
|                    |                   |terminate its output, while still    |
|                    |                   |receiving data from the other end.   |
|                    |                   |Only available for                   |
|                    |                   |TCP/TCP_CLIENT_FIRST protocols.      |
+--------------------+-------------------+-------------------------------------+
|algorithm           |String *(Optional)*|Algorithm that defines how traffic   |
|                    |                   |should be directed between back-end  |
|                    |                   |nodes.                               |
+--------------------+-------------------+-------------------------------------+
|port                |String *(Optional)*|Port number for the service you are  |
|                    |                   |load balancing.                      |
+--------------------+-------------------+-------------------------------------+
|timeout             |String *(Optional)*|The timeout value for the load       |
|                    |                   |balancer and communications with its |
|                    |                   |nodes. Defaults to 30 seconds with a |
|                    |                   |maximum of 120 seconds.              |
+--------------------+-------------------+-------------------------------------+
|httpsRedirect       |Boolean            |Enables or disables HTTP to HTTPS    |
|                    |*(Optional)*       |redirection for the load balancer.   |
|                    |                   |When enabled, any HTTP request       |
|                    |                   |returns status code 301 (Moved       |
|                    |                   |Permanently), and the requester is   |
|                    |                   |redirected to the requested URL via  |
|                    |                   |the HTTPS protocol on port 443. For  |
|                    |                   |example,                             |
|                    |                   |`http://example.com/page.html        |
|                    |                   |<http://example.com/page.html>`__    |
|                    |                   |would be redirected to               |
|                    |                   |`https://example.com/page.html       |
|                    |                   |<https://example.com/page.html>`__.  |
|                    |                   |Only available for HTTPS protocol (  |
|                    |                   |``port=443`` ), or HTTP protocol     |
|                    |                   |with a properly configured SSL       |
|                    |                   |termination (                        |
|                    |                   |``secureTrafficOnly=true``,          |
|                    |                   |``securePort=443`` ). Note that SSL  |
|                    |                   |termination for a load balancer can  |
|                    |                   |only be configured after the load    |
|                    |                   |balancer has been created.           |
+--------------------+-------------------+-------------------------------------+





**Example Update load balancer properties: JSON request**


.. code::

    {"loadBalancer":{
        "name": "sample-loadbalancer",
        "algorithm": "RANDOM",
        "protocol": "HTTP",
        "port": 80,
        "timeout": 60,
        "httpsRedirect": true
        }
    }


**Example Update load balancer properties: XML request**


.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        name="sample-loadbalancer"
        algorithm="RANDOM"
        protocol="HTTP"
        port="80"
        timeout="60"
        httpsRedirect="true"/>


Response
""""""""""""""""






This operation does not return a response body.




