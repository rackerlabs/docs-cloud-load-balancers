===================================================================================================================================
3.5. Account Load Balancers and Usage (Billing) - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
===================================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.5. Account Load Balancers and Usage (Billing)
   :name: account-load-balancers-and-usage-billing
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/accounts/``accountId``/loadbalancers
Retrieve a list of load balancers on this account.
Support, Service Admin
**GET**
/management/accounts/``accountId``/extendedloadbalancers
Retrieve a list of load balancers on this account with extended details
including virtual IPs.
Support, Service Admin
**GET**
/management/accounts/billing?startTime=``YYYY``-``MM``-``DD``\ T
``HH``:``mm``:``ss``\ &endTime=\ ``YYYY``-``MM``-``DD``\ T
``HH``:``mm``:``ss``
Retrieve usage for all accounts for a *single* day.
Support, Service Admin, Billing
**GET**
/management/accounts/usage?startTime=``YYYY``-``MM``-``DD``\ T
``HH``:``mm``:``ss``\ &endTime=\ ``YYYY``-``MM``-``DD``\ T
``HH``:``mm``:``ss``\ &offset=\ ``offset``\ &limit=\ ``limit``
Retrieves account- specific usage for all accounts for the given date
range. The response is paginated with a default limit of 500 and a
maximum limit of 1000
Support, Service Admin, Billing
**GET**
/management/loadbalancers/usage?startTime=``YYYY``-``MM``-``DD``\ T
``HH``:``mm``:``ss``\ &endTime=\ ``YYYY``-``MM``-``DD``\ T
``HH``:``mm``:``ss``\ &offset=\ ``offset``\ &limit=\ ``limit``
Retrieves load balancer- specific usage for all load balancers for the
given date range. The response is paginated with a default limit of 500
and a maximum limit of 1000
Support, Service Admin, Billing
Normal Response Code(s): 200

Error Response Code(s): loadBalancerManagementFault (400, 500),
serviceUnavailable (503), unauthorized ( 401), badRequest (400),
overLimit ( 413)

A user can list all load balancers and their usage for the given account
using these methods. The date parameters follow the YYYY-MM-DD date
format. Please note that usage is retained for a maximum of 90 days. The
``startTime`` and ``endTime`` parameters are required for the call.

`  <>`__
**Example 3.9. List Account Load Balancers Response: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <ns2:accountLoadBalancers xmlns:ns2="http://docs.openstack.org/loadbalancers/api/management/v1.0" accountId="5805065">
        <ns2:accountLoadBalancer loadBalancerId="321" loadBalancerName="a-new-loadbalancer" clusterId="1" clusterName="DEV"
                                  protocol="HTTP" status="BUILD"/>
        <ns2:accountLoadBalancer loadBalancerId="322" loadBalancerName="a-new-loadbalancer" clusterId="1" clusterName="DEV"
                                  protocol="HTTP" status="ACTIVE"/>
    </ns2:accountLoadBalancers>

                    

`  <>`__
**Example 3.10. List Account Load Balancers Response: JSON**

.. code::  

    {"accountId":5805065,"accountLoadBalancers":[
        {
            "protocol":"HTTP",
            "status":"BUILD",
            "loadBalancerId":321,
            "loadBalancerName":"a-new-loadbalancer",
            "clusterId":1,
            "clusterName":"DEV"
        },
        {
            "protocol":"HTTP",
            "status":"ACTIVE",
            "loadBalancerId":322,
            "loadBalancerName":"a-new-loadbalancer",
            "clusterId":1,
            "clusterName":"DEV"
        }
    ]}

                    

`  <>`__
**Example 3.11. List Extended Account Load Balancers Response: XML**

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

                    

`  <>`__
**Example 3.12. List Extended Account Load Balancers Response: JSON**

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

                    

`  <>`__
**Example 3.13. List Account Load Balancers Usage Response: XML**

.. code::  

    <accountBilling xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" accountId="1106">
        <accountUsage>
            <accountUsageRecord numLoadBalancers="2" numPublicVips="1" 
                numServicenetVips="0" startTime="2010-12-01T14:09:14-06:00"/>
        </accountUsage>
        <loadBalancerUsage loadBalancerId="66" loadBalancerName="My first loadbalancer">
            <loadBalancerUsageRecord id="394" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="1"
                numPolls="32" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T16:23:54-06:00"
                     vipType="PUBLIC"/>
            <loadBalancerUsageRecord id="473" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="2"
                numPolls="5" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T12:36:30-06:00"
                     vipType="PUBLIC"/>
            <loadBalancerUsageRecord id="474" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="2"
                numPolls="5" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T12:36:30-06:00"
                     vipType="PUBLIC"/>
            <loadBalancerUsageRecord id="475" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="2"
                numPolls="5" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T12:36:30-06:00"
                     vipType="PUBLIC"/>
        </loadBalancerUsage>
        <loadBalancerUsage loadBalancerId="77" loadBalancerName="My second loadbalancer">
            <loadBalancerUsageRecord id="394" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="1"
                numPolls="32" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T16:23:54-06:00"
                     vipType="PUBLIC"/>
            <loadBalancerUsageRecord id="473" averageNumConnections="0.0"
                    incomingTransfer="0" outgoingTransfer="0" numVips="2" numPolls="5"
                    startTime="2010-12-21T12:32:07-06:00"
                    endTime="2010-12-21T12:36:30-06:00"
                     vipType="PUBLIC"/>
        </loadBalancerUsage>
    </accountBilling>

                    

`  <>`__
**Example 3.14. List Accounts Usage Response (Paginated): XML**

.. code::  

    <mgmt:accountUsageRecords 
        xmlns:mgmt="http://docs.openstack.org/loadbalancers/api/management/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom">
        <mgmt:accountUsageRecord accountId="406271" numLoadBalancers="16"
            numPublicVips="4" numServicenetVips="12"
            startTime="2011-09-01T14:21:16-05:00"/>
        <mgmt:accountUsageRecord accountId="406271" numLoadBalancers="15"
            numPublicVips="3" numServicenetVips="12"
            startTime="2011-09-01T14:21:24-05:00"/>
        <mgmt:accountUsageRecord accountId="406271" numLoadBalancers="16"
            numPublicVips="4" numServicenetVips="12"
            startTime="2011-09-01T14:22:06-05:00"/>
        <mgmt:accountUsageRecord accountId="406271" numLoadBalancers="15"
            numPublicVips="3" numServicenetVips="12"
            startTime="2011-09-01T14:23:03-05:00"/>
        <mgmt:accountUsageRecord accountId="406271" numLoadBalancers="16"
            numPublicVips="4" numServicenetVips="12"
            startTime="2011-09-01T14:46:48-05:00"/>
        <atom:link
            href="https://admin.ord.loadbalancers.api.rackspacecloud.com/v1.0/management/accounts/usage?startTime=2011-01-11&amp;endTime=2013-01-12&amp;offset=30&amp;limit=5"
            rel="next"/>
        <atom:link
            href="https://admin.ord.loadbalancers.api.rackspacecloud.com/v1.0/management/accounts/usage?startTime=2011-01-11&amp;endTime=2013-01-12&amp;offset=20&amp;limit=5"
            rel="previous"/>
    </mgmt:accountUsageRecords>

                    

`  <>`__
**Example 3.15. List Accounts Usage Response (Paginated): JSON**

.. code::  

    {
        "accountUsageRecords": [
            {
                "startTime": "2011-09-01T14:21:16-05:00",
                "accountId": 406271,
                "numLoadBalancers": 16,
                "numPublicVips": 4,
                "numServicenetVips": 12
            },
            {
                "startTime": "2011-09-01T14:21:24-05:00",
                "accountId": 406271,
                "numLoadBalancers": 15,
                "numPublicVips": 3,
                "numServicenetVips": 12
            },
            {
                "startTime": "2011-09-01T14:22:06-05:00",
                "accountId": 406271,
                "numLoadBalancers": 16,
                "numPublicVips": 4,
                "numServicenetVips": 12
            },
            {
                "startTime": "2011-09-01T14:23:03-05:00",
                "accountId": 406271,
                "numLoadBalancers": 15,
                "numPublicVips": 3,
                "numServicenetVips": 12
            },
            {
                "startTime": "2011-09-01T14:46:48-05:00",
                "accountId": 406271,
                "numLoadBalancers": 16,
                "numPublicVips": 4,
                "numServicenetVips": 12
            }
        ],
        "links": [
            {
                "link": {
                    "otherAttributes": {},
                    "href": "http://localhost:8080/lb-mgmt-rest-service/management/accounts/usage?startTime=2011-01-11&endTime=2013-01-12&offset=30&limit=5",
                    "rel": "next"
                }
            },
            {
                "link": {
                    "otherAttributes": {},
                    "href": "http://localhost:8080/lb-mgmt-rest-service/management/accounts/usage?startTime=2011-01-11&endTime=2013-01-12&offset=20&limit=5",
                    "rel": "previous"
                }
            }
        ]
    }

                    

`  <>`__
**Example 3.16. List Load Balancers Usage Response (Paginated): XML**

.. code::  

    <mgmt:loadBalancerUsageRecords
        xmlns:mgmt="http://docs.openstack.org/loadbalancers/api/management/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom">
        <mgmt:loadBalancerUsageRecord
            id="21"
            accountId="406271"
            loadBalancerId="33"
            averageNumConnections="0.0"
            incomingTransfer="0"
            outgoingTransfer="0"
            averageNumConnectionsSsl="0.0"
            incomingTransferSsl="0"
            outgoingTransferSsl="0"
            numVips="1"
            numPolls="89"
            startTime="2011-08-25T11:45:48-05:00"
            endTime="2011-08-25T17:36:59-05:00"
            vipType="SERVICENET"
            sslMode="OFF"
            eventType="CREATE_LOADBALANCER"/>
        <mgmt:loadBalancerUsageRecord
            id="27"
            accountId="406271"
            loadBalancerId="33"
            averageNumConnections="0.0"
            incomingTransfer="0"
            outgoingTransfer="0"
            averageNumConnectionsSsl="0.0"
            incomingTransferSsl="0"
            outgoingTransferSsl="0"
            numVips="1"
            numPolls="7"
            startTime="2011-09-01T16:38:06-05:00"
            endTime="2011-09-01T17:37:27-05:00"
            vipType="SERVICENET"
            sslMode="OFF"/>
        <mgmt:loadBalancerUsageRecord
            id="37"
            accountId="406271"
            loadBalancerId="33"
            averageNumConnections="0.0"
            incomingTransfer="0"
            outgoingTransfer="0"
            averageNumConnectionsSsl="0.0"
            incomingTransferSsl="0"
            outgoingTransferSsl="0"
            numVips="1"
            numPolls="49"
            startTime="2011-09-02T11:51:56-05:00"
            endTime="2011-09-02T16:00:55-05:00"
            vipType="SERVICENET"
            sslMode="OFF"/>
        <mgmt:loadBalancerUsageRecord
            id="73"
            accountId="406271"
            loadBalancerId="33"
            averageNumConnections="0.0"
            incomingTransfer="0"
            outgoingTransfer="0"
            averageNumConnectionsSsl="0.0"
            incomingTransferSsl="0"
            outgoingTransferSsl="0"
            numVips="1"
            numPolls="1"
            startTime="2011-10-28T14:42:29-05:00"
            endTime="2011-10-28T14:42:29-05:00"
            vipType="SERVICENET"
            sslMode="OFF"/>
        <mgmt:loadBalancerUsageRecord
            id="1089"
            accountId="406271"
            loadBalancerId="33"
            averageNumConnections="0.0"
            incomingTransfer="0"
            outgoingTransfer="0"
            averageNumConnectionsSsl="0.0"
            incomingTransferSsl="0"
            outgoingTransferSsl="0"
            numVips="0"
            numPolls="0"
            startTime="2012-01-25T22:09:21-06:00"
            endTime="2012-01-25T22:09:21-06:00"
            vipType="SERVICENET"
            sslMode="OFF"
            eventType="DELETE_LOADBALANCER"/>
        <atom:link
            href="https://admin.ord.loadbalancers.api.rackspacecloud.com/v1.0/management/loadbalancers/usage?startTime=2011-01-11&amp;endTime=2013-01-12&amp;offset=30&amp;limit=5"
            rel="next"/>
        <atom:link
            href="https://admin.ord.loadbalancers.api.rackspacecloud.com/v1.0/management/loadbalancers/usage?startTime=2011-01-11&amp;endTime=2013-01-12&amp;offset=20&amp;limit=5"
            rel="previous"/>
    </mgmt:loadBalancerUsageRecords>

                    

`  <>`__
**Example 3.17. List Load Balancers Usage Response (Paginated): JSON**

.. code::  

    {
        "loadBalancerUsageRecords": [
            {
                "id": 21,
                "accountId": 406271,
                "loadBalancerId": 33,
                "averageNumConnections": 0,
                "incomingTransfer": 0,
                "outgoingTransfer": 0,
                "averageNumConnectionsSsl": 0,
                "incomingTransferSsl": 0,
                "outgoingTransferSsl": 0,
                "numVips": 1,
                "numPolls": 89,
                "startTime": "2011-08-25T11:45:48-05:00",
                "endTime": "2011-08-25T17:36:59-05:00",
                "vipType": "SERVICENET",
                "sslMode": "OFF",
                "eventType": "CREATE_LOADBALANCER"
            },
            {
                "id": 27,
                "accountId": 406271,
                "loadBalancerId": 33,
                "averageNumConnections": 0,
                "incomingTransfer": 0,
                "outgoingTransfer": 0,
                "averageNumConnectionsSsl": 0,
                "incomingTransferSsl": 0,
                "outgoingTransferSsl": 0,
                "numVips": 1,
                "numPolls": 7,
                "startTime": "2011-09-01T16:38:06-05:00",
                "endTime": "2011-09-01T17:37:27-05:00",
                "vipType": "SERVICENET",
                "sslMode": "OFF"
            },
            {
                "id": 37,
                "accountId": 406271,
                "loadBalancerId": 33,
                "averageNumConnections": 0,
                "incomingTransfer": 0,
                "outgoingTransfer": 0,
                "averageNumConnectionsSsl": 0,
                "incomingTransferSsl": 0,
                "outgoingTransferSsl": 0,
                "numVips": 1,
                "numPolls": 49,
                "startTime": "2011-09-02T11:51:56-05:00",
                "endTime": "2011-09-02T16:00:55-05:00",
                "vipType": "SERVICENET",
                "sslMode": "OFF"
            },
            {
                "id": 73,
                "accountId": 406271,
                "loadBalancerId": 33,
                "averageNumConnections": 0,
                "incomingTransfer": 0,
                "outgoingTransfer": 0,
                "averageNumConnectionsSsl": 0,
                "incomingTransferSsl": 0,
                "outgoingTransferSsl": 0,
                "numVips": 1,
                "numPolls": 1,
                "startTime": "2011-10-28T14:42:29-05:00",
                "endTime": "2011-10-28T14:42:29-05:00",
                "vipType": "SERVICENET",
                "sslMode": "OFF"
            },
            {
                "id": 1089,
                "accountId": 406271,
                "loadBalancerId": 33,
                "averageNumConnections": 0,
                "incomingTransfer": 0,
                "outgoingTransfer": 0,
                "averageNumConnectionsSsl": 0,
                "incomingTransferSsl": 0,
                "outgoingTransferSsl": 0,
                "numVips": 0,
                "numPolls": 0,
                "startTime": "2012-01-25T22:09:21-06:00",
                "endTime": "2012-01-25T22:09:21-06:00",
                "vipType": "PUBLIC",
                "sslMode": "OFF",
                "eventType": "DELETE_LOADBALANCER"
            }
        ],
        "links": [
            {
                "link": {
                    "otherAttributes": {},
                    "href": "http://localhost:8080/lb-mgmt-rest-service/management/loadbalancers/usage?startTime=2011-01-11&endTime=2013-01-12&offset=30&limit=5",
                    "rel": "next"
                }
            },
            {
                "link": {
                    "otherAttributes": {},
                    "href": "http://localhost:8080/lb-mgmt-rest-service/management/loadbalancers/usage?startTime=2011-01-11&endTime=2013-01-12&offset=20&limit=5",
                    "rel": "previous"
                }
            }
        ]
    }

                    
