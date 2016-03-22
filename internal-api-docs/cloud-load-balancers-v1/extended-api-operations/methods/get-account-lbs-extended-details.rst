.. _get-account-lbs-extended-details:

Retrieve load balancers by account with extended details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/accounts/{accountId}/extendedloadbalancers  


This operation retrieves a list of load balancers on the specified account with extended 
details including virtual IPs.



The access levels for this operation are ``support`` and  ``service admin``. 

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

**Example: List extended account load balancers XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <ns2:extendedAccountLoadbalancers xmlns:ns2="http://docs.openstack.org/loadbalancers/api/management/v1.0"
                                       xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" accountId="5805065">
        <ns2:extendedAccountLoadbalancer loadBalancerId="321" loadBalancerName="a-new-loadbalancer" clusterId="1"
                                          clusterName="DEV" protocol="HTTP" status="BUILD" region="ORD">
            <ns2:virtualIps>
                <ns2:virtualIp xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="virtualIp" id="1298"
                                address="10.12.99.227" ipVersion="IPV4" type="PUBLIC"/>
                <ns2:virtualIp xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="virtualIp" id="267"
                                address="2001:4801:79f1:0002:22d6:5749:0000:0001" ipVersion="IPV6" type="PUBLIC"/>
            </ns2:virtualIps>
        </ns2:extendedAccountLoadbalancer>
        <ns2:extendedAccountLoadbalancer loadBalancerId="322" loadBalancerName="a-new-loadbalancer" clusterId="1"
                                          clusterName="DEV" protocol="HTTP" status="ACTIVE" region="ORD">
            <ns2:virtualIps>
                <ns2:virtualIp xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="virtualIp" id="1299"
                                address="10.12.99.228" ipVersion="IPV4" type="PUBLIC"/>
                <ns2:virtualIp xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="virtualIp" id="268"
                                address="2001:4801:79f1:0002:22d6:5749:0000:0002" ipVersion="IPV6" type="PUBLIC"/>
            </ns2:virtualIps>
        </ns2:extendedAccountLoadbalancer>
    </ns2:extendedAccountLoadbalancers>

                    


**Example: List extended account load balancers JSON response**

.. code::  

    {"accountId":5805065,"extendedAccountLoadbalancers":[
        {
            "protocol":"HTTP",
            "status":"BUILD",
            "virtualIps":[
                {
                    "address":"10.12.99.227",
                    "id":1298,
                    "type":"PUBLIC",
                    "ipVersion":"IPV4"
                },
                {
                    "address":"2001:4801:79f1:0002:22d6:5749:0000:0001",
                    "id":267,
                    "type":"PUBLIC",
                    "ipVersion":"IPV6"
                }
            ],
            "region":"ORD",
            "loadBalancerId":321,
            "loadBalancerName":"a-new-loadbalancer",
            "clusterId":1,
            "clusterName":"DEV"
        },
        {
            "protocol":"HTTP",
            "status":"ACTIVE",
            "virtualIps":[
                {
                    "address":"10.12.99.228",
                    "id":1299,
                    "type":"PUBLIC",
                    "ipVersion":"IPV4"
                },
                {
                    "address":"2001:4801:79f1:0002:22d6:5749:0000:0002",
                    "id":268,
                    "type":"PUBLIC",
                    "ipVersion":"IPV6"
                }
            ],
            "region":"ORD",
            "loadBalancerId":322,
            "loadBalancerName":"a-new-loadbalancer",
            "clusterId":1,
            "clusterName":"DEV"
        }
    ]}
