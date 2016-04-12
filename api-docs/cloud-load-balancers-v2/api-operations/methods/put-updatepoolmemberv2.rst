.. _update-pool-member-v2:

Update a pool member
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/pools/{pool_id}/members/{member_id}



This operation enables you to change one or more of the following member
attributes:

-  ``weight``

-  ``admin_state_up``

..  note::
  -  You cannot update the member ``id``, ``tenant_id``, ``address``,
     ``protocol_port``, and ``subnet_id`` attributes. If you attempt to
     update any of these attributes, the service returns the HTTP
     ``Immutable (422)`` response code.
  - You cant update a member only if the attached load balancer has a
    ``provisioning_status`` of ``ACTIVE``.

The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | The request succeeded.                      |
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
| 413     | Over Limit            | The number of items returned is greater than|
|         |                       | the allowed limit.                          |
+---------+-----------------------+---------------------------------------------+
| 422     | Immutable             | The entity is unprocessable.                |
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
|pool_id           |csapi:uuid  | The UUID of the pool.                                        |
+------------------+------------+--------------------------------------------------------------+
|member_id         |csapi:uuid  | The UUID of the member.                                      |
+------------------+------------+--------------------------------------------------------------+


The following table shows the body parameters for the request.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| member           | plain     | xsd:dict    | A member object.                                                                   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the member, which is up (``true``) or down (``false``).|
|                  |           |             | The default is ``true``.                                                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The portion of requests or connections that the member services compared to the    |
|                  |           |             | other members of the pool. A value of 0 means that the member does not participate |
|                  |           |             | in load balancing but still accepts persistent connections. Valid values are from  |
|                  |           |             | 0 to 256.                                                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Update a pool member JSON request**

.. code::

    {
        "member": {
            "admin_state_up": false,
            "weight": 5
        }
    }

Response
""""""""""""""""



The following table shows the body parameters for the response.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| member           | plain     | xsd:dict    | A member object.                                                                   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| address          | plain     | xsd:ip      | The IP address of the member.                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the member, which is up (``true``) or down (``false``).|
|                  |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID of the member.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port    | plain     | xsd:int     | The port where the application is hosted.                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| subnet_id        | plain     | xsd:int     | The UUID of the subnet on which the member resides.                                |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the member. Only administrative users can specify  |
|                  |           |             | a tenant UUID other than their own.                                                |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The portion of requests or connections that the member services compared to the    |
|                  |           |             | other members of the pool. A value of 0 means the member does not participate in   |
|                  |           |             | load balancing but still accepts persistent connections. Valid values are from 0 to|
|                  |           |             | 256.                                                                               |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: Update a pool member JSON response**

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
