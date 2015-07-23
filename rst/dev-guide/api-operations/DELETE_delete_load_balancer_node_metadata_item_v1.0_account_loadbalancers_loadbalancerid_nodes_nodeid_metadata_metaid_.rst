=============================================================================
Delete Load Balancer Node Metadata Item -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Delete Load Balancer Node Metadata Item
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_delete_load_balancer_node_metadata_item_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_metadata_metaid_.rst#request>`__
`Response <DELETE_delete_load_balancer_node_metadata_item_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_metadata_metaid_.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}/metadata/{metaId}

Deletes a metadata item from the node.

Any and all configuration data is immediately purged and is not recoverable.



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
|{nodeId}                  |xsd:string *(Required)*  |The ID for the node.     |
+--------------------------+-------------------------+-------------------------+
|{metaId}                  |xsd:string *(Required)*  |The ID of the metadata   |
|                          |                         |item.                    |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




