.. _add-member-to-pool-v2:

Add member to pool
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/pools/{pool_id}/members


This operation provisions a new member and adds it to a pool based on
the configuration defined in the request object. After the request is
validated and progress has started on the provisioning process, a
response object is returned. The object contains a unique identifier.

At a minimum, you must specify the following pool attributes:

-  ``tenant_id``. Only required if the caller has an administrative role
   and wants to create a pool for another tenant.

-  ``address``. The IP address of the member to receive traffic from the
   load balancer.

-  ``protocol_port`` The port on which the member is listening to
   receive traffic.

Some attributes receive default values if you omit them from the
request:

-  ``admin_state_up``. Default is ``true``.

-  ``weight``. Default is ``1``.

If you omit the ``subnet_id`` parameter, LBaaS uses the
``vip_subnet_id`` parameter value for the subnet ID.

If the request fails due to incorrect data, the service returns the HTTP
``Bad Request (400)`` response code with information about the failure
in the response body. Validation errors require that you correct the
error and submit the request again.

To configure all documented member features at creation time, specify
additional elements or attributes in the request.

Users with an administrative role can create members on behalf of other
tenants by specifying a ``tenant_id`` attribute that is different than
their own.

To update a member, the load balancer must have a
``provisioning_status`` of ``ACTIVE``.

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 201     | Created               | The request has been fulfilled and resulted |
|         |                       | in a new resource being created.            |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 404     | Not Found             | The requested item was not found.           |
+---------+-----------------------+---------------------------------------------+
| 409     | Conflict              | The request could not be completed due to a |
|         |                       | conflict with the current state of the      |
|         |                       | resource.                                   |
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

**Example. Add member to a pool: JSON request**

This list shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| member           | plain     | xsd:dict    | A member object.                                                                   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID for the pool. The UUID of the tenant who owns the member. Only            |
|                  |           |             | administrative users can specify a tenant UUID other than their own.               |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| address          | plain     | xsd:ip      | The IP address of the member.                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port    | plain     | xsd:int     | The port where the application is hosted.                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| subnet_id        | plain     | xsd:int     | If you omit this parameter, LBaaS uses the ``vip_subnet_id`` parameter value       |
| (optional)       |           |             | for the subnet UUID.                                                               |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+

.. code::  

    {
        "member": {
            "address": "10.0.0.8",
            "admin_state_up": true,
            "protocol_port": "80",
            "subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2",
            "weight": "1"
        }
    }

Response
""""""""""""""""

**Example. Add member to pool: JSON response**

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
| subnet_id        | plain     | xsd:int     | If you omit this parameter, LBaaS uses the ``vip_subnet_id`` parameter value       |
| (optional)       |           |             | for the subnet UUID.                                                               |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| address          | plain     | xsd:ip      | The IP address of the member.                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port    | plain     | xsd:int     | The port where the application is hosted.                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The weight of a member determines the portion of requests or connections it        |
| (optional)       |           |             | services compared to the other members of the pool. A value of 0 means the member  |
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
            "admin_state_up": true,
            "id": "9a7aff27-fd41-4ec1-ba4c-3eb92c629313",
            "protocol_port": 80,
            "subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2",
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c",
            "weight": 1
        }
    }
