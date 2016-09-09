.. _update-load-balancer-v2:

Update load balancer
~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v2.0/lbaas/loadbalancers/{loadbalancer_id}

This operations enables you to change one or more of the following load
balancer attributes:

-  ``name``

-  ``description``

-  ``admin_state_up``

If the request is validated, the service returns the
``Accepted (202)`` response code.

This operation returns the updated load balancer object. The
``provisioning_status`` value can be ``ACTIVE``, ``PENDING_UPDATE``, or
``ERROR``.

Check that the load
balancer ``provisioning_status`` has changed to ``ACTIVE`` to confirm
that the update has taken effect. If the load balancer
``provisioning_status`` is ``PENDING_UPDATE``, you can poll the
load balancer object by using a **GET** operation to wait for the
changes to be applied.

The following table shows the possible response codes for this operation.

+---------+-----------------------+-------------------------------------------+
|Response | Name                  | Description                               |
|code     |                       |                                           |
+=========+=======================+===========================================+
| 200     | Success               | Request succeeded.                        |
+---------+-----------------------+-------------------------------------------+
| 202     | Accepted              | Request validated.                        |
+---------+-----------------------+-------------------------------------------+
| 400     | Bad Request           | The request is missing one or more        |
|         |                       | elements, or the values of some elements  |
|         |                       | are invalid.                              |
+---------+-----------------------+-------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this   |
|         |                       | operation. This error can occur if the    |
|         |                       | request is submitted with an invalid      |
|         |                       | authentication token.                     |
+---------+-----------------------+-------------------------------------------+
| 413     | Over Limit            | The number of items returned is above the |
|         |                       | allowed limit.                            |
+---------+-----------------------+-------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer has experienced a fault.|
+---------+-----------------------+-------------------------------------------+
| 503     | Service Unavailable   | The service is not available.             |
+---------+-----------------------+-------------------------------------------+

Request
-------

The following table shows the URI parameters for the request.

+------------------+------------+---------------------------------------------+
|Name              |Type        |Description                                  |
+==================+============+=============================================+
|loadbalancer_id   |csapi:uuid  | The UUID for the load balancer.             |
+------------------+------------+---------------------------------------------+

The following table shows the body parameters for the request.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| loadbalancer     | plain     | xsd:string  | A load balancers object.                                                           |
| (*Required*)     |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name             | plain     | xsd:string  | The load balancer name. The name does not have to be unique. If you omit the name, |
|                  |           |             | the default value is an empty string.                                              |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The load balancer description. If you omit the description, the default value is an|
|                  |           |             | empty string.                                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
| (*Required*)     |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Update a load balancer JSON request**

.. code::

    {
        "loadbalancer": {
            "admin_state_up": false,
            "description": "simple lb2",
            "name": "loadbalancer2"
        }
    }

Response
--------

The following table shows the body parameters for the response.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| loadbalancer        | plain     | xsd:string  | A load balancers object.                                                           |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                  | plain     | csapi:uuid  | The UUID for the load balancer.                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners           | plain     | xsd:string  | The listeners object for the load balancer                                         |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                | plain     | xsd:string  | The load balancer name.                                                            |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | The load balancer description.                                                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_address         | plain     | xsd:ip      | The virtual IP (VIP) address.                                                      |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_subnet_id       | plain     | csapi:uuid  | The UUID of the VIP subnet.                                                        |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id           | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP. Only administrative users can specify a   |
|                     |           |             | tenant UUID other than their own.                                                  |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| operating_status    | plain     | xsd:string  | The status of the load balancer.                                                   |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| provisioning_status | plain     | xsd:string  | The provisioning status of the load balancer.                                      |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Update a load balancer JSON response**

.. code::

    {
        "loadbalancer": {
            "admin_state_up": false,
            "description": "simple lb2",
            "id": "a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "listeners": [],
            "name": "loadbalancer2",
            "operating_status": "ONLINE",
            "provisioning_status": "PENDING_UPDATE",
            "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
            "vip_address": "10.0.0.4",
            "vip_subnet_id": "00000000-0000-0000-0000-000000000000"
        }
    }
