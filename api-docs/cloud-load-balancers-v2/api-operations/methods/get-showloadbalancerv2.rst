.. _get-show-load-balancers-v2:

Show load balancer details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/loadbalancers/{loadbalancer_id}


This operation returns the load balancer object identified by
``loadbalancer_id``. If the user is not an administrative user and the
load balancer object does not belong to the user's tenant account, the service
returns the HTTP ``Forbidden (403)`` response code.

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
| 403     | Forbidden             | The server understood the request, but      |
|         |                       | won't fulfill it.                           |
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
""""""""""""""""

The following table shows the URI parameters for the request.

+------------------+------------+--------------------------------------------------------------+
|Name              |Type        |Description                                                   |
+==================+============+==============================================================+
|loadbalancer_id   |csapi:uuid  | The UUID for the load balancer.                              |
+------------------+------------+--------------------------------------------------------------+


This operation does not accept a request body.

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
| vip_subnet_id       | plain     | csapi:uuid  | The UUID of the subnet on which to allocate the VIP address.                       |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| status              | plain     | xsd:string  | The status of the load balancer, which indicates whether the load balancer is      |
|                     |           |             | operational.                                                                       |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id           | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP address. Only administrative users can     |
|                     |           |             | specify a tenant UUID other than their own.                                        |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| provisioning_status | plain     | xsd:string  | The provisioning status of the load balancer.                                      |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| operating_status    | plain     | xsd:string  | The operating status of the load balancer                                          |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners           | plain     | xsd:list    | A list of the listeners IDs that belong to the load balancers.                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Show load balancer details JSON response**

.. code::

    {
       "loadbalancer":{
          "id":"8992a43f-83af-4b49-9afd-c2bfbd82d7d7",
          "name":"Example LB",
          "description":"A very simple example load balancer.",
          "vip_address":"1.2.3.4",
          "vip_subnet_id":"SUBNET_ID",
          "tenant_id":"7725fe12-1c14-4f45-ba8e-44bf01763578",
          "admin_state_up":true,
          "status":"ACTIVE"
          "listeners": [
                    {
                        "id": "35cb8516-1173-4035-8dae-0dae3453f37f"
                    }
                ],
       }
    }
