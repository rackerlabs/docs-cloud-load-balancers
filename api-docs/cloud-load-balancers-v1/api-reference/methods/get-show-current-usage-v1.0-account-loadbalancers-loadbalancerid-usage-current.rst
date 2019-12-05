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
        "links": [],
        "loadBalancerUsageRecord": [
            {
                "id": 42030,
                "startTime": "2014-06-25T15:00:00-05:00",
                "endTime": "2014-06-25T16:00:00-05:00",
                "outgoingTransfer": 0,
                "incomingTransfer": 0,
                "outgoingTransferSsl": 0,
                "incomingTransferSsl": 0,
                "numVips": 1,
                "vipType": "PUBLIC",
                "averageNumConnections": 0,
                "averageNumConnectionsSsl": 0,
                "numPolls": 0,
                "eventType": "DELETE_LOADBALANCER",
                "sslMode": "OFF"
            }
        ]
    }

**Example Show current usage: XML response**

.. code::

      	<loadBalancerUsageRecord id="42030" averageNumConnections="0.0" incomingTransfer="0" outgoingTransfer="0"
                 averageNumConnectionsSsl="0.0" incomingTransferSsl="0" outgoingTransferSsl="0" numVips="1" numPolls="0"
                 startTime="2014-06-25T15:00:00-05:00" endTime="2014-06-25T16:00:00-05:00" vipType="PUBLIC"
                 sslMode="OFF" eventType="DELETE_LOADBALANCER">
        </loadBalancerUsageRecord>
