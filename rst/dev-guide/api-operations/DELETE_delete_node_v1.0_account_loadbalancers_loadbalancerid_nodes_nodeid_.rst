=============================================================================
Delete Node -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Delete Node
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_delete_node_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_.rst#request>`__
`Response <DELETE_delete_node_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}

Deletes a node from a specified load balancer.

To bulk-delete nodes, provide a query parameter list of node IDs (for example: /nodes?id= ``nodeId`` & id= ``nodeId`` ). The current default limit is ten IDs per request. Any and all configuration data is immediately purged and is not recoverable. If one of the items in the list cannot be removed due to its current status a 400:BadRequest is returned along with the IDs of the ones the system identified as potential failures for this request.



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








Response
^^^^^^^^^^^^^^^^^^




