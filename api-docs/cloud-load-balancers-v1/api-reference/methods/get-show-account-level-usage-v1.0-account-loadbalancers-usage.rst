.. _get-show-account-level-usage:

Show account-level usage
~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/usage

Shows account-level usage.

The load balancer usage reports provide a view of all transfer activity,
average number  of connections, and number of virtual IPs associated with the
load balancing service.  Values for both ``incomingTransfer`` and
``outgoingTransfer`` are expressed in bytes  transferred. The optional
``startTime`` and ``endTime`` parameters can be used to filter all usage.  If
neither the ``startTime`` parameter nor the ``endTime`` parameter is supplied,
then  only the preceding 24 hours of usage are returned. If the ``startTime``
parameter  is supplied, but the ``endTime`` parameter is not, then all usage
beginning with the  ``startTime`` is provided. Likewise, if the ``endTime``
parameter is supplied but the  ``startTime`` parameter is not, then all usage
is returned up to the ``endTime``  specified.

.. note::

   Account-level usage data is available for up to 90 days of service activity.

The following table shows the possible response codes for this operation:

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

The following table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|startTime                 |Date                     |If the startTime         |
|                          |                         |parameter is supplied    |
|                          |                         |but the endTime          |
|                          |                         |parameter is not, all    |
|                          |                         |usage beginning with the |
|                          |                         |startTime is returned.   |
+--------------------------+-------------------------+-------------------------+
|endTime                   |Date                     |If the endTime parameter |
|                          |                         |is supplied but the      |
|                          |                         |startTime parameter is   |
|                          |                         |not, all usage up to the |
|                          |                         |endTime is returned.     |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

Response
--------


**Example Show account-level usage: JSON response**

.. code::

        {
            "accountUsage": {
                "links": [],
                "accountUsageRecords": [
                    {
                        "numLoadBalancers": 0,
                        "numPublicVips": 0,
                        "numServicenetVips": 0,
                        "startTime": "2019-12-05T00:00:00Z"
                    },
                    {
                        "numLoadBalancers": 1,
                        "numPublicVips": 1,
                        "numServicenetVips": 0,
                        "startTime": "2019-12-05T18:55:56Z"
                    }
                ]
            },
            "loadBalancerUsages": [
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
                        }
                    ],
                    "links": [],
                    "loadBalancerId": 331456,
                    "loadBalancerName": "a-new-loadbalancer"
                }
            ],
            "accountId": 5806065
        }

**Example Show account-level usage: XML response**

.. code::

        <accountBilling xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" xmlns:atom="http://www.w3.org/2005/Atom" accountId="5806065">
            <accountUsage>
                <accountUsageRecord numLoadBalancers="0" numPublicVips="0" numServicenetVips="0" startTime="2019-12-05T00:00:00Z"/>
                <accountUsageRecord numLoadBalancers="1" numPublicVips="1" numServicenetVips="0" startTime="2019-12-05T18:55:56Z"/>
            </accountUsage>
            <loadBalancerUsage loadBalancerId="331456" loadBalancerName="a-new-loadbalancer">
                <loadBalancerUsageRecord id="11007607" averageNumConnections="0.0" incomingTransfer="0" outgoingTransfer="0" averageNumConnectionsSsl="0.0" incomingTransferSsl="0" outgoingTransferSsl="0" numVips="1" numPolls="2" startTime="2019-12-05T18:55:56Z" endTime="2019-12-05T19:00:00Z" vipType="PUBLIC" sslMode="OFF" eventType="CREATE_LOADBALANCER"/>
                <loadBalancerUsageRecord id="11007946" averageNumConnections="0.0" incomingTransfer="710" outgoingTransfer="89" averageNumConnectionsSsl="0.0" incomingTransferSsl="0" outgoingTransferSsl="0" numVips="1" numPolls="12" startTime="2019-12-05T19:00:00Z" endTime="2019-12-05T20:00:00Z" vipType="PUBLIC" sslMode="OFF"/>
            </loadBalancerUsage>
        </accountBilling>
