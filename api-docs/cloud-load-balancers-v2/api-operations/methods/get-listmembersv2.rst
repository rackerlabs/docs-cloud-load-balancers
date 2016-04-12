.. _get-list-pool-members-v2:

List pool members
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/pools/{pool_id}/members


This operations lists all of the members that are associated with the specified
pool.



The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | The request succeeded.                      |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.      |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

The following table shows the URI parameters for the request.

+------------------+------------+--------------------------------------------------------------+
|Name              |Type        |Description                                                   |
+==================+============+==============================================================+
|pool_id           |csapi:uuid  | The UUID for the pool.                                       |
+------------------+------------+--------------------------------------------------------------+



This operation does not accept a request body.

Response
""""""""""""""""



The following table shows the body parameters for the response.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| members          | plain     | xsd:list    | A list of member objects.                                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| address          | plain     | xsd:ip      | The IP address of the member.                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the member, which is up (true) or down (false).        |
|                  |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID of the member.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port    | plain     | xsd:int     | The port where the application is hosted.                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| subnet_id        | plain     | csapi:uuid  | The UUID of the subnet.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the member. Only                                   |
|                  |           |             | administrative users can specify a tenant UUID other than their own.               |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The portion of requests or connections that the member services compared to the    |
|                  |           |             | other members of the pool. A value of 0 means that the member does not participate |
|                  |           |             | in load-balancing but still accepts persistent connections. Valid values are from  |
|                  |           |             | 0 to 256.                                                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+



**Example: List pool members JSON response**

.. code::

    {
        "members": [
            {
                "address": "10.0.0.8",
                "admin_state_up": true,
                "id": "9a7aff27-fd41-4ec1-ba4c-3eb92c629313",
                "protocol_port": 80,
                "subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2",
                "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c",
                "weight": 1
            }
        ]
    }
