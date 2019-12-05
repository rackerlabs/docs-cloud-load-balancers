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
        "accountId": 548939,
        "accountUsage": {
            "accountUsageRecords": [
                {
                    "startTime": "2014-03-13T12:03:51-05:00",
                    "numLoadBalancers": 4,
                    "numPublicVips": 4,
                    "numServicenetVips": 0
                }
            ],
            "links": []
        },
        "loadBalancerUsages": [
            {
                "loadBalancerId": 2000,
                "loadBalancerName": "dev-testing",
                "links": [],
                "loadBalancerUsageRecords": [
                    {
                        "id": 22591,
                        "startTime": "2014-04-08T10:00:00-05:00",
                        "endTime": "2014-04-08T10:37:39-05:00",
                        "outgoingTransfer": 0,
                        "incomingTransfer": 0,
                        "outgoingTransferSsl": 0,
                        "incomingTransferSsl": 0,
                        "numVips": 1,
                        "vipType": "PUBLIC",
                        "averageNumConnections": 0,
                        "averageNumConnectionsSsl": 0,
                        "numPolls": 1,
                        "sslMode": "OFF"
                    }
                ]
            }
        ]
    }

**Example Show account-level usage: XML response**

.. code::

    <?xml version="1.0" encoding="UTF-8" ?>
    	<accountBilling xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" accountId="548939">
            <accountusage>
                <accountUsageRecord  numLoadBalancers="4" numPublicVips="4" numServicenetVips="0" startTime="2014-03-13T12:03:51-05:00"/>
            </accountUsage>
            <loadBalancerUsage loadBalancerId="2000" loadBalancerName="dev-testing">
                <loadBalancerUsageRecord id="22591" averageNumConnections="0.0" incomingTransfer="0" outgoingTransfer="0"
                 averageNumConnectionsSsl="0.0" incomingTransferSsl="0" outgoingTransferSsl="0" numVips="0" numPolls="0"
                 startTime="2014-04-08T10:00:00-05:00" endTime="2014-04-08T10:37:39-05:00" vipType="PUBLIC" sslMode="OFF"/>
            </loadBalancerUsage>
        </accountBilling>
