.. _get-show-current-usage:

Show current usage
~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/usage/current

Shows current usage.

The load balancer usage reports provide a view of all transfer activity,
average number of connections, and number of virtual IPs associated with the
load balancing service. Current usage represents all usage recorded within the
preceding 24 hours. Values for both ``incomingTransfer`` and
``outgoingTransfer`` are expressed in bytes transferred. The following table
shows the possible response codes for this operation:

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


**Example Show current usage: JSON response**

.. code::

        {
            "loadBalancerUsageRecords": [
                {
                    "averageNumConnections": 0.0,
                    "averageNumConnectionsSsl": 0.0,
                    "numPolls": 2,
                    "sslMode": "OFF",
                    "outgoingTransfer": 0,
                    "incomingTransfer": 0,
                    "outgoingTransferSsl": 0,
                    "incomingTransferSsl": 0,
                    "numVips": 1,
                    "endTime": "2019-12-05T19:00:00Z",
                    "vipType": "PUBLIC",
                    "startTime": "2019-12-05T18:55:56Z",
                    "eventType": "CREATE_LOADBALANCER",
                    "id": 11007607
                },
                {
                    "averageNumConnections": 0.0,
                    "averageNumConnectionsSsl": 0.0,
                    "numPolls": 12,
                    "sslMode": "OFF",
                    "outgoingTransfer": 89,
                    "incomingTransfer": 710,
                    "outgoingTransferSsl": 0,
                    "incomingTransferSsl": 0,
                    "numVips": 1,
                    "endTime": "2019-12-05T20:00:00Z",
                    "vipType": "PUBLIC",
                    "startTime": "2019-12-05T19:00:00Z",
                    "id": 11007946
                }
            ],
            "links": []
        }

**Example Show current usage: XML response**

.. code::

        <loadBalancerUsage xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" xmlns:atom="http://www.w3.org/2005/Atom">
            <loadBalancerUsageRecord id="11007607" averageNumConnections="0.0" incomingTransfer="0" outgoingTransfer="0" averageNumConnectionsSsl="0.0" incomingTransferSsl="0" outgoingTransferSsl="0" numVips="1" numPolls="2" startTime="2019-12-05T18:55:56Z" endTime="2019-12-05T19:00:00Z" vipType="PUBLIC" sslMode="OFF" eventType="CREATE_LOADBALANCER"/>
            <loadBalancerUsageRecord id="11007946" averageNumConnections="0.0" incomingTransfer="710" outgoingTransfer="89" averageNumConnectionsSsl="0.0" incomingTransferSsl="0" outgoingTransferSsl="0" numVips="1" numPolls="12" startTime="2019-12-05T19:00:00Z" endTime="2019-12-05T20:00:00Z" vipType="PUBLIC" sslMode="OFF"/>
        </loadBalancerUsage>
