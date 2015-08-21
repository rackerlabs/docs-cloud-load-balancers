
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

List load balancers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{account}/loadbalancers

Lists load balancers that are configured for the account.

The response object shows a limited set of load balancer attributes, including the following attributes:



*  ``name``
*  ``id``
*  ``status``
*  ``created``
*  ``updated``


Use the changes-since query parameter to list all load balancers that have changed since the specified date/time. For example, using the URI ``/loadbalancers?changes-since=2011-05-19T08:07:08-0500`` lists all load balancers that have changed since May 19th, 2011 at 8:07:08 AM, GMT-5. See `Date and time format <http://docs.rackspace.com/loadbalancers/api/v1.0/clb-devguide/content/Date_Time_Format.html>`__ for information about specifying the date/time.

To view deleted load balancers, add the query parameter ``?status=DELETED`` to the end of the URI. A deleted load balancer is immutable and irrecoverable.

To find out if any load balancer for an account has a specific node attached to it, use the query parameter nodeaddress to specify the IP address or domain name for the desired node. For example, using the URI ``/loadbalancers?nodeaddress=10.1.1.1`` searches all load balancers for the account for a node with IP address 10.1.1.1, and returns a list including the ID, name, and status of all load balancers attached.



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





This operation does not accept a request body.




Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|loadBalancers             |String *(Optional)*      |A ``loadBalancers``      |
|                          |                         |object.                  |
+--------------------------+-------------------------+-------------------------+
|name                      |String *(Optional)*      |Name of the load         |
|                          |                         |balancer to create. The  |
|                          |                         |name must be 128         |
|                          |                         |characters or fewer in   |
|                          |                         |length, and all UTF-8    |
|                          |                         |characters are valid.    |
|                          |                         |See ` http://www.utf8-   |
|                          |                         |chartable.de/            |
|                          |                         |<http://www.utf8-        |
|                          |                         |chartable.de/>`__ for    |
|                          |                         |information about the    |
|                          |                         |UTF-8 character set.     |
+--------------------------+-------------------------+-------------------------+
|id                        |Int *(Optional)*         |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|protocol                  |String *(Optional)*      |Protocol of the service  |
|                          |                         |that is being load       |
|                          |                         |balanced.                |
+--------------------------+-------------------------+-------------------------+
|port                      |String *(Optional)*      |Port number for the      |
|                          |                         |service you are load     |
|                          |                         |balancing.               |
+--------------------------+-------------------------+-------------------------+
|algorithm                 |String *(Optional)*      |Algorithm that defines   |
|                          |                         |how traffic should be    |
|                          |                         |directed between back-   |
|                          |                         |end nodes.               |
+--------------------------+-------------------------+-------------------------+
|status                    |String *(Optional)*      |The status of the load   |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|nodeCount                 |Int *(Optional)*         |The number of load       |
|                          |                         |balancer nodes.          |
+--------------------------+-------------------------+-------------------------+
|created                   |Object *(Optional)*      |The date and time what   |
|                          |                         |the load balancer was    |
|                          |                         |created.                 |
+--------------------------+-------------------------+-------------------------+
|updated                   |Object *(Optional)*      |The date and time what   |
|                          |                         |the load balancer was    |
|                          |                         |last updated.            |
+--------------------------+-------------------------+-------------------------+
|virtualIps                |Object *(Optional)*      |The list of virtualIps   |
|                          |                         |for a load balancer.     |
+--------------------------+-------------------------+-------------------------+
|id                        |Int *(Optional)*         |The ID for the IP        |
|                          |                         |address.                 |
+--------------------------+-------------------------+-------------------------+
|address                   |String *(Optional)*      |The IP address.          |
+--------------------------+-------------------------+-------------------------+
|type                      |String *(Optional)*      |The IP address type. See |
|                          |                         |the Virtual IP Types     |
|                          |                         |table in the Chapter 4   |
|                          |                         |section "Virtual IPs".   |
+--------------------------+-------------------------+-------------------------+
|ipVersion                 |String *(Optional)*      |The IP version.          |
+--------------------------+-------------------------+-------------------------+







**Example List load balancers: JSON response**


.. code::

    {
        "loadBalancers":[
            {
                "name":"lb-site1",
                "id":71,
                "protocol":"HTTP",
                "port":80,
                "algorithm":"RANDOM",
                "status":"ACTIVE",
                "nodeCount":3,
                "virtualIps":[
                    {
                        "id":403,
                        "address":"206.55.130.1",
                        "type":"PUBLIC",
                        "ipVersion":"IPV4"
                    }
                ],
                "created":{
                    "time":"2010-11-30T03:23:42Z"
                },
                "updated":{
                    "time":"2010-11-30T03:23:44Z"
                }
            },
            {
                "name":"lb-site2",
                "id":166,
                "protocol":"HTTP",
                "port":80,
                "algorithm":"RANDOM",
                "status":"ACTIVE",
                "nodeCount":4,
                "virtualIps":[
                    {
                        "id":401,
                        "address":"206.55.130.2",
                        "type":"PUBLIC",
                        "ipVersion":"IPV4"
                    }
                ],
                "created":{
                    "time":"2010-11-30T03:23:42Z"
                },
                "updated":{
                    "time":"2010-11-30T03:23:44Z"
                }
            }
        ]
    }


**Example List load balancers: XML response**


.. code::

    <?xml version="1.0" ?>
    <loadBalancers xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <loadBalancer id="71" name="lb-site1" status="ACTIVE"
            protocol="HTTP" port="80" algorithm="RANDOM" nodeCount="3">
            <virtualIps>
                <virtualIp id="403" address="206.55.130.1" ipVersion="IPV4"
                    type="PUBLIC" />
            </virtualIps>
            <created time="2010-12-13T15:38:27-06:00" />
            <updated time="2010-12-13T15:38:38-06:00" />
        </loadBalancer>
        <loadBalancer id="166" name="lb-site2" status="ACTIVE"
            protocol="HTTP" port="80" algorithm="RANDOM" nodeCount="4">
            <virtualIps>
                <virtualIp id="401" address="206.55.130.2" ipVersion="IPV4"
                    type="PUBLIC" />
            </virtualIps>
            <created time="2010-12-13T15:38:27-06:00" />
            <updated time="2010-12-13T15:38:38-06:00" />
        </loadBalancer>
    </loadBalancers>


**Example List load balancers: Atom response**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next"
              href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers.atom?page=2"/>
        <title type="text">Parent Feed</title>
        <id>1234-loadbalancers</id>
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
    </feed>

