=============================================================================
Show Current Usage -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Current Usage
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_current_usage_v1.0_account_loadbalancers_loadbalancerid_usage_current.rst#request>`__
`Response <GET_show_current_usage_v1.0_account_loadbalancers_loadbalancerid_usage_current.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/usage/current

Shows current usage.

The load balancer usage reports provide a view of all transfer activity, average number of connections, and number of virtual IPs associated with the load balancing service. Current usage represents all usage recorded within the preceding 24 hours. Values for both ``incomingTransfer`` and ``outgoingTransfer`` are expressed in bytes transferred.

The optional ``startTime`` and ``endTime`` parameters can be used to filter all usage. If the ``startTime`` parameter is supplied but the ``endTime`` parameter is not, then all usage beginning with the ``startTime`` is provided. Likewise, if the ``endTime`` parameter is supplied but the ``startTime`` parameter is not, then all usage is returned up to the ``endTime`` specified.



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





**Example Show Current Usage: JSON request**


.. code::

    {
        "links": [],
        "loadBalancerUsageRecords": [
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
                "sslMode": "OFF"
            }
        ]
    }
    


**Example Show Current Usage: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8" ?>
    	<loadBalancerUsageRecords>
    		<id>42030</id>
    		<startTime>2014-06-25T15:00:00-05:00</startTime>
    		<endTime>2014-06-25T16:00:00-05:00</endTime>
    		<outgoingTransfer>0</outgoingTransfer>
    		<incomingTransfer>0</incomingTransfer>
    		<outgoingTransferSsl>0</outgoingTransferSsl>
    		<incomingTransferSsl>0</incomingTransferSsl>
    		<numVips>1</numVips>
    		<vipType>PUBLIC</vipType>
    		<averageNumConnections>0</averageNumConnections>
    		<averageNumConnectionsSsl>0</averageNumConnectionsSsl>
    		<numPolls>0</numPolls>
    		<sslMode>OFF</sslMode>
    	</loadBalancerUsageRecords>
    

