=======================================================================
4.4. Nodes - Rackspace Cloud Load Balancers Developer Guide  - API v1.0
=======================================================================

.. rubric::  4.4. Nodes
   :class: title

`4.4.1. List
nodes <GET_listNodes_v1.0__account__loadbalancers__loadBalancerId__nodes_Nodes-d1e2173.html>`__
`4.4.2. Add
node <POST_addNode_v1.0__account__loadbalancers__loadBalancerId__nodes_Nodes-d1e2173.html>`__
`4.4.3. Bulk-delete
nodes <DELETE_bulkDeleteNodes_v1.0__account__loadbalancers__loadBalancerId__nodes_Nodes-d1e2173.html>`__
`4.4.4. Show node
details <GET_showNode_v1.0__account__loadbalancers__loadBalancerId__nodes__nodeId__Nodes-d1e2173.html>`__
`4.4.5. Update
node <PUT_updateNode_v1.0__account__loadbalancers__loadBalancerId__nodes__nodeId__Nodes-d1e2173.html>`__
`4.4.6. Delete
node <DELETE_deleteNode_v1.0__account__loadbalancers__loadBalancerId__nodes__nodeId__Nodes-d1e2173.html>`__
`4.4.7. List node service
events <GET_listNodeEvents_v1.0__account__loadbalancers__loadBalancerId__nodes_events_Nodes-d1e2173.html>`__

The `nodes <#>`__ defined by the load balancer are responsible for
servicing the requests received through the load balancer's virtual IP.
By default, the load balancer employs a basic health check that ensures
the node is listening on its defined port. The node is checked at the
time of addition and at regular intervals as defined by the load
balancer health check configuration. If a back-end node is not listening
on its port or does not meet the conditions of the defined active health
check for the load balancer, then the load balancer does not forward
connections and its status is listed as ``OFFLINE``. Only nodes that are
in an ``ONLINE`` status receive and can service traffic from the load
balancer.

All nodes have an associated condition that indicates whether the node
is ``ENABLED``, ``DISABLED``, or ``DRAINING``. Nodes that are in
an \ ``ENABLED`` condition receive and can service traffic from the load
balancer. The ``DISABLED`` condition represents a node that cannot
accept or service traffic. A node in the \ ``DRAINING`` condition
represents a node that stops the traffic manager from sending any
additional *new* connections to the node, but honors established
sessions. If the traffic manager receives a request and session
persistence requires that the node is used, the traffic manager uses it.
As mentioned earlier, the status is determined by the passive or active
health monitors.

..  note:: 
Note
Do not confuse the condition of a node with its status. The
``condition`` attribute is mutable and gives the user control on how to
manage requests to the node. The ``status`` attribute is immutable and
is updated by the load balancing service based on whether or not the
node *can* service requests.

If the ``WEIGHTED_ROUND_ROBIN`` load balancer algorithm mode is
selected, then the caller should assign the relevant weights to the node
as part of the weight attribute of the node element. When the algorithm
of the load balancer is changed to ``WEIGHTED_ROUND_ROBIN`` and the
nodes do not already have an assigned weight, the service automatically
sets the weight to ``1`` for all nodes.

One or more secondary nodes can be added to a specified load balancer so
that if all the primary nodes fail, traffic can be redirected to
secondary nodes. The type attribute allows configuring the node as
either ``PRIMARY`` or ``SECONDARY``.

..  note:: 
Note
The node's IP and port are immutable attributes and cannot be modified
with a **PUT** request. Supplying an unsupported attribute results in a
400 (badRequest) fault. A load balancer supports a maximum of 25 nodes;
the maximum weight of a node is 100.

Every node in the load balancer has an associated condition which
determines its role within the load balancer.

The following table lists the required and optional attributes:

Table 4.3. Required and optional attributes
Name
Description
Required
condition
Condition for the node, which determines its role within the load
balancer.
No
type
Type of node:

-  ``PRIMARY`` – Nodes defined as ``PRIMARY`` are in the normal rotation
   to receive traffic from the load balancer.

-  ``SECONDARY`` – Nodes defined as ``SECONDARY`` are only in the
   rotation to receive traffic from the load balancer when all the
   primary nodes fail. This provides a failover feature that
   automatically routes traffic to the secondary node in the event that
   the primary node is disabled or in a failing state. Note that active
   health monitoring must be enabled on the load balancer to enable the
   failover feature to the secondary node.

No
weight
Weight of node. If the WEIGHTED\_ROUND\_ROBIN load balancer algorithm
mode is selected, then the user should assign the relevant weight to the
node using the weight attribute for the node. Must be an integer from 1
to 100.
No

..  note:: 
Note
*At least one* of the optional attributes is required for the Modify
Nodes request.

Table 4.4. Load balancer node conditions
Name
Description
``ENABLED``
Node is permitted to accept new connections.
``DISABLED``
Node is not permitted to accept any new connections regardless of
session persistence configuration. Existing connections are forcibly
terminated.
``DRAINING``
Node is allowed to service existing established connections and
connections that are being directed to it as a result of the session
persistence configuration.
+---------+------------------------------+--------------------------------------+
| Method  | URI                          | Description                          |
+=========+==============================+======================================+
| **GET** | ``/v1.0/{account}/loadbalanc | Lists nodes that are configured for  |
|         | ers/{loadBalancerId}/nodes`` | a specified load balancer.           |
+---------+------------------------------+--------------------------------------+
| **POST* | ``/v1.0/{account}/loadbalanc | Adds a node to a specified load      |
| *       | ers/{loadBalancerId}/nodes`` | balancer.                            |
+---------+------------------------------+--------------------------------------+
| **DELET | ``/v1.0/{account}/loadbalanc | Bulk-deletes the specified nodes     |
| E**     | ers/{loadBalancerId}/nodes​{ | from a specified load balancer.      |
|         | ?nodeId}``                   |                                      |
+---------+------------------------------+--------------------------------------+
| **GET** | ``/v1.0/{account}/loadbalanc | Show details for a specified node.   |
|         | ers/{loadBalancerId}/nodes/{ |                                      |
|         | nodeId}``                    |                                      |
+---------+------------------------------+--------------------------------------+
| **PUT** | ``/v1.0/{account}/loadbalanc | Updates the configuration for a      |
|         | ers/{loadBalancerId}/nodes/{ | specified node on a specified load   |
|         | nodeId}``                    | balancer.                            |
+---------+------------------------------+--------------------------------------+
| **DELET | ``/v1.0/{account}/loadbalanc | Deletes a node from a specified load |
| E**     | ers/{loadBalancerId}/nodes/{ | balancer.                            |
|         | nodeId}``                    |                                      |
+---------+------------------------------+--------------------------------------+
| **GET** | ``/v1.0/{account}/loadbalanc | Lists node service events.           |
|         | ers/{loadBalancerId}/nodes/e |                                      |
|         | vents``                      |                                      |
+---------+------------------------------+--------------------------------------+
