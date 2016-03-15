.. _get-list-load-balancers-v2:

List load balancers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/loadbalancers


This operation lists all load balancers that are associated with your tenant account.
This operation returns a list, which might be empty.

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

This operation does not accept a request body.

Response
""""""""""""""""


The following table shows the body parameters for the response.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| loadbalancers       | plain     | xsd:string  | A load balancer object.                                                            |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                  | plain     | csapi:uuid  | The UUID for the load balancer.                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                | plain     | xsd:string  | The load balancer name.                                                            |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | The load balancer description.                                                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_address         | plain     | xsd:ip      | The virtual IP address (VIP).                                                      |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_subnet_id       | plain     | xsd:ip      | The subnet ID of the VIP.                                                          |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners           | plain     | xsd:ip      | The listeners associated with the load balancer.                                   |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| provisioning_status | plain     | xsd:string  | The provisioning status of the load balancer.                                      |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| operating_status    | plain     | xsd:string  | The operating status of the load balancer                                          |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| status              | plain     | xsd:string  | The status of the load balancer, which indicates whether the load balancer is      |
|                     |           |             | operational.                                                                       |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id           | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP address. Only administrative users can     |
|                     |           |             | specify a tenant UUID other than their own.                                        |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: List load balancers JSON response**

.. code::

    {
        "loadbalancers": [
            {
                "id": "3b98602c-3cfe-4f91-bfa4-c3a11c9e7fe0",
                "name": "Example LB",
                "description": "A very simple example load balancer.",
                "tenant_id": "783b31af-6635-48b2-a807-091d9973e3a9",
                "admin_state_up": true,
                "status": "ACTIVE"
            },
            {
                "id": "c617c538-daa5-4ead-be88-59521d8745a7",
                "name": "Example LB",
                "description": "A very simple example load balancer.",
                "tenant_id": "783b31af-6635-48b2-a807-091d9973e3a9",
                "admin_state_up": true,
                "status": "ACTIVE"
            }
        ]
    }
