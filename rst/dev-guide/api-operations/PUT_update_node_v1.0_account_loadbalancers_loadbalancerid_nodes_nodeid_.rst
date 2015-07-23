=============================================================================
Update Node -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Update Node
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <PUT_update_node_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_.rst#request>`__
`Response <PUT_update_node_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_.rst#response>`__

.. code-block:: javascript

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}

Updates the configuration for a specified node on a specified load balancer.

The node's IP, port, and status are immutable attributes and cannot be modified with a ``PUT`` request. Supplying an unsupported attribute results in a 400 (badRequest) fault. A load balancer supports a maximum of 25 nodes; the maximum weight of a node is 100.

Suppose you want to add nodes to the load balancer before the services on those nodes are ready to serve traffic. As of right now, the default status for added nodes is ``ONLINE``. To get the nodes added without having them serve traffic, you can add a node with a ``DRAINING`` condition, which will prevent traffic from going to the node, but still allow the health monitor to perform checks. Once the backend node is ready to serve traffic, you can change the condition to ``ENABLED``.

Every node in the load balancer has an associated condition which determines its role within the load balancer.



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
|{nodeId}                  |xsd:string *(Required)*  |The ID for the node.     |
+--------------------------+-------------------------+-------------------------+








**Example Update Node: JSON request**


.. code::

    {"node":{
            "condition": "ENABLED",
            "weight": 59
        }
    }


**Example Update Node: XML request**


.. code::

    <node xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" condition="ENABLED" weight="12"/>


Response
^^^^^^^^^^^^^^^^^^




