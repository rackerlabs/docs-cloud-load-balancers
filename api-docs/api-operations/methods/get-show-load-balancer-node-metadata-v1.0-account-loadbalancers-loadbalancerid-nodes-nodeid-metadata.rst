
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-show-load-balancer-node-metadata-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid-metadata:

Show load balancer node metadata
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}/metadata

Shows all metadata associated with a specified node and load balancer.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|{nodeId}                  |String *(Required)*      |The ID for the node.     |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Show load balancer node metadata: JSON response**


.. code::

    {
      "metadata": [
        {
          "id":"1",
          "key":"color",
          "value":"red"
        },
        {
          "id":"2",
          "key":"label",
          "value":"web-load-balancer"
        }
      ]
    }


**Example Show load balancer node metadata: XML response**


.. code::

    <metadata xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
      <meta id="1" key="color">red</meta>
      <meta id="2" key="label">web-load-balancer</meta>
    </metadata>

