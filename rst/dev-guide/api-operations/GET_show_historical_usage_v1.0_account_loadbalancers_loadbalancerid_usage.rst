=============================================================================
Show Historical Usage -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Historical Usage
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_historical_usage_v1.0_account_loadbalancers_loadbalancerid_usage.rst#request>`__
`Response <GET_show_historical_usage_v1.0_account_loadbalancers_loadbalancerid_usage.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/usage

Shows historical usage.

The load balancer usage reports provide a view of all transfer activity, average number of connections, and number of virtual IPs associated with the load balancing service. Values for both ``incomingTransfer`` and ``outgoingTransfer`` are expressed in bytes transferred.

The optional ``startTime`` and ``endTime`` parameters can be used to filter all usage. If the ``startTime`` parameter is supplied but the ``endTime`` parameter is not, then all usage beginning with the ``startTime`` is provided. Likewise, if the ``endTime`` parameter is supplied but the ``startTime`` parameter is not, then all usage is returned up to the ``endTime`` specified.

Historical usage data is available for up to 90 days of service activity.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|413                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |xsd:string               |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |xsd:string *(Required)*  |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|startTime                 |xsd:date *(Required)*    |If the startTime         |
|                          |                         |parameter is supplied    |
|                          |                         |but the endTime          |
|                          |                         |parameter is not, all    |
|                          |                         |usage beginning with the |
|                          |                         |startTime is returned.   |
+--------------------------+-------------------------+-------------------------+
|endTime                   |xsd:date *(Required)*    |If the endTime parameter |
|                          |                         |is supplied but the      |
|                          |                         |startTime parameter is   |
|                          |                         |not, all usage up to the |
|                          |                         |endTime is returned.     |
+--------------------------+-------------------------+-------------------------+







Response
^^^^^^^^^^^^^^^^^^





**Example Show Historical Usage: JSON request**


.. code::

    {
        "loadBalancerUsageRecords": [
            {
                "id": 394,
                "averageNumConnections": 0.0,
                "incomingTransfer": 0,
                "outgoingTransfer": 0,
                "averageNumConnectionsSsl": 0.0,
                "incomingTransferSsl": 0,
                "outgoingTransferSsl": 0,
                "numVips": 1,
                "numPolls": 32,
                "startTime": "2010-12-21T12:32:07-06:00",
                "endTime": "2010-12-21T16:23:54-06:00" ,
                "vipType": "PUBLIC",
                "sslMode": "OFF",
                "eventType": "CREATE_LOADBALANCER"
            },
            {
                "id": 473,
                "averageNumConnections": 0.0,
                "incomingTransfer": 0,
                "outgoingTransfer": 0,
                "averageNumConnectionsSsl": 0.0,
                "incomingTransferSsl": 0,
                "outgoingTransferSsl": 0,
                "numVips": 2,
                "numPolls": 5,
                "startTime": "2010-12-21T12:32:07-06:00",
                "endTime": "2010-12-21T12:36:30-06:00" ,
                "vipType": "PUBLIC",
                "sslMode": "MIXED",
                "eventType": "SSL_MIXED_ON"
            }
        ]
    }


**Example Show Historical Usage: XML request**


.. code::

    <loadBalancerUsage xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <loadBalancerUsageRecord
                id="394"
                averageNumConnections="0.0"
                incomingTransfer="0"
                outgoingTransfer="0"
                averageNumConnectionsSsl="0.0"
                incomingTransferSsl="0"
                outgoingTransferSsl="0"
                numVips="1"
                numPolls="32"
                startTime="2010-12-21T12:32:07-06:00"
                endTime="2010-12-21T16:23:54-06:00"
                vipType="PUBLIC"
                sslMode="OFF"
                eventType="CREATE_LOADBALANCER"/>
        <loadBalancerUsageRecord
                id="473"
                averageNumConnections="0.0"
                incomingTransfer="0"
                outgoingTransfer="0"
                averageNumConnectionsSsl="0.0"
                incomingTransferSsl="0"
                outgoingTransferSsl="0"
                numVips="2"
                numPolls="5"
                startTime="2010-12-21T12:32:07-06:00"
                endTime="2010-12-21T12:36:30-06:00"
                vipType="PUBLIC"
                sslMode="MIXED"
                eventType="SSL_MIXED_ON"/>
    </loadBalancerUsage>

