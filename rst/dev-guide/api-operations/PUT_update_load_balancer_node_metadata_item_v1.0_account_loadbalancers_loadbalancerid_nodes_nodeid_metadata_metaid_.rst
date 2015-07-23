=============================================================================
Update Load Balancer Node Metadata Item -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Update Load Balancer Node Metadata Item
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <PUT_update_load_balancer_node_metadata_item_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_metadata_metaid_.rst#request>`__
`Response <PUT_update_load_balancer_node_metadata_item_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_metadata_metaid_.rst#response>`__

.. code-block:: javascript

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}/metadata/{metaId}

Updates the configuration of a metadata item on the node.

The meta data item's id and key are immutable attributes and cannot be modified with a ``PUT`` request. Supplying an unsupported attribute results in a 400 (badRequest) fault. A load balancer and node support a maximum of 25 metadata items.

The following table lists the required and optional attributes:



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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|value                     |xsd:string *(Required)*  |Value for the metadata   |
|                          |                         |item. Must be 256        |
|                          |                         |characters or less. All  |
|                          |                         |UTF-8 characters are     |
|                          |                         |valid.                   |
+--------------------------+-------------------------+-------------------------+





**Example Update Load Balancer Node Metadata Item: JSON request**


.. code::

    {
      "meta": {
        "value":"blue"
      }
    }


**Example Update Load Balancer Node Metadata Item: XML request**


.. code::

    <meta xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">blue</meta>


Response
^^^^^^^^^^^^^^^^^^




