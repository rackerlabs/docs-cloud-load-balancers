
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-show-load-balancer-statistics-v1.0-account-loadbalancers-loadbalancerid-stats:

Show load balancer statistics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/stats

Shows statistics for a specified load balancer.

This operation provides detailed stats output, including the following information, for a specific load balancer configured and associated with the user's account:



*  connectTimeOut – Connections closed by this load balancer because the 'connect_timeout' interval was exceeded.
*  connectError – Number of transaction or protocol errors in this load balancer.
*  connectFailure – Number of connection failures in this load balancer.
*  dataTimedOut – Connections closed by this load balancer because the 'timeout' interval was exceeded.
*  keepAliveTimedOut – Connections closed by this load balancer because the 'keepalive_timeout' interval was exceeded.
*  maxConn – Maximum number of simultaneous TCP connections this load balancer has processed at any one time.
*  currentConn – Number of simultaneous connections active at the time of the request.
*  connectTimeOutSsl – SSL connections closed by this load balancer because the 'connect_timeout' interval was exceeded.
*  connectErrorSsl – Number of SSL transaction or protocol errors in this load balancer.
*  connectFailureSsl – Number of SSL connection failures in this load balancer.
*  dataTimedOutSsl – SSL connections closed by this load balancer because the 'timeout' interval was exceeded.
*  keepAliveTimedOutSsl – SSL connections closed by this load balancer because the 'keepalive_timeout' interval was exceeded.
*  maxConnSsl – Maximum number of simultaneous SSL connections this load balancer has processed at any one time.
*  currentConnSsl – Number of simultaneous SSL connections active at the time of the request.


.. note::
   The Show load balancer statistics API operation caches data for approximately 5 minutes after the initial request is sent. If the system is under high load, a 503 error response is returned to the user along with a Retry-After header suggesting to the client when to send the next request. To limit 503 error responses, the client should honor the Retry-After header. 
   
   

The information is duplicated for SSL Termination. However, if the Load Balancer is not SSL Terminated, the appropriate information will be left without a value.



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
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Show load balancer statistics: JSON response**


.. code::

    {
        "connectTimeOut":10,
        "connectError":20,
        "connectFailure":30,
        "dataTimedOut":40,
        "keepAliveTimedOut":50,
        "maxConn":60,
        "currentConn":40,
        "connectTimeOutSsl":10,
        "connectErrorSsl":20,
        "connectFailureSsl":30,
        "dataTimedOutSsl":40,
        "keepAliveTimedOutSsl":50,
        "maxConnSsl":60,
        "currentConnSsl":40
    }
    


**Example Show load balancer statistics: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <stats xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
           connectTimeOut="10"
           connectError="20"
           connectFailure="1"
           dataTimedOut="30"
           keepAliveTimedOut="40"
           maxConn="50"
           currentConn="40"
           connectTimeOutSsl="10"
           connectErrorSsl="20"
           connectFailureSsl="1"
           dataTimedOutSsl="30"
           keepAliveTimedOutSsl="40"
           maxConnSsl="50"
           currentConnSsl="40" />
    

