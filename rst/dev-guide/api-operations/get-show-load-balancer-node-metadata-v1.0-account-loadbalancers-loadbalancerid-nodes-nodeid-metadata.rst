
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Load Balancer Node Metadata -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Load Balancer Node Metadata
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-load-balancer-node-metadata-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid-metadata.html#request>`__
`Response <get-show-load-balancer-node-metadata-v1.0-account-loadbalancers-loadbalancerid-nodes-nodeid-metadata.html#response>`__

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}/metadata

Shows all metadata associated with a specified node and load balancer.



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








Response
^^^^^^^^^^^^^^^^^^





**Example Show Load Balancer Node Metadata: JSON response**


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


**Example Show Load Balancer Node Metadata: XML response**


.. code::

    <metadata xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
      <meta id="1" key="color">red</meta>
      <meta id="2" key="label">web-load-balancer</meta>
    </metadata>

