.. _get-account-usage:

Retrieve paginated account-specific usage
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/accounts/usage?startTime=YYYY-MM-DDT HH:mm:ss&endTime=YYYY-MM-DDT HH:mm:ss&offset=offset&limit=limit  


This operation retrieves  account-specific usage for all accounts for the given date range. The 
response is paginated with a default limit of 500 and a maximum limit of 1000.

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


                    


**Example: List accounts usage XML response (paginated)**

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

                    


**Example: List accounts usage JSON response (paginated)**

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

                    


