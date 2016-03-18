.. _get-loadbalancers-vipsid:

Retrieve load balancers for a VIP ID
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/loadbalancers?vipid=id


This operation lists all load balancers associated with the specified virtual IP ID.

The access levels for this operation are ``support`` and ``service admin``. 

Use query parameters to retrieve a list of load balancers based on virtual IP  ID, ``?vipid=id``. The response contains basic information for all load balancers that are associated with the requested virtual IP ID.

A single call can accept either ?vipid or ?vipaddress (described in the next section) but not both. If both parameters are supplied, the request will fail with a badRequest (400) and message ``Cannot set both ip address and vip id``.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response code             |Name                     |Description              |
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
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
 

Response
""""""""""""""""



**Example: List load balancers by virtual IP ID XML response**

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

                        


**Example: List load balancers by virtual IP ID JSON response**

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

                        

