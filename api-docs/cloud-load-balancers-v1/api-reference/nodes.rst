.. _nodes:

=====
Nodes
=====

.. contents::
   :local:
   :depth: 1

The nodes defined by the load balancer are responsible for
servicing the requests received through the load balancer's virtual IP.
By default, the load balancer employs a basic health check that ensures
the node is listening on its defined port. The node is checked at the
time of addition and at regular intervals as defined by the load
balancer health check configuration. If a back-end node is not listening
on its port or does not meet the conditions of the defined active health
check for the load balancer, then the load balancer does not forward
connections and its ``status`` is listed as ``OFFLINE``. Only nodes with a
``status`` of ``ONLINE`` can receive and service traffic from the load
balancer.

All nodes have an associated ``condition`` that indicates whether the node
is ``ENABLED``, ``DISABLED``, or ``DRAINING``. Nodes that are in
an ``ENABLED`` condition receive and can service traffic from the load balancer.
The ``DISABLED`` condition represents a node that cannot
accept or service traffic. A node in the \ ``DRAINING`` condition
represents a node that stops the traffic manager from sending any
additional *new* connections to the node, but honors established
sessions. If the traffic manager receives a request and session
persistence requires that the node is used, the traffic manager uses it.
As mentioned earlier, the status is determined by the passive or active
health monitors.

..  note::

    Do not confuse the condition of a node with its status. The
    ``condition`` attribute is mutable and gives the user control on how to
    manage requests to the node. The ``status`` attribute is immutable and
    is updated by the load balancing service based on whether or not the
    node *can* service requests.

Table. Load balancer node conditions

+--------------+---------------------------------------------------------------------+
| Name         | Description                                                         |
+==============+=====================================================================+
| ``ENABLED``  | Node is permitted to accept new connections.                        |
+--------------+---------------------------------------------------------------------+
| ``DISABLED`` | Node is not permitted to accept any new connections regardless      |
|              | of session persistence configuration. Existing connections are      |
|              | forcibly terminated.                                                |
+--------------+---------------------------------------------------------------------+
| ``DRAINING`` | Node is allowed to service existing established connections and     |
|              | connections that are being directed to it as a result of the        |
|              | session persistence configuration.                                  |
+--------------+---------------------------------------------------------------------+

A load balancer can have an associated algorithm. If the
``WEIGHTED_ROUND_ROBIN`` load balancer algorithm is selected, then the caller
should assign the relevant weights to the node as part of the weight attribute
of the node element. When the algorithm of the load balancer is changed to
``WEIGHTED_ROUND_ROBIN`` and the nodes do not already have an assigned weight,
the service automatically sets the weight to ``1`` for all nodes. If the
``WEIGHTED_LEAST_CONNECTIONS`` load balancer algorithm is selected, each
request is assigned to a node based on the number of concurrent connections
to the node and its weight. For additional information about the load balancer
algorithms, see :ref:`Algorithms <algorithms>`.

One or more secondary nodes can be added to a specified load balancer so
that if all the primary nodes fail, traffic can be redirected to
secondary nodes. The ``type`` attribute allows configuring the node as
either ``PRIMARY`` or ``SECONDARY``.

..  note::
      The node's IP and port are immutable attributes and cannot be modified
      with a **PUT** request. Supplying an unsupported attribute results in a
      ``400 badRequest fault``. A load balancer supports a maximum of 25 nodes.
      The maximum weight of a node is 100.

Every node in the load balancer has an associated condition which
determines its role within the load balancer.

The following table lists the optional attributes.

..  note::
       *At least one* of the optional attributes is required for the
       :ref:`Update nodes request <put-update-node>`.

Table. Optional attributes

+-----------+---------------------------------------------------------------+----------+
| Name      | Description                                                   | Required |
+===========+===============================================================+==========+
| condition | Condition for the node, which determines its role             |  No      |
|           | within the load balancer.                                     |          |
+-----------+---------------------------------------------------------------+----------+
| type      | Type of node:                                                 |  No      |
|           |                                                               |          |
|           | PRIMARY – Nodes defined as ``PRIMARY`` are in the normal      |          |
|           | rotation to receive traffic from the load balancer.           |          |
|           |                                                               |          |
|           | SECONDARY – Nodes defined as ``SECONDARY`` are only in the    |          |
|           | rotation to receive traffic from the load balancer when       |          |
|           | all the primary nodes fail. This provides a failover          |          |
|           | feature that automatically routes traffic to the secondary    |          |
|           | node in the event that the primary node is disabled or in     |          |
|           | a failing state. Note that active health monitoring must      |          |
|           | be enabled on the load balancer to enable the failover        |          |
|           | feature to the secondary node.                                |          |
+-----------+---------------------------------------------------------------+----------+
| weight    |  Weight of node. If the WEIGHTED_ROUND_ROBIN load             |  No      |
|           |  balancer algorithm is selected, then the user should         |          |
|           |  assign the relevant weight to the node using the weight      |          |
|           |  attribute for the node. Must be an integer from 1 to 100.    |          |
+-----------+---------------------------------------------------------------+----------+


.. include:: methods/get-list-nodes-v1.0-account-loadbalancers-loadbalancerid-nodes.rst
.. include:: methods/post-add-node-v1.0-account-loadbalancers-loadbalancerid-nodes.rst
.. include:: methods/delete-bulk-delete-nodes-v1.0-account-loadbalancers-loadbalancerid-nodes.rst
.. include:: methods/get-show-node-details-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid.rst
.. include:: methods/put-update-node-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid.rst
.. include:: methods/put-bulk-update-nodes-v1.0-account-loadbalancers-loadbalancerid-nodes.rst
.. include:: methods/delete-delete-node-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid.rst
.. include:: methods/get-list-node-service-events-v1.0-account-loadbalancers-loadbalancerid-nodes-events.rst
