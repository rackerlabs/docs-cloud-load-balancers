
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Bulk-Delete Load Balancer Node Metadata Items -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Bulk-Delete Load Balancer Node Metadata Items
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <delete-bulk-delete-load-balancer-node-metadata-items-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid-metadata.html#request>`__
`Response <delete-bulk-delete-load-balancer-node-metadata-items-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid-metadata.html#response>`__

.. code::

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}/metadata

Bulk-deletes the metadata items given specified id list.

To bulk-delete metadata, provide a query parameter list of meta IDs. For example: /metadata?id= ``metaId`` & id= ``metaId``. The current default limit is ten IDs per request. Any and all configuration data is immediately purged and is not recoverable. If one of the items in the list cannot be removed due to its current status, a 400:BadRequest is returned along with the IDs of the ones the system identified as potential failures for this request.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
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



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|metaId                    |xsd:string *(Required)*  |The ID for the metadata  |
|                          |                         |item.                    |
+--------------------------+-------------------------+-------------------------+







Response
^^^^^^^^^^^^^^^^^^




