.. _add-member-to-pool-v2:

Add a member to pool
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/lbaas/pools/{pool_id}/members


This operation provisions a new member and adds it to a pool based on
the configuration defined in the request. After the request is
validated and progress has started on the provisioning process, a
response is returned. The response contains a unique identifier for the member.

At a minimum, you must specify the following pool attributes:

-  ``tenant_id``

-  ``address``

-  ``protocol_port``

Some attributes receive default values if you omit them from the
request. See the body parameters table for details.

-  ``admin_state_up``

-  ``weight``



If the request fails because of incorrect data, the service returns the HTTP
``Bad Request (400)`` response code with information about the failure
in the response body. Validation errors require that you correct the
error and submit the request again.


Users with an administrative role can create members on behalf of other
tenants by specifying a ``tenant_id`` attribute that is different than
their own.

To add a member, the load balancer must have a
``provisioning_status`` of ``ACTIVE``.

The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 201     | Created               | The request has been fulfilled and a new    |
|         |                       | resource was created.                       |
+---------+-----------------------+---------------------------------------------+
| 400     | Bad Request           | The request cannot be fulfilled due to      |
|         |                       | insufficient data or data that is not valid.|
|         |                       | Information about the failure is in the     |
|         |                       | response today. Correct the error and submit|
|         |                       | the request again.                          |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 404     | Not Found             | The requested item was not found.           |
+---------+-----------------------+---------------------------------------------+
| 409     | Conflict              | The request could not be completed because  |
|         |                       | of a conflict with the current state of the |
|         |                       | resource.                                   |
+---------+-----------------------+---------------------------------------------+
| 413     | Over Limit            | The number of items returned is greater than|
|         |                       | the allowed limit.                          |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.      |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
~~~~~~~~~~~



The following table shows the body parameters for the request.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| member           | plain     | xsd:dict    | A member object.                                                                   |
| (*Required*)     |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| address          | plain     | xsd:ip      | The IP address of the member that receives traffic from the load balancer.         |
| (*Required*)     |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the member, which is up (``true``) or down (``false``).|
| (*Required*)     |           |             | The default is ``true``.                                                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port    | plain     | xsd:int     | The port where the application is hosted and where the member is listening to      |
| (*Required*)     |           |             | receive traffic.                                                                   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| subnet_id        | plain     | xsd:int     | The UUID of the subnet on which the member resides. If you omit this parameter,    |
|                  |           |             | the service uses the ``vip_subnet_id`` parameter value for ``subnet_id``.          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The weight of a member determines the portion of requests or connections it        |
|                  |           |             | services compared to the other members of the pool. A value of 0 means the member  |
|                  |           |             | does not participate in load-balancing but still accepts persistent connections.   |
|                  |           |             | A valid value is from 0 to 256.  The default is ``1``.                             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the member. This parameter is required only if the |
|                  |           |             | user has an administrative role and wants to create a member for another tenant.   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+




**Example: Add a member to a pool JSON request**

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
~~~~~~~~~~~~~~



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
| subnet_id        | plain     | xsd:int     | The UUID of the subnet on which the member resides. If you omit this parameter, the|
|                  |           |             | services uses the ``vip_subnet_id`` parameter value for the ``subnet_id``.         |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the member. Only administrative users can specify a|
|                  |           |             | tenant UUID other than their own.                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| weight           | plain     | xsd:int     | The portion of requests or connections that the member services compared to the    |
| (optional)       |           |             | other members of the pool. A value of 0 means that the member does not participate |
|                  |           |             | in load balancing but still accepts persistent connections. Valid value are from 0 |
|                  |           |             | 256. The default is 1.                                                             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: Add a member to a pool JSON response**

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
