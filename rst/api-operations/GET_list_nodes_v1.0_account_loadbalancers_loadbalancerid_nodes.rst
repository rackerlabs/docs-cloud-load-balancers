=============================================================================
List Nodes -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Nodes
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_nodes_v1.0_account_loadbalancers_loadbalancerid_nodes.rst#request>`__
`Response <GET_list_nodes_v1.0_account_loadbalancers_loadbalancerid_nodes.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes

Lists nodes that are configured for a specified load balancer.

The ``weight`` attributes are only displayed for load balancers that use the ``WEIGHTED_LEAST_CONNECTIONS`` or ``WEIGHTED_ROUND_ROBIN`` algorithms.



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








Response
^^^^^^^^^^^^^^^^^^





**Example List Nodes: JSON request**


.. code::

    {
        "nodes": [
            {
                "id":410,
                "address":"10.1.1.1",
                "port":80,
                "condition":"ENABLED",
                "status":"ONLINE",
                "weight":3,
                "type":"PRIMARY"
            },
            {
                "id":411,
                "address":"10.1.1.2",
                "port":80,
                "condition":"ENABLED",
                "status":"ONLINE",
                "weight":8,
                "type":"SECONDARY"
            },
            {
                "id":412,
                "address":"10.1.1.3",
                "port":80,
                "condition":"DISABLED",
                "status":"ONLINE",
                "weight":12,
                "type":"SECONDARY"
            }
        ]
    }


**Example List Nodes: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <nodes xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <node
            id="410"
            address="10.1.1.1"
            port="80"
            condition="ENABLED"
            status="ONLINE"
            weight="3"
            type="PRIMARY"/>
        <node
            id="411"
            address="10.1.1.2"
            port="80"
            condition="ENABLED"
            status="ONLINE"
            weight="8"
            type="SECONDARY"/>
        <node
            id="412"
            address="10.1.1.3"
            port="80"
            condition="DISABLED"
            status="ONLINE"
            weight="12"
            type="SECONDARY"/>
    </nodes>

