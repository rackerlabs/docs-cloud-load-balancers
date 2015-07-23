=============================================================================
Create Or Update Connection Throttling Configuration -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Create Or Update Connection Throttling Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <PUT_create_or_update_connection_throttling_configuration_v1.0_account_loadbalancers_loadbalancerid_connectionthrottle.rst#request>`__
`Response <PUT_create_or_update_connection_throttling_configuration_v1.0_account_loadbalancers_loadbalancerid_connectionthrottle.rst#response>`__

.. code-block:: javascript

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/connectionthrottle

Creates or updates the throttling configuration.

The connection throttling feature imposes limits on the number of connections per IP address to help mitigate malicious or abusive traffic to your applications. The attributes in the table that follows can be configured based on the traffic patterns for your sites.

You must specify all attributes when initially creating the connection throttle. However, when you update an existing setting, you can pass as few as one attribute.



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
|maxConnectionRate         |xsd:int *(Required)*     |Deprecated as of v1.22   |
|                          |                         |and later versions.      |
|                          |                         |Parameter can still be   |
|                          |                         |set, but it has no       |
|                          |                         |effect on the load       |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|maxConnections            |xsd:int *(Required)*     |Maximum number of        |
|                          |                         |connections to allow for |
|                          |                         |a single IP address. To  |
|                          |                         |enable unlimited         |
|                          |                         |simultaneous             |
|                          |                         |connections, setto 0.    |
|                          |                         |Set to a value from 1 to |
|                          |                         |100000.                  |
+--------------------------+-------------------------+-------------------------+
|minConnections            |xsd:int *(Required)*     |Deprecated as of v1.22   |
|                          |                         |and later versions.      |
|                          |                         |Parameter can still be   |
|                          |                         |set, but it has no       |
|                          |                         |effect on the load       |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|rateInterval              |xsd:int *(Required)*     |Deprecated as of v1.22   |
|                          |                         |and later versions.      |
|                          |                         |Parameter can still be   |
|                          |                         |set, but it has no       |
|                          |                         |effect on the load       |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





**Example Create Or Update Connection Throttling Configuration: JSON request**


.. code::

    {
        "connectionThrottle":{
            "maxConnections": 10,
            "minConnections": 100,
            "maxConnectionRate": 50,
            "rateInterval": 60
        }
    }


**Example Create Or Update Connection Throttling Configuration: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    
    <connectionThrottle xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        minConnections="10"
        maxConnections="100"
        maxConnectionRate="50"
        rateInterval="60" />


**Example Create Or Update Connection Throttling Configuration: JSON request**


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
^^^^^^^^^^^^^^^^^^




