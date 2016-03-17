====================================================================================================================================
3.4. Viewing Extended Details of a Load Balancer - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
====================================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.4. Viewing Extended Details of a Load Balancer
   :name: viewing-extended-details-of-a-load-balancer
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/loadbalancers/``loadBalancerId``/extendedview
View extended details of a load balancer.
Support, Service Admin
This operation provides the detailed output for a specific load balancer
configured and associated with the designated account. It differs from
the customer view because it provides the total active connections, host
machine information, and a rate limit (if applicable) as part of the
``loadbalancer`` element.

..  note:: 
Note
An extended detail view is not available for a list of load balancers.

`  <>`__
**Example 3.7. List Extended Load Balancer Details Response: XML**

.. code::  

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
            id="2000"
            name="sample-loadbalancer"
            sticky="true"
            accountId="54334"
            protocol="HTTP"
            port="80"
            algorithm="RANDOM"
            status="ACTIVE"
            timeout="30"
            totalActiveConnections="340"
            ipv4Servicenet="10.0.0.0"
            ipv4Public="1.2.3.4"
            ipv6Public="FFFF:0000:0000:0000:0000:0000:0000:FFFF">
        <host id="1" type="ACTIVE" />
        <currentUsage
                incomingTransfer="1.40"
                outgoingTransfer="20.14" />
        <virtualIps>
            <virtualIp
                    id="1000"
                    address="206.10.10.210"
                    type="PUBLIC" />
        </virtualIps>
        <nodes>
            <node
                    nodeId="1041"
                    ip="10.1.1.1"
                    port="80"
                    condition="ENABLED"
                    status="ONLINE"
                    type="PRIMARY"/>
            <node
                    nodeId="1411"
                    ip="10.1.1.2"
                    port="80"
                    condition="ENABLED"
                    status="ONLINE"
                    type="SECONDARY"/>
        </nodes>
        <sessionPersistence persistenceType="HTTP_COOKIE"/>
        <connectionLimits
                minConnections="10"
                maxConnectionsFromIp="100"
                maxConnectionRateFromIp="50"
                maxConnectionRateTimer="60" />
        <connectionLogging enabled="false" />
        <cluster name="c1.dfw1" />
        <ratelimit
                ticketId="4100"
                expirationTime="2010-10-17 00:00:00"
                maxRequestsPerSecond="100" />
        <created time="2010-06-01T12:00:00Z" />
        <updated time="2010-06-01T12:00:00Z" />
        <sslTermination xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true" securePort="500" secureTrafficOnly="false"/>
    </loadBalancer>

                    

`  <>`__
**Example 3.8. List Extended Load Balancer Details Response: XML**

.. code::  

    {"loadbalancer": {
        "id": 2000,
        "accountId" : 3434,
        "sticky" : true,
        "name": "sample-loadbalancer",
        "protocol": "HTTP",
        "port": 80,
        "algorithm": "RANDOM",
        "status": "ACTIVE",
        "timeout": 30,
        "totalActiveConnections": 340,
        "ipv4Servicenet": "10.0.0.0",
        "ipv4Public": "1.2.3.4",
        "ipv6Public": "FFFF:0000:0000:0000:0000:0000:0000:FFFF",
        "currentUsage": {
            "incomingTransfer": 1.40,
            "outgoingTransfer": 20.14
        },
        "host": {
            "id": 1,
            "type": "ACTIVE"
        },
        "virtualIps": {
            "virtualIp": {
                "id": 1000,
                "address": "206.10.10.2010",
                "type": "PUBLIC"
            }
        },
        "nodes": {
            "node": [
                {
                    "nodeId": 1041,
                    "ip": "10.1.1.1",
                    "port": 9090,
                    "condition": "ENABLED",
                    "status": "ONLINE",
                    "type":"PRIMARY"
                },
                {
                    "nodeId": 1042,
                    "ip": "10.1.1.2",
                    "port": 80,
                    "condition": "ENABLED",
                    "status": "ONLINE",
                    "type":"SECONDARY"
                }
            ]
        },
        "connectionLogging": {
            "enabled": "true"
        },
        "rateLimit": {
            "ticketId": 1123,
            "expirationTime": 1283277190574,
            "maxRequestsPerSecond": 37
        },
        "sessionPersistence": {
            "persistenceType": "HTTP_COOKIE"
        },
        "connectionLimits": {
            "minConnections": 10,
            "maxConnectionsFromIp": 100,
            "maxConnectionsRateFromIp": 50,
            "maxConnectionsRateTimer": 60
        },
        "cluster": {
            "name": "c1.dfw1",
            "description": "Cluster Description"
        },
        "created": {
            "time": "2010-06-01 00: 00: 00"
        },
        "updated": {
            "time": "2010-06-01 00: 00: 00"
        },
        "sslTermination":{
            "enabled":true,
            "secureTrafficOnly":false,
            "securePort":555
        }
    }
    }

                    
