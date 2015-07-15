=============================================================================
Bulk-Delete Nodes -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Bulk-Delete Nodes
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_bulk-delete_nodes_v1.0_account_loadbalancers_loadbalancerid_nodes.rst#request>`__
`Response <DELETE_bulk-delete_nodes_v1.0_account_loadbalancers_loadbalancerid_nodes.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes

Bulk-deletes the specified nodes from a specified load balancer.

To bulk-delete nodes, provide a query parameter list of node IDs (for example: /nodes?id= ``nodeId`` & id= ``nodeId`` ). The current default limit is ten IDs per request. Any and all configuration data is immediately purged and is not recoverable.

This operation is an all or nothing proposition. If one or more of the items in the list cannot be removed due to their current status, a badRequest (400) is returned along with the IDs of the items the system identified as potential failures for this request. In this case, no nodes are deleted, and the user is notified with the specified ID(s) and related error message. Refer to the error response example shown below.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Bulk-delete Nodes Error: |                         |
|                          |JSON response            |                         |
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



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|nodeId                    |xsd:string *(Required)*  |The ID for the specified |
|                          |                         |node.                    |
+--------------------------+-------------------------+-------------------------+







Response
^^^^^^^^^^^^^^^^^^





**Example Bulk-delete Nodes Error: JSON response**


.. code::

    {
       "validationErrors":{
          "messages":[
             "Node ids 100 are not a part of your loadbalancer"
          ]
       },
       "message":"Validation Failure",
       "code":400,
       "details":"The object is not valid"
    }
    

