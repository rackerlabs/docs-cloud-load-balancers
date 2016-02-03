.. _update-pool-member-v2:

Update pool member
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/pools/{pool_id}/members/{member_id}


Upon successful validation of the request, the service returns the HTTP
``OK (200)`` response code.

The update operation enables you to change one or more of these pool
attributes:

-  ``weight``

-  ``admin_state_up``

..  note:: 
  -  You cannot update the member ID, ``tenant_id``, ``address``,
     ``protocol_port``, and ``subnet_id`` attributes. If you attempt to
     update any of these attributes, the service returns the HTTP
     ``Immutable (422)`` response code.
  - You cannot update a member if the attached load balancer does not have a
    ``provisioning_status`` of ``ACTIVE``.

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | Request succeeded.                          |
+---------+-----------------------+---------------------------------------------+
| 400     | Bad Request           | The request is missing one or more          |
|         |                       | elements, or the values of some elements    |
|         |                       | are invalid.                                |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 413     | Over Limit            | The number of items returned is above the   |
|         |                       | allowed limit.                              |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer has experienced a fault.  |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

**Example. Update pool member: JSON request**

This list shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| member           | plain     | xsd:dict    | A member object.                                                                   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| pool_id          | plain     | csapi:uuid  | The UUID of the pool to which the member belongs.                                  |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The weight of a member determines the portion of requests or connections it        |
|                  |           |             | services compared to the other members of the pool. A value of 0 means the member  |
|                  |           |             | does not participate in load-balancing but still accepts persistent connections.   |
|                  |           |             | A valid value is from 0 to 256.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the member, which is up (true) or down (false).        |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


.. code::  

    {
        "member": {
            "admin_state_up": false,
            "weight": 5
        }
    }

Response
""""""""""""""""

**Example. Update pool member: JSON response**

This table shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| member           | plain     | xsd:dict    | A member object.                                                                   |
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
        "member": {
            "address": "10.0.0.8",
            "admin_state_up": false,
            "id": "9a7aff27-fd41-4ec1-ba4c-3eb92c629313",
            "protocol_port": 80,
            "subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2",
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c",
            "weight": 5
        }
    }
