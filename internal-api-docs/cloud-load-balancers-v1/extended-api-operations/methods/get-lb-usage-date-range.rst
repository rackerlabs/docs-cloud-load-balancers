.. _get-lb-usage-date-range:

Retrieve paginated load-balancer specific  usage
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/loadbalancers/usage?startTime=YYYY-MM-DDT HH:mm:ss&endTime=YYYY-MM-DDT HH:mm:ss&offset=offset&limit=limit 


This operation retrieves load-balancer specific usage for all load balancers for the given date range. The response is paginated with a default limit of 500 and a maximum limit of 1000.

The date parameters follow the ``YYYY-MM-DD`` date format. Note that usage is retained for a maximum of 
90 days. The ``startTime`` and ``endTime`` parameters are required for the call. 


The access levels for this operation are ``support``, ``service admin``, and ``billing``. 

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


                    


**Example: List load balancers usage XML response (paginated)**

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

                    


**Example: List load balancers usage JSON response (paginated): JSON**

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
