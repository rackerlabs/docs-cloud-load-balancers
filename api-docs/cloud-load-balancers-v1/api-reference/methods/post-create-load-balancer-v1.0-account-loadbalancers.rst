
.. _post-create-load-balancer-v1.0-account-loadbalancers:

Create load balancer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v1.0/{account}/loadbalancers

Creates a load balancer with the configuration defined by the request.

This operation asynchronously provisions a new load balancer based on the configuration defined in the request object. Once the request is validated and progress has started on the provisioning process, a response object is returned. The object contains a unique ID and status of the request. Using the ID, the caller can check on the progress of the operation by performing a ``GET`` on ``loadbalancers/id``. If the corresponding request cannot be fulfilled due to insufficient or invalid data, an ``HTTP`` 400 (Bad Request) error response is returned with information regarding the nature of the failure in the body of the response. Failures in the validation process are non-recoverable and require the caller to correct the cause of the failure and ``POST`` the request again.

An HTTP load balancer has the X-Forwarded-For (XFF) HTTP header set by default. This header contains the actual originating IP address of a client connecting to a web server through an HTTP proxy or load balancer, which many web applications are already designed to use when determining the source address for a request. (This header is also included on the Modify Load Balancer request if the protocol changes to re-enable it.)

An HTTP load balancer also includes the X-Forwarded-Proto (XFP) HTTP header, which has been added for identifying the originating protocol of an HTTP request as "http" or "https" depending on what protocol the client requested. This is specially useful when using SSL termination.

An HTTP load balancer also includes the X-Forwarded-Port HTTP header, which has been added for being able to generate secure URLs containing the specified port. This header, along with the X-Forwarded-For header, provide the needed information to the underlying application servers.

.. note::
   The headers listed here (X-Forwarded-For, X-Forwarded-Proto, and X-Forwarded-Port) are available for HTTP load balancers with or without SSL termination enabled, however HTTPS load balancers do not provide these header elements due to encryption.
   
 
The following table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
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
^^^^^^^^^^^^^   
The following table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+   

The following table shows the body parameters for the request:

+--------------------+-------------------+-------------------------------------+
|Name                |Type               |Description                          |
+====================+===================+=====================================+
|name                |String *(Required)*|Name of the load balancer to create. |
|                    |                   |The name must be 128 characters or   |
|                    |                   |fewer in length, and all UTF-8       |
|                    |                   |characters are valid. See            |
|                    |                   |`http://www.utf8-chartable.de/       |
|                    |                   |<http://www.utf8-chartable.de/>`_    |
|                    |                   |for information about the UTF-8      |
|                    |                   |character set.                       |
+--------------------+-------------------+-------------------------------------+
|nodes               |Object             |Nodes to be added to the load        |
|                    |                   |balancer.                            |
+--------------------+-------------------+-------------------------------------+
|protocol            |String *(Required)*|Protocol of the service that is      |
|                    |                   |being load balanced.                 |
+--------------------+-------------------+-------------------------------------+
|halfClosed          |Boolean            |Enables or disables Half-Closed      |
|                    |                   |support for the load balancer. Half- |
|                    |                   |Closed support provides the ability  |
|                    |                   |for one end of the connection to     |
|                    |                   |terminate its output, while still    |
|                    |                   |receiving data from the other end.   |
|                    |                   |Only available for                   |
|                    |                   |TCP/TCP_CLIENT_FIRST protocols.      |
+--------------------+-------------------+-------------------------------------+
|virtualIps          |Object *(Required)*|Type of virtualIp to add with the    |
|                    |                   |creation of a load balancer. See the |
|                    |                   |virtual IP types table at            |
|                    |                   |:ref:`virtual-ips`.                  |
+--------------------+-------------------+-------------------------------------+
|accessList          |String             |The access list management feature   |
|                    |                   |allows fine-grained network access   |
|                    |                   |controls to be applied to the load   |
|                    |                   |balancer virtual IP address. Refer   |
|                    |                   |to :ref:`access-lists`               |
|                    |                   |for information and examples.        |
+--------------------+-------------------+-------------------------------------+
|algorithm           |String             |Algorithm that defines how traffic   |
|                    |                   |should be directed between back-end  |
|                    |                   |nodes.                               |
+--------------------+-------------------+-------------------------------------+
|connectionLogging   |String             |Current connection logging           |
|                    |                   |configuration. Refer to              |
|                    |                   |:ref:`log-connections`               |
|                    |                   |for information and examples.        |
+--------------------+-------------------+-------------------------------------+
|connectionThrottle  |String             |Specifies limits on the number of    |
|                    |                   |connections per IP address to help   |
|                    |                   |mitigate malicious or abusive        |
|                    |                   |traffic to your applications. See    |
|                    |                   |:ref:`throttle-connections`          |
|                    |                   |for information and examples.        |
+--------------------+-------------------+-------------------------------------+
|healthMonitor       |String             |The type of health monitor check to  |
|                    |                   |perform to ensure that the service   |
|                    |                   |is performing properly.              |
+--------------------+-------------------+-------------------------------------+
|metadata            |String             |Information (metadata) that can be   |
|                    |                   |associated with each load balancer.  |
+--------------------+-------------------+-------------------------------------+
|port                |String             |Port number for the service you are  |
|                    |                   |load balancing.                      |
+--------------------+-------------------+-------------------------------------+
|timeout             |String             |The timeout value for the load       |
|                    |                   |balancer and communications with its |
|                    |                   |nodes. Defaults to 30 seconds with a |
|                    |                   |maximum of 120 seconds.              |
+--------------------+-------------------+-------------------------------------+
|sessionPersistence  |String             |Specifies whether multiple requests  |
|                    |                   |from clients are directed to the     |
|                    |                   |same node.                           |
+--------------------+-------------------+-------------------------------------+
|httpsRedirect       |Boolean            |Enables or disables HTTP to HTTPS    |
|                    |                   |redirection for the load balancer.   |
|                    |                   |When enabled, any HTTP request       |
|                    |                   |returns status code 301 (Moved       |
|                    |                   |Permanently), and the requester is   |
|                    |                   |redirected to the requested URL via  |
|                    |                   |the HTTPS protocol on port 443. For  |
|                    |                   |example,                             |
|                    |                   |`http://example.com/page.html        |
|                    |                   |<http://example.com/page.html>`__    |
|                    |                   |would be redirected to               |
|                    |                   |`https://example.com/page.html       |
|                    |                   |<https://example.com/page.html>`__.  |
|                    |                   |Only available for HTTPS protocol (  |
|                    |                   |``port=443`` ), or HTTP protocol     |
|                    |                   |with a properly configured SSL       |
|                    |                   |termination (                        |
|                    |                   |``secureTrafficOnly=true``,          |
|                    |                   |``securePort=443`` ). Note that SSL  |
|                    |                   |termination for a load balancer can  |
|                    |                   |only be configured after the load    |
|                    |                   |balancer has been created.           |
+--------------------+-------------------+-------------------------------------+   

**Example Create load balancer: JSON request**


.. code::

    {
        "loadBalancer": {
            "name": "a-new-loadbalancer",
            "port": 80,
            "protocol": "HTTP",
            "virtualIps": [
                {
                    "type": "PUBLIC"
                }
            ],
            "nodes": [
                {
                    "address": "10.1.1.1",
                    "port": 80,
                    "condition": "ENABLED"
                }
            ]
        }
    }


**Example Create load balancer: XML request**


.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        name="a-new-loadbalancer"
        port="80"
        protocol="HTTP">
        <virtualIps>
            <virtualIp type="PUBLIC"/>
        </virtualIps>
        <nodes>
            <node address="10.1.1.1" port="80" condition="ENABLED"/>
        </nodes>
    </loadBalancer>


**Example Create load balancer with shared IP: JSON request**


.. code::

    {
        "loadBalancer":{
            "name":"a-new-loadbalancer",
            "port":80,
            "protocol":"HTTP",
            "virtualIps":[
                {
                    "id":2341
                }
            ],
            "nodes":[
                {
                    "address":"10.1.1.1",
                    "port":80,
                    "condition":"ENABLED"
                }
            ]
        }
    }


**Example Create load balancer with shared IP: XML request**


.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        name="a-new-loadbalancer"
        port="80"
        protocol="HTTP">
        <virtualIps>
            <virtualIp id="2341"/>
        </virtualIps>
        <nodes>
            <node address="10.1.1.1" port="80" condition="ENABLED" />
        </nodes>
    </loadBalancer>


**Example Create load balancer with IPv4/IPv6: JSON request**


.. code::

    {
        "loadBalancer":{
            "name":"a-new-loadbalancer",
            "port":80,
            "protocol":"HTTP",
            "virtualIps":[
                {
                    "id":2341
                },
                {
                    "id":900001
                }
            ],
            "nodes":[
                {
                    "address":"10.1.1.1",
                    "port":80,
                    "condition":"ENABLED"
                }
            ]
        }
    }


**Example Create load balancer with IPv4/IPv6: XML request**


.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        name="a-new-loadbalancer"
        port="80"
        protocol="HTTP">
        <virtualIps>
            <virtualIp id="2341"/>
            <virtualIp id="900001"/>
        </virtualIps>
        <nodes>
            <node address="10.1.1.1" port="80" condition="ENABLED" />
        </nodes>
    </loadBalancer>


Response
^^^^^^^^^^^^^   

The following table shows the body parameters for the response:

+--------------------------+-------------------------+---------------------------+
|Name                      |Type                     |Description                |
+==========================+=========================+===========================+
|loadBalancer              |String                   |A ``loadBalancer``         |
|                          |                         |object.                    |
+--------------------------+-------------------------+---------------------------+
|id                        |Int                      |The ID for the load        |
|                          |                         |balancer.                  |
+--------------------------+-------------------------+---------------------------+
|protocol                  |String                   |Protocol of the service    |
|                          |                         |that is being load         |
|                          |                         |balanced.                  |
+--------------------------+-------------------------+---------------------------+
|port                      |String                   |Port number for the        |
|                          |                         |service you are load       |
|                          |                         |balancing.                 |
+--------------------------+-------------------------+---------------------------+
|algorithm                 |String                   |Algorithm that defines     |
|                          |                         |how traffic should be      |
|                          |                         |directed between back-     |
|                          |                         |end nodes.                 |
+--------------------------+-------------------------+---------------------------+
|status                    |String                   |The status of the load     |
|                          |                         |balancer.                  |
+--------------------------+-------------------------+---------------------------+
|timeout                   |String                   |The timeout value for      |
|                          |                         |the load balancer and      |
|                          |                         |communications with its    |
|                          |                         |nodes. Defaults to 30      |
|                          |                         |seconds with a maximum     |
|                          |                         |of 120 seconds.            |
+--------------------------+-------------------------+---------------------------+
|connectionLogging         |String                   |Current connection         |
|                          |                         |logging configuration.     |
|                          |                         |Refer to the API Ops       |
|                          |                         |section "Log Connections"  |
|                          |                         |for                        |
|                          |                         |information and examples.  |
+--------------------------+-------------------------+---------------------------+
|virtualIps                |Object                   |Type of virtualIp to add   |
|                          |                         |with the creation of a     |
|                          |                         |load balancer. See the     |
|                          |                         |virtual IP types table in  |
|                          |                         |the API Operations         |
|                          |                         |section "Virtual IPs".     |
+--------------------------+-------------------------+---------------------------+
|id                        |Int                      |The ID for the IP          |
|                          |                         |address.                   |
+--------------------------+-------------------------+---------------------------+
|address                   |String                   |The IP address.            |
+--------------------------+-------------------------+---------------------------+
|type                      |String                   |The IP address type.       |
+--------------------------+-------------------------+---------------------------+
|ipVersion                 |String                   |The IP version.            |
+--------------------------+-------------------------+---------------------------+
|nodes                     |Object                   |Nodes to be added to the   |
|                          |                         |load balancer.             |
+--------------------------+-------------------------+---------------------------+
|address                   |String                   |The node address.          |
+--------------------------+-------------------------+---------------------------+
|port                      |Int                      |The node port.             |
+--------------------------+-------------------------+---------------------------+
|condition                 |String                   |The node condition. For    |
|                          |                         |example, ENABLED.          |
+--------------------------+-------------------------+---------------------------+
|status                    |String                   |The node status. For       |
|                          |                         |example, ONLINE.           |
+--------------------------+-------------------------+---------------------------+
|sessionPersistence        |String                   |Specifies whether          |
|                          |                         |multiple requests from     |
|                          |                         |clients are directed to    |
|                          |                         |the same node.             |
+--------------------------+-------------------------+---------------------------+
|connectionThrottle        |String                   |Specifies limits on the    |
|                          |                         |number of connections      |
|                          |                         |per IP address to help     |
|                          |                         |mitigate malicious or      |
|                          |                         |abusive traffic to your    |
|                          |                         |applications. See          |
|                          |                         |:ref:`throttle-connections`|  
|                          |                         |for information and        |
|                          |                         |examples.                  |
+--------------------------+-------------------------+---------------------------+
|cluster                   |String                   |The cluster name.          |
+--------------------------+-------------------------+---------------------------+
|created                   |Object                   |The date and time what     |
|                          |                         |the load balancer was      |
|                          |                         |created.                   |
+--------------------------+-------------------------+---------------------------+
|updated                   |Object                   |The date and time what     |
|                          |                         |the load balancer was      |
|                          |                         |last updated.              |
+--------------------------+-------------------------+---------------------------+
|sourceAddresses           |Dict                     |The source public and      |
|                          |                         |private IP addresses.      |
+--------------------------+-------------------------+---------------------------+      






**Example Create load balancer: JSON response**


.. code::

    {
        "loadBalancer":{
            "name":"a-new-loadbalancer",
            "id":2200,
            "port":80,
            "protocol":"HTTP",
            "halfClosed":"false",
            "algorithm":"RANDOM",
            "status":"BUILD",
            "timeout": 30,
            "cluster":{
                "name":"host2_cluster1"
            },
            "nodes":[{
                    "address":"10.1.1.1",
                    "id":2208,
                    "port":80,
                    "status":"ONLINE",
                    "condition":"ENABLED",
                    "weight":1
                }
            ],
            "virtualIps":[{
                    "address":"10.0.0.18",
                    "id":15,
                    "type":"PUBLIC",
                    "ipVersion":"IPV4"
                },
                {
                    "address":"fd24:f480:ce44:91bc:1af2:15ff:0000:0005",
                    "id":9000137,
                    "type":"PUBLIC",
                    "ipVersion":"IPV6"
                }
            ],
            "created":{
                "time":"2011-06-01T08:20:09-05:00"
            },
            "updated":{
                "time":"2011-06-01T08:20:09-05:00"
            },
            "connectionLogging":{
                "enabled":false
            },
            "sourceAddresses":{
                "ipv6Public":"2001:4801:79f1:1::1/64",
                "ipv4Servicenet":"10.0.0.0",
                "ipv4Public":"10.12.99.28"
            }
        }
    }


**Example Create load balancer: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" id="2198" name="a-new-loadbalancer"
                  algorithm="RANDOM" protocol="HTTP" halfClosed="false" port="80" status="BUILD" timeout="30">
        <virtualIps>
            <virtualIp id="13" address="10.0.0.16" ipVersion="IPV4" type="PUBLIC"/>
            <virtualIp id="9000135" address="fd24:f480:ce44:91bc:1af2:15ff:0000:0003" ipVersion="IPV6" type="PUBLIC"/>
        </virtualIps>
        <nodes>
            <node id="2206" address="10.1.1.1" port="80" condition="ENABLED" status="ONLINE" weight="1"/>
        </nodes>
        <cluster name="host2_cluster1"/>
        <created time="2011-06-01T08:08:41-05:00"/>
        <updated time="2011-06-01T08:08:41-05:00"/>
        <connectionLogging enabled="false"/>
        <sourceAddresses ipv4Servicenet="10.0.0.0" ipv4Public="10.12.99.29" ipv6Public="2001:4801:79f1:1::3/64"/>
    </loadBalancer>


**Example Create load balancer with shared IP: JSON response**


.. code::

    {
        "loadBalancer": {
            "name": "a-new-loadbalancer",
            "id": 144,
            "protocol": "HTTP",
            "halfClosed": "true",
            "port": 83,
            "algorithm": "RANDOM",
            "status": "BUILD",
            "timeout": 30,
            "cluster": {
                "name": "ztm-n01.staging1.lbaas.rackspace.net"
            },
            "nodes": [
                {
                    "address": "10.1.1.1",
                    "id": 653,
                    "port": 80,
                    "status": "ONLINE",
                    "condition": "ENABLED",
                    "weight": 1
                }
            ],
            "virtualIps": [
                {
                    "address": "206.10.10.210",
                    "id": 39,
                    "type": "PUBLIC",
                    "ipVersion": "IPV4"
                }
            ],
            "created": {
                "time": "2011-04-13T14:18:07Z"
            },
            "updated": {
                "time": "2011-04-13T14:18:07Z"
            },
            "connectionLogging": {
                "enabled": false
            }
        }
    }


**Example Create load balancer with shared IP: XML response**


.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        id="144"
        name="a-new-loadbalancer"
        algorithm="RANDOM"
        protocol="HTTP"
        port="83"
        status="BUILD"
        timeout="30">
        <virtualIps>
            <virtualIp
                id="39"
                address="206.10.10.210"
                ipVersion="IPV4"
                type="PUBLIC" />
        </virtualIps>
        <nodes>
            <node
                id="653"
                address="10.1.1.1"
                port="80"
                condition="ENABLED"
                status="ONLINE"
                weight="1" />
        </nodes>
        <cluster name="ztm-n03.staging1.lbaas.rackspace.net" />
        <created time="2011-02-08T21:19:55Z" />
        <updated time="2011-02-08T21:19:55Z" />
        <connectionLogging enabled="false" />
    </loadBalancer>


**Example Create load balancer with IPv4/IPv6: JSON response**


.. code::

    {
        "loadBalancer": {
            "name": "a-new-loadbalancer",
            "id": 144,
            "protocol": "HTTP",
            "halfClosed": "false",
            "port": 83,
            "algorithm": "RANDOM",
            "status": "BUILD",
            "timeout": 30,
            "cluster": {
                "name": "ztm-n01.staging1.lbaas.rackspace.net"
            },
            "nodes": [
                {
                    "address": "10.1.1.1",
                    "id": 653,
                    "port": 80,
                    "status": "ONLINE",
                    "condition": "ENABLED",
                    "weight": 1
                }
            ],
            "virtualIps": [
                {
                    "address": "206.10.10.210",
                    "id": 39,
                    "type": "PUBLIC",
                    "ipVersion": "IPV4"
                },
                {
                    "address": "2001:4801:79f1:0002:711b:be4c:0000:0021",
                    "id": 900001,
                    "type": "PUBLIC",
                    "ipVersion": "IPV6"
                }
            ],
            "created": {
                "time": "2011-04-13T14:18:07Z"
            },
            "updated": {
                "time": "2011-04-13T14:18:07Z"
            },
            "connectionLogging": {
                "enabled": false
            }
        }
    }


**Example Create load balancer with IPv4/IPv6: XML response**


.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        id="144"
        name="a-new-loadbalancer"
        algorithm="RANDOM"
        protocol="HTTP"
        halfclosed="false"
        port="83"
        status="BUILD"
        timeout="30">
        <virtualIps>
            <virtualIp
                id="39"
                address="206.10.10.210"
                ipVersion="IPV4"
                type="PUBLIC" />
            <virtualIp
                id="900001"
                address="2001:4801:79f1:0002:711b:be4c:0000:0021"
                ipVersion="IPV6"
                type="PUBLIC" />
        </virtualIps>
        <nodes>
            <node
                id="653"
                address="10.1.1.1"
                port="80"
                condition="ENABLED"
                status="ONLINE"
                weight="1" />
        </nodes>
        <cluster name="ztm-n03.staging1.lbaas.rackspace.net" />
        <created time="2011-02-08T21:19:55Z" />
        <updated time="2011-02-08T21:19:55Z" />
        <connectionLogging enabled="false" />
    </loadBalancer>

