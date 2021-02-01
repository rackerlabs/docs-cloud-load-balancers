.. _get-list-virtual-ips:

List virtual IPs
~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/virtualips

Lists virtual IPs that are associated with a specified load balancer.

The following table shows the possible response codes for this operation:

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
-------

The following table shows the URI parameters for the request:

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
--------


**Example List virtual IPs: JSON response**

.. code::

        {
            "virtualIps": [
                {
                    "address": "172.25.0.17",
                    "id": 17,
                    "type": "PUBLIC",
                    "ipVersion": "IPV4"
                },
                {
                    "address": "fd00:0000:0000:0101:22d6:5749:0000:0011",
                    "id": 17,
                    "type": "PUBLIC",
                    "ipVersion": "IPV6"
                }
            ]
        }

**Example List virtual IPs: XML response**

.. code::

        <virtualIps xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
            <virtualIp id="17" address="172.25.0.17" ipVersion="IPV4" type="PUBLIC"/>
            <virtualIp id="17" address="fd00:0000:0000:0101:22d6:5749:0000:0011" ipVersion="IPV6" type="PUBLIC"/>
        </virtualIps>

**Example List atom virtual IPs: ATOM/XML response**

.. code::

        <feed xmlns="http://www.w3.org/2005/Atom">
            <link rel="next" href="https://staging.ord.loadbalancers.api.rackspacecloud.com/v1.0/5806065/loadbalancers/347763/virtualips.atom?page=2"/>
            <title type="text">Virtual Ips Feed</title>
            <id>5806065-loadbalancers-347763-virtualips</id>
            <author>
                <name>Rackspace Cloud</name>
            </author>
            <entry>
                <title type="text">Virtual Ip Successfully Added</title>
                <summary type="text">Virtual ip successfully added with address: '184.106.24.17', type: 'PUBLIC'</summary>
                <author>
                    <name>cloudUser</name>
                </author>
                <link href="https://staging.ord.loadbalancers.api.rackspacecloud.com/v1.0/5806065/loadbalancers/347763/virtualips/919"/>
                <id>5806065-loadbalancers-347763-virtualips-919-20193501825450</id>
                <category term="CREATE"/>
                <updated>2019-12-16T18:25:45.000Z</updated>
            </entry>
            <entry>
                <title type="text">Virtual Ip Successfully Added</title>
                <summary type="text">Virtual ip successfully added with address: '2001:4801:79f1:0100:22d6:5749:0000:0001', type: 'PUBLIC'</summary>
                <author>
                    <name>cloudUser</name>
                </author>
                <link href="https://staging.ord.loadbalancers.api.rackspacecloud.com/v1.0/5806065/loadbalancers/347763/virtualips/9078732"/>
                <id>5806065-loadbalancers-347763-virtualips-9078732-20193501825450</id>
                <category term="CREATE"/>
                <updated>2019-12-16T18:25:45.000Z</updated>
            </entry>
        </feed>