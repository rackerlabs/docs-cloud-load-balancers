.. _put-update-nodes:

Update nodes
~~~~~~~~~~~~

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes

Updates the configuration for specified list of nodes on a specified load balancer.

.. note::
   The node's IP, port, and status are immutable attributes and cannot be
   modified with a ``PUT`` request. Supplying an unsupported attribute results
   in a 400 (badRequest) fault. A load balancer supports a maximum of 25 nodes;
   the maximum weight of a node is 100.

Suppose you want to add nodes to the load balancer before the services on those
nodes are ready to serve traffic. As of right now, the default status for added
nodes is ``ONLINE``. To get the nodes added without having them serve traffic,
you can add a node with a ``DRAINING`` condition, which will prevent traffic
from going to the node, but still allow the health monitor to perform checks.
Once the backend node is ready to serve traffic, you can change the condition
to ``ENABLED``.

Every node in the load balancer has an associated condition which determines
its role within the load balancer.

The following table shows the possible response codes for this operation:

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

The following table shows the body parameters for the ``node`` object for the
request.

..  note::

    At least one* of the optional parameters listed in the table is required.

+------------------+-------------+--------------------------------------------+
| **Parameter**    | Type        | Description                                |
+==================+=============+============================================+
| **nodeId**       | Integer     |The ID for the node.                        |
| (*Required*)     |             |                                            |
+------------------+-------------+--------------------------------------------+
| **condition**    | String      | Indicates if the node is ``ENABLED``,      |
| (*Optional*)     |             | ``DISABLED``, or ``DRAINING``. For more    |
|                  |             | information, see :ref:`Nodes <nodes>`.     |
+------------------+-------------+--------------------------------------------+
| **weight**       | Integer     | Indicates the ``weight`` for the node.     |
| (*Optional*)     |             | You can specify ``weight`` or change       |
|                  |             | ``weight`` for an existing node even when  |
|                  |             | the load balancer is not using a weighted  |
|                  |             | algorithm (WEIGHTED_LEAST_CONNECTIONS or   |
|                  |             | WEIGHTED_ROUND_ROBIN). When a load balancer|
|                  |             | is not using a weighted algorithm, a node's|
|                  |             | weight is stored and ignored. However, if  |
|                  |             | the load balancer is changed to a weighted |
|                  |             | algorithm, the weight is used. For more    |
|                  |             | information, see :ref:`Nodes <nodes>`.     |
+------------------+-------------+--------------------------------------------+
| **type**         | String      | The node type. For more information, see   |
| (*Optional*)     |             | :ref:`Nodes <nodes>`.                      |
+------------------+-------------+--------------------------------------------+

**Example Update nodes: JSON request**

.. code::

    {
        "nodes": [
            {
                "condition":"ENABLED",
                "id":50,
                "type":"PRIMARY",
                "weight":1
            },
            {
                "condition":"ENABLED",
                "id":51,
                "type":"PRIMARY",
                "weight":1
            }
        ]
    }

Response
--------

.. code::

    {
        "nodes": [
            {
                "status": "ONLINE",
                "metadata": [],
                "address": "10.176.197.163",
                "id": 50,
                "type": "PRIMARY",
                "port": 80,
                "weight": 1,
                "condition": "ENABLED"
            },
            {
                "status": "ONLINE",
                "metadata": [],
                "address": "10.176.194.38",
                "id": 51,
                "type": "PRIMARY",
                "port": 80,
                "weight": 1,
                "condition": "ENABLED"
            }
        ]
    }
