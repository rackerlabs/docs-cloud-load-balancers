=============================================================================
Show Node Details -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Node Details
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_node_details_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_.rst#request>`__
`Response <GET_show_node_details_v1.0_account_loadbalancers_loadbalancerid_nodes_nodeid_.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/{nodeId}

Show details for a specified node.

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
|{nodeId}                  |xsd:string *(Required)*  |The ID for the node.     |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Show Node Details: JSON request**


.. code::

    {"node": {
            "id":410,
            "address":"10.1.1.1",
            "port":80,
            "condition":"ENABLED",
            "status":"ONLINE",
            "weight":12,
            "type":"PRIMARY"
        }
    }


**Example Show Node Details: XML request**


.. code::

    <node
        id="410"
        address="10.1.1.1"
        port="80"
        condition="ENABLED"
        status="ONLINE"
        weight="12"
        type="PRIMARY"/>


**Example Show Node Details: JSON request**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next"
              href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/nodes/18536.atom?page=2"/>
        <title type="text">Node Feed</title>
        <id>1234-loadbalancers-141-nodes-18536</id>
        <author>
            <name>Rackspace Cloud</name>
        </author>
        <entry>
            <title type="text">Node Status Updated</title>
            <summary type="text">Node '18536' status changed to 'OFFLINE' for load balancer '141'</summary>
            <author>
                <name>Rackspace Cloud</name>
            </author>
            <link href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/nodes/18536"/>
            <id>1234-loadbalancers-141-nodes-18536-201195217490</id>
            <category term="UPDATE"/>
            <updated>2011-04-05T21:07:49.000Z</updated>
        </entry>
    </feed>

