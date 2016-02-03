.. _get-list-pool-members-v2:

List pool members
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/pools/{pool_id}/members


Lists all members that are associated with a pool that is associated
with your tenant account. The list of members includes only members that
belong to the pool object identified by ``pool_id``.

This operation returns a list, which might be empty. Each element in the
list is a member that can contain the following attributes:

-  ``id``

-  ``tenant_id``

-  ``address``

-  ``protocol_port``

-  ``weight``

-  ``subnet_id``

-  ``admin_state_up``

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | Request succeeded.                          |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer has experienced a fault.  |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

This operation does not accept a request body.

Response
""""""""""""""""

**Example. List pool members: JSON response**

This list shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| members          | plain     | xsd:list    | A list of member objects.                                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID for the member.                                                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID for the pool. The UUID of the tenant who owns the member. Only            |
|                  |           |             | administrative users can specify a tenant UUID other than their own.               |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| pool_id          | plain     | csapi:uuid  | The UUID of the pool to which the member belongs.                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| address          | plain     | xsd:ip      | The IP address of the member.                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port    | plain     | xsd:int     | The port where the application is hosted.                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The weight of a member determines the portion of requests or connections it        |
|                  |           |             | services compared to the other members of the pool. A value of 0 means the member  |
|                  |           |             | does not participate in load-balancing but still accepts persistent connections.   |
|                  |           |             | A valid value is from 0 to 256.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the member, which is up (true) or down (false).        |
|                  |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| status           | plain     | xsd:string  | The status of the member. Indicates whether the member is operational.             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+



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
