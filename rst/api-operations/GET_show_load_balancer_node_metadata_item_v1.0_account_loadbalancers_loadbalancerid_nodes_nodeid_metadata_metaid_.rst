=============================================================================
Show Load Balancer Node Metadata Item -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Load Balancer Node Metadata Item
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_load_balancer_node_metadata_item_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_metadata_metaid_.rst#request>`__
`Response <GET_show_load_balancer_node_metadata_item_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_metadata_metaid_.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}/metadata/{metaId}

Shows details for a specified metadata item for a specified node and load balancer.



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





**Example Show Load Balancer Node Metadata Item: JSON request**


.. code::

    {"meta": {
            "id":4,
            "key":"color",
            "value":"red"
        }
    }


**Example Show Load Balancer Node Metadata Item: XML request**


.. code::

    <meta id="1" key="color">red</meta>

