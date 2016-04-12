
.. _put-update-node-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid:

Update node
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}

Updates the configuration for a specified node on a specified load balancer.

.. note::
   The node's IP, port, and status are immutable attributes and cannot be modified with a ``PUT`` request. Supplying an unsupported attribute results in a 400 (badRequest) fault. A load balancer supports a maximum of 25 nodes; the maximum weight of a node is 100.
   
   

Suppose you want to add nodes to the load balancer before the services on those nodes are ready to serve traffic. As of right now, the default status for added nodes is ``ONLINE``. To get the nodes added without having them serve traffic, you can add a node with a ``DRAINING`` condition, which will prevent traffic from going to the node, but still allow the health monitor to perform checks. Once the backend node is ready to serve traffic, you can change the condition to ``ENABLED``.

Every node in the load balancer has an associated condition which determines its role within the load balancer.



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
|{loadBalancerId}          |String                   |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|{nodeId}                  |String                   |The ID for the node.     |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Update node: JSON request**


.. code::

    {"node":{
            "condition": "ENABLED",
            "weight": 59
        }
    }


**Example Update node: XML request**


.. code::

    <node xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" condition="ENABLED" weight="12"/>


Response
""""""""""""""""






This operation does not return a response body.




