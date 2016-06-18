
.. _get-show-access-list-v1.0-account-loadbalancers-loadbalancerid-accesslist:

Show access list
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/accesslist

Shows the access list.



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
^^^^^^^^^^^^




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String                   |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
^^^^^^^^^^^^^










**Example Show access list: JSON response**


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


**Example Show access list: XML response**


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

