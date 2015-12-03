
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-show-load-balancer-details-v1.0-account-loadbalancers-loadbalancerid:

Show load balancer details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}

Shows details for a specified load balancer.

This operation provides detailed output for a specific load balancer configured and associated with your account. This operation is not capable of returning details for a load balancer which has been deleted.

Notice in the following examples that API users are now able to programmatically derive the source IP addresses of our load balancers using the ``sourceAddresses`` label included at the bottom of the list load balancer details response. This feature is useful for customers who are automating the deployment of infrastructure and need to determine the IP addresses of requests coming from our load balancers for the purpose of creating more robust firewall rules.



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
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
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
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|loadBalancer              |String *(Required)*      |A ``loadBalancer``       |
|                          |                         |object.                  |
+--------------------------+-------------------------+-------------------------+
|id                        |Int *(Required)*         |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|protocol                  |String *(Required)*      |Protocol of the service  |
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
|status                    |String *(Required)*      |The status of the load   |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+
|timeout                   |String *(Optional)*      |The timeout value for    |
|                          |                         |the load balancer and    |
|                          |                         |communications with its  |
|                          |                         |nodes. Defaults to 30    |
|                          |                         |seconds with a maximum   |
|                          |                         |of 120 seconds.          |
+--------------------------+-------------------------+-------------------------+
|connectionLogging         |String *(Optional)*      |Current connection       |
|                          |                         |logging configuration.   |
|                          |                         |Refer to the API Ops     |
|                          |                         |section "Log             |
|                          |                         |connections" for         |
|                          |                         |information and examples.|
+--------------------------+-------------------------+-------------------------+
|virtualIps                |Object *(Required)*      |Type of virtualIp to add |
|                          |                         |with the creation of a   |
|                          |                         |load balancer. See the   |
|                          |                         |virtual IP types table   |
|                          |                         |in the API Ops section   |
|                          |                         |"Virtual IPs".           |
+--------------------------+-------------------------+-------------------------+
|id                        |Int *(Required)*         |The ID for the IP        |
|                          |                         |address.                 |
+--------------------------+-------------------------+-------------------------+
|address                   |String *(Required)*      |The IP address.          |
+--------------------------+-------------------------+-------------------------+
|type                      |String *(Required)*      |The IP address type.     |
+--------------------------+-------------------------+-------------------------+
|ipVersion                 |String *(Required)*      |The IP version.          |
+--------------------------+-------------------------+-------------------------+
|nodes                     |Object *(Optional)*      |Nodes to be added to the |
|                          |                         |load balancer.           |
+--------------------------+-------------------------+-------------------------+
|address                   |String *(Required)*      |The node address.        |
+--------------------------+-------------------------+-------------------------+
|port                      |Int *(Required)*         |The node port.           |
+--------------------------+-------------------------+-------------------------+
|condition                 |String *(Required)*      |The node condition. For  |
|                          |                         |example, ENABLED.        |
+--------------------------+-------------------------+-------------------------+
|status                    |String *(Required)*      |The node status. For     |
|                          |                         |example, ONLINE.         |
+--------------------------+-------------------------+-------------------------+
|sessionPersistence        |String *(Optional)*      |Specifies whether        |
|                          |                         |multiple requests from   |
|                          |                         |clients are directed to  |
|                          |                         |the same node.           |
+--------------------------+-------------------------+-------------------------+
|connectionThrottle        |String *(Optional)*      |Specifies limits on the  |
|                          |                         |number of connections    |
|                          |                         |per IP address to help   |
|                          |                         |mitigate malicious or    |
|                          |                         |abusive traffic to your  |
|                          |                         |applications. Refer to   |
|                          |                         |the API Ops section      |
|                          |                         |"Throttle connections"   |
|                          |                         |for information and      |
|                          |                         |examples.                |
+--------------------------+-------------------------+-------------------------+
|cluster                   |String *(Required)*      |The cluster name.        |
+--------------------------+-------------------------+-------------------------+
|created                   |Object *(Required)*      |The date and time what   |
|                          |                         |the load balancer was    |
|                          |                         |created.                 |
+--------------------------+-------------------------+-------------------------+
|updated                   |Object *(Required)*      |The date and time what   |
|                          |                         |the load balancer was    |
|                          |                         |last updated.            |
+--------------------------+-------------------------+-------------------------+
|sourceAddresses           |Dict *(Required)*        |The source public and    |
|                          |                         |private IP addresses.    |
+--------------------------+-------------------------+-------------------------+







**Example Show load balancer details: JSON response**


.. code::

    {
        "loadBalancer":{
            "id": 2000,
            "name":"sample-loadbalancer",
            "protocol":"HTTP",
            "port": 80,
            "algorithm":"RANDOM",
            "status":"ACTIVE",
            "timeout": 30,
            "connectionLogging":{
                "enabled":true
            },
            "virtualIps":[
                {
                    "id": 1000,
                    "address":"206.10.10.210",
                    "type":"PUBLIC",
                    "ipVersion":"IPV4"
                }
            ],
            "nodes":[
                {
                    "id": 1041,
                    "address":"10.1.1.1",
                    "port": 80,
                    "condition":"ENABLED",
                    "status":"ONLINE"
                },
                {
                    "id": 1411,
                    "address":"10.1.1.2",
                    "port": 80,
                    "condition":"ENABLED",
                    "status":"ONLINE"
                }
            ],
            "sessionPersistence":{
                "persistenceType":"HTTP_COOKIE"
            },
            "connectionThrottle":{
                "minConnections": 10,
                "maxConnections": 100,
                "maxConnectionRate": 50,
                "rateInterval": 60
            },
            "cluster":{
                "name":"c1.dfw1"
            },
            "created":{
                "time":"2010-11-30T03:23:42Z"
            },
            "updated":{
                "time":"2010-11-30T03:23:44Z"
            },
            "sourceAddresses":{"ipv6Public":"2001:4801:79f1:1::1/64","ipv4Servicenet":"10.0.0.0","ipv4Public":"10.12.99.28"}
        }
    }


**Example Show load balancer details: XML response**


.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        id="2000"
        name="sample-loadbalancer"
        protocol="HTTP"
        port="80"
        algorithm="RANDOM"
        status="ACTIVE"
        timeout="30">
        <connectionLogging enabled="false" />
        <virtualIps>
            <virtualIp
                id="1000"
                address="206.10.10.210"
                type="PUBLIC"
                ipVersion="IPV4" />
        </virtualIps>
        <nodes>
            <node
                id="1041"
                address="10.1.1.1"
                port="80"
                condition="ENABLED"
                status="ONLINE" />
            <node
                id="1411"
                address="10.1.1.2"
                port="80"
                condition="ENABLED"
                status="ONLINE" />
        </nodes>
        <sessionPersistence persistenceType="HTTP_COOKIE"/>
        <connectionThrottle
            minConnections="10"
            maxConnections="100"
            maxConnectionRate="50"
            rateInterval="60" />
        <cluster name="c1.dfw1" />
        <created time="2010-11-30T03:23:42Z" />
        <updated time="2010-11-30T03:23:44Z" />
        <sourceAddresses ipv4Servicenet="10.0.0.0" ipv4Public="10.12.99.28" ipv6Public="2001:4801:79f1:1::1/64"/>
    </loadBalancer>


**Example Show atom load balancer details: ATOM/XML response**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next"
              href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141.atom?page=2"/>
        <title type="text">Load Balancer Feed</title>
        <id>1234-loadbalancers-141</id>
        <author>
            <name>Rackspace Cloud</name>
        </author>
        <entry>
            <title type="text">Load Balancer Successfully Updated</title>
            <summary
                    type="text">Load balancer successfully updated with algorithm: 'RANDOM', protocol: 'HTTP', port: '80''
            </summary>
            <author>
                <name>tvardema</name>
            </author>
            <link href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141"/>
            <id>1234-loadbalancers-141-2011961339450</id>
            <category term="UPDATE"/>
            <updated>2011-04-06T13:39:45.000Z</updated>
        </entry>
    </feed>

