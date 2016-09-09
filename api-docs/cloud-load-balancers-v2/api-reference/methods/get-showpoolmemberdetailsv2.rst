.. _get-show-pool-member-details-v2:

Show pool member details
~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/lbaas/pools/{pool_id}/members/{member_id}

This operation returns the specified member that belongs to the specified pool.
If the user is not an administrative user and the pool or member object does
not belong to the user's tenant account, the service returns the HTTP
``Forbidden (403)`` response code.

The following table shows the possible response codes for this operation.

+---------+-----------------------+-------------------------------------------+
|Response | Name                  | Description                               |
|code     |                       |                                           |
+=========+=======================+===========================================+
| 200     | Success               | The request succeeded.                    |
+---------+-----------------------+-------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this   |
|         |                       | operation. This error can occur if the    |
|         |                       | request is submitted with an invalid      |
|         |                       | authentication token.                     |
+---------+-----------------------+-------------------------------------------+
| 403     | Forbidden             | The server understood the request, but    |
|         |                       | won't fulfill it.                         |
+---------+-----------------------+-------------------------------------------+
| 404     | Not Found             | The requested item was not found.         |
+---------+-----------------------+-------------------------------------------+
| 409     | Conflict              | The request could not be completed because|
|         |                       | of a conflict with the current state of   |
|         |                       | the resource.                             |
+---------+-----------------------+-------------------------------------------+
| 413     | Over Limit            | The number of items returned is greater   |
|         |                       | than the allowed limit.                   |
+---------+-----------------------+-------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.    |
+---------+-----------------------+-------------------------------------------+
| 503     | Service Unavailable   | The service is not available.             |
+---------+-----------------------+-------------------------------------------+

Request
-------

The following table shows the URI parameters for the request.

+------------------+------------+---------------------------------------------+
|Name              |Type        |Description                                  |
+==================+============+=============================================+
|pool_id           |csapi:uuid  | The UUID of the pool.                       |
+------------------+------------+---------------------------------------------+
|member_id         |csapi:uuid  | The UUID of the member.                     |
+------------------+------------+---------------------------------------------+

This operation does not accept a request body.

Response
--------

The following table shows the body parameters for the response.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| member           | plain     | xsd:dict    | A member object.                                                                   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| address          | plain     | xsd:ip      | The IP address of the member.                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the member, which is up (``true``) or down (``false``).|
|                  |           |             | The default is ``true``.                                                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID of the member.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port    | plain     | xsd:int     | The port where the application is hosted.                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| pool_id          | plain     | csapi:uuid  | The UUID of the pool to which the member belongs.                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the member. Only administrative users can specify  |
|                  |           |             | a tenant UUID other than their own.                                                |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The portion of requests or connections that the member services compared to other  |
|                  |           |             | members of the pool. A value of 0 means the member does not participate in load    |
|                  |           |             | balancing but still accepts persistent connections. Valid values arefrom 0 to 256. |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Show pool member details JSON response**

.. code::

    {
        "member": {
            "address": "10.0.0.8",
            "admin_state_up": true,
            "id": "9a7aff27-fd41-4ec1-ba4c-3eb92c629313",
            "protocol_port": 80,
            "pool_id": "a5a8839d-1ac3-41f9-9aae-f375fa4da50a",
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c",
            "weight": 1
        }
    }
