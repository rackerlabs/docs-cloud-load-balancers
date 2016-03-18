==============================================================================================================
2.1.1. List Load Balancers - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
==============================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.1.1. List Load Balancers
   :name: list-load-balancers
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/loadbalancers?vipid=``id``
Retrieve a list of all load balancers using a virtual IP id.
Support, Service Admin
**GET**
/management/loadbalancers?vipaddress=``vipAddress``
Retrieve a list of all load balancers using a virtual IP address.
Support, Service Admin
Normal Response Code(s): 200

Error Response Code(s): loadBalancerManagementFault(400, 500),
serviceUnavailable (503), unauthorized (401), badRequest (400),
overLimit (413)

Use query parameters to retrieve a list of load balancers based on
virtual IP id or address. The response will contain basic information
for all load balancers that are associated with the requested virtual
IP.

A single call can accept either ``?vipid`` or ``?vipaddress`` but not
both. If both parameters are supplied, the request will fail with a
badRequest (400) and message 'Cannot set both ip address and vip id.'

The virtual IP address is validated before use. If the specified
``?vipaddress`` does not conform to IPv4 or IPv6 syntax, the request
will fail with a badRequest (400) and message 'Ip address is invalid.'

`  <>`__
**Example 2.1. List Load Balancers by Virtual IP Response: XML**

.. code::  

    <mgmt:loadBalancers xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" xmlns:atom="http://www.w3.org/2005/Atom"
                        xmlns:mgmt="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <mgmt:loadBalancer id="13281" name="myLB" algorithm="RANDOM" protocol="HTTP" status="SUSPENDED" isSticky="false">
            <virtualIps>
                <virtualIp id="22" address="10.11.255.1" ipVersion="IPV4" type="PUBLIC"/>
                <virtualIp id="9003827" address="2a00:1a48:79ff:0000:711b:be4c:0000:0001" ipVersion="IPV6" type="PUBLIC"/>
            </virtualIps>
            <cluster name="mgmt.lbaas.rackspace.net"/>
            <created time="2012-06-14T16:56:39Z"/>
            <updated time="2012-06-14T17:53:37Z"/>
            <connectionLogging enabled="false"/>
            <mgmt:tickets/>
        </mgmt:loadBalancer>
    </mgmt:loadBalancers>

                        

`  <>`__
**Example 2.2. List Load Balancers by Virtual IP Response: JSON**

.. code::  

    {"loadBalancers":[
        {
            "tickets":[],
            "name":"myNewer",
            "id":13281,
            "protocol":"HTTP",
            "algorithm":"RANDOM",
            "status":"SUSPENDED",
            "cluster":{
                "name":"mgmt.lbaas.rackspace.net"
            },
            "created":{
                "time":"2012-06-14T16:56:39Z"
            },
            "virtualIps":[
                {
                    "address":"10.11.255.1",
                    "id":22,
                    "type":"PUBLIC",
                    "ipVersion":"IPV4"
                },
                {
                    "address":"2a00:1a48:79ff:0000:711b:be4c:0000:0001",
                    "id":9003827,
                    "type":"PUBLIC",
                    "ipVersion":"IPV6"
                }
            ],
            "updated":{
                "time":"2012-06-14T17:53:37Z"
            },
            "connectionLogging":{
                "connectionLogging":{
                    "enabled":false
                }
            },
            "isSticky":false
        }
    ]}

                        

`  <>`__
**Example 2.3. List Load Balancers by Virtual IP Address Response: XML**

.. code::  

    <mgmt:loadBalancers xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" xmlns:atom="http://www.w3.org/2005/Atom"
                        xmlns:mgmt="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <mgmt:loadBalancer id="13281" name="myLB" algorithm="RANDOM" protocol="HTTP" status="SUSPENDED" isSticky="false">
            <virtualIps>
                <virtualIp id="22" address="10.11.255.1" ipVersion="IPV4" type="PUBLIC"/>
                <virtualIp id="9003827" address="2a00:1a48:79ff:0000:711b:be4c:0000:0001" ipVersion="IPV6" type="PUBLIC"/>
            </virtualIps>
            <cluster name="mgmt.lbaas.rackspace.net"/>
            <created time="2012-06-14T16:56:39Z"/>
            <updated time="2012-06-14T17:53:37Z"/>
            <connectionLogging enabled="false"/>
            <mgmt:tickets/>
        </mgmt:loadBalancer>
    </mgmt:loadBalancers>

                        

`  <>`__
**Example 2.4. List Load Balancers by Virtual IP Address Response:
JSON**

.. code::  

    {"loadBalancers":[
        {
            "tickets":[],
            "name":"myNewer",
            "id":13281,
            "protocol":"HTTP",
            "algorithm":"RANDOM",
            "status":"SUSPENDED",
            "cluster":{
                "name":"mgmt.lbaas.rackspace.net"
            },
            "created":{
                "time":"2012-06-14T16:56:39Z"
            },
            "virtualIps":[
                {
                    "address":"10.11.255.1",
                    "id":22,
                    "type":"PUBLIC",
                    "ipVersion":"IPV4"
                },
                {
                    "address":"2a00:1a48:79ff:0000:711b:be4c:0000:0001",
                    "id":9003827,
                    "type":"PUBLIC",
                    "ipVersion":"IPV6"
                }
            ],
            "updated":{
                "time":"2012-06-14T17:53:37Z"
            },
            "connectionLogging":{
                "connectionLogging":{
                    "enabled":false
                }
            },
            "isSticky":false
        }
    ]}

                        
