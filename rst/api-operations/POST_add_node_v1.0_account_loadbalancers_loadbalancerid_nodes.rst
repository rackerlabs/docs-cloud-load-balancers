=============================================================================
Add Node -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Add Node
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_add_node_v1.0_account_loadbalancers_loadbalancerid_nodes.rst#request>`__
`Response <POST_add_node_v1.0_account_loadbalancers_loadbalancerid_nodes.rst#response>`__

.. code-block:: javascript

    POST /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes

Adds a node to a specified load balancer.

When a node is added, it is assigned a unique ID that can be used for management operations such as changing the condition or removing it. Every load balancer is dual-homed on both the public Internet and ServiceNet. That is, you may add public or ServiceNet nodes. As a result, nodes can either be internal ServiceNet addresses or addresses on the public Internet. The Virtual IP (or Virtual IPs) of the load balancer, however, can only be either public or ServiceNet.

One or more secondary nodes can be added to a specified load balancer so that if all the primary nodes fail, traffic can be redirected to secondary nodes. The type attribute enables configuring the node as either PRIMARY or SECONDARY.

Domain names are also accepted with certain restrictions. Refer to the following API operation for information about how to list the allowed names: `List allowed domains <http://docs.rackspace.com/loadbalancers/api/v1.0/clb-devguide/content/GET_listAllowedDomains_v1.0__account__loadbalancers_alloweddomains_allowed_domains.html>`__.

Suppose that you want to add nodes to the load balancer before the services on those nodes are ready to serve traffic. As of right now, the default status for added nodes is ``ONLINE``. The node's status is an immutable attribute, and only health monitoring can change this attribute. So in order to prevent traffic from going to the node, but still allowing the health monitor to perform checks, you can add a node with a ``DRAINING`` condition. Once the backend node is ready to serve traffic, you can then change the condition to ``ENABLED``.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |                         |                         |
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
|422                       |                         |                         |
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








**Example Add Node: JSON request**


.. code::

    {"nodes": [
            {
                "address": "10.2.2.3",
                "port": 80,
                "condition": "ENABLED",
                "type":"PRIMARY"
            },
            {
                "address": "10.2.2.4",
                "port": 81,
                "condition": "ENABLED",
                "type":"SECONDARY"
            },
            {
                "address": "www.myrackspace.com",
                "port": 88,
                "condition": "ENABLED",
                "weight": 10,
                "type":"SECONDARY"
            }
        ]
    }


**Example Add Node: XML request**


.. code::

    <nodes xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <node address="10.1.1.1" port="80" condition="ENABLED" type="PRIMARY"/>
        <node address="10.2.2.1" port="80" condition="ENABLED" type="SECONDARY"/>
        <node address="www.myrackspace.com" port="88" condition="ENABLED" type="SECONDARY" weight="10"/>
    </nodes>


Response
^^^^^^^^^^^^^^^^^^





**Example Add Node: JSON request**


.. code::

    {"nodes": [
        {
            "address": "10.2.2.3",
            "id": 185,
            "port": 80,
            "status": "ONLINE",
            "condition": "ENABLED",
            "weight": 1,
            "type":"PRIMARY"
        },
        {
            "address": "10.2.2.4",
            "id": 186,
            "port": 81,
            "status": "ONLINE",
            "condition": "ENABLED",
            "weight": 1,
            "type":"SECONDARY"
        },
        {
            "address": "www.myrackspace.com",
            "id": 186,
            "port": 88,
            "status": "ONLINE",
            "condition": "ENABLED",
            "weight": 10,
            "type":"SECONDARY"
        }
    ]
    }


**Example Add Node: XML request**


.. code::

    <nodes xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <node
            address="10.1.1.1"
            id="185"
            port="80"
            condition="ENABLED"
            status="ONLINE"
            weight="1"
            type="PRIMARY"/>
        <node
            address="10.2.2.1"
            id="186"
            port="80"
            condition="ENABLED"
            status="ONLINE"
            weight="1"
            type="SECONDARY"/>
        <node
            address="www.myrackspace.com"
            id="186"
            port="80"
            condition="ENABLED"
            status="ONLINE"
            weight="10"
            type="SECONDARY"/>
    </nodes>

