.. _put-create-or-update-connection-throttling-configuration:

Create or update connection throttling configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/connectionthrottle

Creates or updates the throttling configuration.

The connection throttling feature imposes limits on the number of connections
per IP address to help mitigate malicious or abusive traffic to your
applications. The attributes in the table in the following Request section
can be configured based on the traffic patterns for your sites.

.. note::
   You must specify all attributes when initially creating the connection
   throttle. However, when you update an existing setting, you can pass as
   few as one attribute.

When connection throttling is active, and the connection limit is exceeded,
the load balancer returns a ``503 Server Too Busy`` response. You'll see
something similar to the following example:

.. code::

   Trying <LB IP>...
   connected
   Connected to <LB IP> (<LB IP>) port 80 (#0)
   > GET /pi.php HTTP/1.1
   > User-Agent: curl/7.26.0
   > Host: <LB IP>
   > Accept: /
   >
   additional stuff not fine transfer.c:1037: 0 0
   HTTP 1.0, assume close after body
   < HTTP/1.0 503 Server Too Busy
   < Content-Length: 25
   < Content-Type: text/html
   <
   <h2>Server Too Busy</h2>
   Closing connection #0




The following table shows the possible response codes for this operation:

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
-------

The following table shows the URI parameters for the request:

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

The following table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|maxConnectionRate         |Int                      |Deprecated as of v1.22   |
|                          |                         |and later versions.      |
|                          |                         |Parameter can still be   |
|                          |                         |set, but it has no       |
|                          |                         |effect on the load       |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|maxConnections            |Int                      |Maximum number of        |
|                          |                         |connections to allow for |
|                          |                         |a single IP address. To  |
|                          |                         |enable unlimited         |
|                          |                         |simultaneous             |
|                          |                         |connections, set to 0.   |
|                          |                         |Set to a value from 1 to |
|                          |                         |100000.                  |
+--------------------------+-------------------------+-------------------------+
|minConnections            |Int                      |Deprecated as of v1.22   |
|                          |                         |and later versions.      |
|                          |                         |Parameter can still be   |
|                          |                         |set, but it has no       |
|                          |                         |effect on the load       |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|rateInterval              |Int                      |Deprecated as of v1.22   |
|                          |                         |and later versions.      |
|                          |                         |Parameter can still be   |
|                          |                         |set, but it has no       |
|                          |                         |effect on the load       |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+

**Example Create or update connection throttling configuration: JSON request**

.. code::

    {
        "connectionThrottle":{
            "maxConnections": 10,
            "minConnections": 100,
            "maxConnectionRate": 50,
            "rateInterval": 60
        }
    }

**Example Create or update connection throttling configuration: XML request**

.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <connectionThrottle xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        minConnections="10"
        maxConnections="100"
        maxConnectionRate="50"
        rateInterval="60" />

Response
--------


This operation does not return a response body.
