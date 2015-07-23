=============================================================================
Show Access List -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Access List
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_access_list_v1.0_account_loadbalancers_loadbalancerid_accesslist.rst#request>`__
`Response <GET_show_access_list_v1.0_account_loadbalancers_loadbalancerid_accesslist.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/accesslist

Shows the access list.



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





**Example Show Access List: JSON request**


.. code::

    {
        "accessList": [
            {
                "address": "206.160.163.21",
                "id": 23,
                "type": "DENY"
            },
            {
                "address": "206.160.165.11",
                "id": 24,
                "type": "DENY"
            },
            {
                "address": "206.160.163.21",
                "id": 25,
                "type": "DENY"
            },
            {
                "address": "206.160.165.11",
                "id": 26,
                "type": "DENY"
            },
            {
                "address": "206.160.123.11",
                "id": 27,
                "type": "DENY"
            },
            {
                "address": "206.160.122.21",
                "id": 28,
                "type": "DENY"
            },
            {
                "address": "206.140.123.11",
                "id": 29,
                "type": "DENY"
            },
            {
                "address": "206.140.122.21",
                "id": 30,
                "type": "DENY"
            }
        ]
    }


**Example Show Access List: XML request**


.. code::

    <accessList xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <networkItem
            id="1000"
            address="206.160.165.40"
            type="ALLOW" />
        <networkItem
            id="1001"
            address="206.160.165.0/24"
            type="DENY" />
    </accessList>


**Example Show atom access list: XML response**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next"
              href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/accesslist.atom?page=2"/>
        <title type="text">Access List Feed</title>
        <id>1234-loadbalancers-141-accesslist</id>
        <author>
            <name>Rackspace Cloud</name>
        </author>
        <entry>
            <title type="text">Access List Updated</title>
            <summary
                    type="text">Access list successfully updated with the following network item: id: '2155', address: '206.160.163.210', type: 'DENY'
            </summary>
            <author>
                <name>tvardema</name>
            </author>
            <link href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/accesslist/"/>
            <id>1234-loadbalancers-141-accesslist-2011971658310</id>
            <category term="UPDATE"/>
            <updated>2011-04-07T16:58:31.000Z</updated>
        </entry>
        <entry>
            <title type="text">Access List Updated</title>
            <summary
                    type="text">Access list successfully updated with the following network item: id: '2156', address: '206.160.165.110', type: 'DENY'
            </summary>
            <author>
                <name>tvardema</name>
            </author>
            <link href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/accesslist/"/>
            <id>1234-loadbalancers-141-accesslist-2011971658310</id>
            <category term="UPDATE"/>
            <updated>2011-04-07T16:58:31.000Z</updated>
        </entry>
    </feed>

