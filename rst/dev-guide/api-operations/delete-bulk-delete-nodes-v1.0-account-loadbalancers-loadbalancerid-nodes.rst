
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _api-operations-delete-bulk-delete-nodes-v1.0-account-loadbalancers-loadbalancerid-nodes:

Bulk-delete nodes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes

Bulk-deletes the specified nodes from a specified load balancer.

To bulk-delete nodes, provide a query parameter list of node IDs (for example: /nodes?id= ``nodeId`` & id= ``nodeId`` ). The current default limit is ten IDs per request. Any and all configuration data is immediately purged and is not recoverable. 

This operation is an all or nothing proposition. If one or more of the items in the list cannot be removed due to their current status, a badRequest (400) is returned along with the IDs of the items the system identified as potential failures for this request. In this case, no nodes are deleted, and the user is notified with the specified ID(s) and related error message. Refer to the error response example shown below.



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
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|nodeId                    |String *(Optional)*      |The ID for the specified |
|                          |                         |node.                    |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




Response
""""""""""""""""










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
    

