
.. _put-create-or-update-connection-throttling-configuration-v1.0-account-loadbalancers-loadbalancerid-connectionthrottle:

Create or update connection throttling configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/connectionthrottle

Creates or updates the throttling configuration.

The connection throttling feature imposes limits on the number of connections per IP address to help mitigate malicious or abusive traffic to your applications. The attributes in the table that follows can be configured based on the traffic patterns for your sites. 

.. note::
   You must specify all attributes when initially creating the connection throttle. However, when you update an existing setting, you can pass as few as one attribute.
   
   



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

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|maxConnectionRate         |Int *(Optional)*         |Deprecated as of v1.22   |
|                          |                         |and later versions.      |
|                          |                         |Parameter can still be   |
|                          |                         |set, but it has no       |
|                          |                         |effect on the load       |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|maxConnections            |Int *(Optional)*         |Maximum number of        |
|                          |                         |connections to allow for |
|                          |                         |a single IP address. To  |
|                          |                         |enable unlimited         |
|                          |                         |simultaneous             |
|                          |                         |connections, set to 0.   |
|                          |                         |Set to a value from 1 to |
|                          |                         |100000.                  |
+--------------------------+-------------------------+-------------------------+
|minConnections            |Int *(Optional)*         |Deprecated as of v1.22   |
|                          |                         |and later versions.      |
|                          |                         |Parameter can still be   |
|                          |                         |set, but it has no       |
|                          |                         |effect on the load       |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|rateInterval              |Int *(Optional)*         |Deprecated as of v1.22   |
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


**Example Create or update atom connection throttling configuration: ATOM/XML response**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next"
              href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/connectionthrottle.atom?page=2"/>
        <title type="text">Connection Throttle Feed</title>
        <id>1234-loadbalancers-141-connectionthrottle</id>
        <author>
            <name>Rackspace Cloud</name>
        </author>
        <entry>
            <title type="text">Error Updating Connection Throttle</title>
            <summary type="text">Could not update the connection throttle at this time</summary>
            <link href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/connectionthrottle/"/>
            <id>1234-loadbalancers-141-connectionthrottle-2011881846570</id>
            <category term="UPDATE"/>
            <updated>2011-03-29T18:46:57.000Z</updated>
        </entry>
    </feed>


Response
""""""""""""""""






This operation does not return a response body.




