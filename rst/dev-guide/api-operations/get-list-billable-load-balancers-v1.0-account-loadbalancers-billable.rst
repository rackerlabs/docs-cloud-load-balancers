
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

List billable load balancers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{account}/loadbalancers/billable

Lists billable load balancers for a specified date range.

The response is paginated with a default limit of 500 and a maximum limit of 1000.

The load balancer usage reports provide a view of all transfer activity, average number of connections, and number of virtual IPs associated with the load balancing service. Values for both ``incomingTransfer`` and ``outgoingTransfer`` are expressed in bytes transferred.

The optional ``startTime`` and ``endTime`` parameters can be used to filter all usage. If the ``startTime`` parameter is supplied but the ``endTime`` parameter is not, then all usage beginning with the ``startTime`` is provided. Likewise, if the ``endTime`` parameter is supplied but the ``startTime`` parameter is not, then all usage is returned up to the ``endTime`` specified.

.. note::
   Historical usage data is available for up to 90 days of service activity.
   
   



This table shows the possible response codes for this operation:


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
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|startTime                 |Date *(Optional)*        |If the startTime         |
|                          |                         |parameter is supplied    |
|                          |                         |but the endTime          |
|                          |                         |parameter is not, all    |
|                          |                         |usage beginning with the |
|                          |                         |startTime is returned.   |
+--------------------------+-------------------------+-------------------------+
|endTime                   |Date *(Optional)*        |If the endTime parameter |
|                          |                         |is supplied but the      |
|                          |                         |startTime parameter is   |
|                          |                         |not, all usage up to the |
|                          |                         |endTime is returned.     |
+--------------------------+-------------------------+-------------------------+
|offset                    |String *(Optional)*      |The pagination offset.   |
+--------------------------+-------------------------+-------------------------+
|limit                     |String *(Optional)*      |The pagination limit.    |
|                          |                         |The response is          |
|                          |                         |paginated with a default |
|                          |                         |limit of 500 and a       |
|                          |                         |maximum limit of 1000.   |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




Response
""""""""""""""""










**Example List billable load balancers: JSON response**


.. code::

    {
        "loadBalancers": [
            {
                "name": "lb01",
                "id": 761,
                "port": 80,
                "protocol": "HTTP",
                "algorithm": "RANDOM",
                "status": "DELETED",
                "created": {
                    "time": "2012-01-23T17:09:08-06:00"
                },
                "updated": {
                    "time": "2012-01-27T15:15:58-06:00"
                }
            },
            {
                "name": "lb02",
                "id": 762,
                "port": 80,
                "protocol": "HTTP",
                "algorithm": "RANDOM",
                "status": "DELETED",
                "created": {
                    "time": "2012-01-23T17:10:30-06:00"
                },
                "updated": {
                    "time": "2012-01-27T15:26:47-06:00"
                }
            }
        ],
        "links": [
            {
                "otherAttributes": {},
                "href": "http://localhost:8080/lb-mgmt-rest-service/528830/loadbalancers/billable?startTime=2012-01-27&endTime=2012-02-26&offset=4&limit=2",
                "rel": "next"
            },
            {
                "otherAttributes": {},
                "href": "http://localhost:8080/lb-mgmt-rest-service/528830/loadbalancers/billable?startTime=2012-01-27&endTime=2012-02-26&offset=0&limit=2",
                "rel": "previous"
            }
        ]
    }


**Example List billable load balancers: XML response**


.. code::

    <loadBalancers
        xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom">
        <loadBalancer id="761" name="lb01" algorithm="RANDOM"
            protocol="HTTP" port="80" status="DELETED">
            <created time="2012-01-23T17:09:08-06:00"/>
            <updated time="2012-01-27T15:15:58-06:00"/>
        </loadBalancer>
        <loadBalancer id="762" name="lb02" algorithm="RANDOM"
            protocol="HTTP" port="80" status="DELETED">
            <created time="2012-01-23T17:10:30-06:00"/>
            <updated time="2012-01-27T15:26:47-06:00"/>
        </loadBalancer>
        <atom:link
            href="http://localhost:8080/lb-mgmt-rest-service/528830/loadbalancers/billable?startTime=2012-01-27&amp;endTime=2012-02-26&amp;offset=4&amp;limit=2"
            rel="next"/>
        <atom:link
            href="http://localhost:8080/lb-mgmt-rest-service/528830/loadbalancers/billable?startTime=2012-01-27&amp;endTime=2012-02-26&amp;offset=0&amp;limit=2"
            rel="previous"/>
    </loadBalancers>

