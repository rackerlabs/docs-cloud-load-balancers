.. _create-load-balancers-v2:

Create a load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/loadbalancers


This operation provisions a new load balancer based on the configuration
defined in the request. After the request is validated and
progress has started on the provisioning process, a response object is
returned. The response contains a unique identifier for the load balancer
and the status of provisioning the load balancer.

The ``provisioning_status`` of the load balancer in the response can
have one of the following values: ``ACTIVE``, ``PENDING_CREATE``, or
``ERROR``.

If the status is ``PENDING_CREATE``, you can view the progress of
the provisioning operation by performing a **GET** operation on
``/lbaas/loadbalancers/{loadbalancer_id}``. When the status of the load
balancer changes to ``ACTIVE``, the load balancer was successfully
provisioned and is ready to handle traffic.

Users with an administrative role can create load balancers on behalf of
other tenants by specifying a ``tenant_id`` attribute different than
their own.

The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 201     | Created               | The request was fulfilled and the new       |
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
| 500     | Load Balancer Fault   | The load balancer has experienced a fault.  |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

The following table shows the body parameters for the request.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| name             | plain     | xsd:string  | The load balancer name. The name does not have to be unique. If you omit the name, |
|                  |           |             | the default value is an empty string.                                              |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The load balancer description. If you omit the description, the default value is an|
|                  |           |             | empty string.                                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_subnet_id    | plain     | csapi:uuid  | The UUID of the subnet on which to allocate the virtual IP (VIP) address for the   |
| (*Required*)     |           |             | load balancer. Tenants can create load balancer VIP addresses only on networks that|
|                  |           |             | are authorized by the policy, such as their own networks or shared or provider     |
|                  |           |             | networks.                                                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP address. Only required if the caller has an|
|                  |           |             | administrative role and wants to create a load balancer for another tenant. Only   |
|                  |           |             | administrative users can specify a tenant UUID other than their own.               |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_address      | plain     | xsd:ip      | The VIP address. You can supply a ``vip_address`` if you own the subnet on which   |
|                  |           |             | the load balancer’s VIP will be created. If this parameter is omitted from the     |
|                  |           |             | request, the service allocates a VIP address from the subnet of the load balancer  |
|                  |           |             | VIP.                                                                               |+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| provider         | plain     | xsd:string  | The name of the provider.                                                          |
|                  |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The admin state. If this parameter is omitted from the request, the default value  |
|                  |           |             | is ``true``.                                                                       |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
|                  |           |             | If this parameter is omitted from the request, the default value is ``true``.      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: Create a load balancer JSON request**

.. code::

    {
        "loadbalancer": {
            "name": "loadbalancer1",
            "description": "simple lb",
            "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
            "vip_subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2",
            "vip_address": "10.0.0.4",
            "admin_state_up": true
        }
    }

Response
""""""""""""""""

The following table shows the body parameters for the response.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| loadbalancer        | plain     | xsd:string  | A load balancers object.                                                           |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                  | plain     | csapi:uuid  | The UUID for the load balancer.                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                | plain     | xsd:string  | The load balancer name.                                                            |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | The load balancer description.                                                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_address         | plain     | xsd:ip      | The virtual IP (VIP) address.                                                      |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| operating_status    | plain     | xsd:string  | The operational status of the load balancer.                                       |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| provisioning_status | plain     | xsd:string  | The provisioning status of the load balancer.                                      |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id           | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP. Only administrative users can specify a   |
|                     |           |             | tenant UUID other than their own.                                                  |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_subnet_id       | plain     | csapi:uuid  | The UUID of the VIP subnet.                                                        |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners           | plain     | xsd:string  | The listeners object for the load balancer                                         |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Create a load balancer JSON response**

.. code::

    {
        "loadbalancer": {
            "admin_state_up": true,
            "description": "simple lb",
            "id": "a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "listeners": [],
            "name": "loadbalancer1",
            "operating_status": "ONLINE",
            "provisioning_status": "ACTIVE",
            "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
            "vip_address": "10.0.0.4",
            "vip_subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2"
        }
    }
