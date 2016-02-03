.. _get-show-load-balancers-v2:

Show load balancer details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/loadbalancers/{loadbalancer_id}


This operation returns a load balancer object identified by
``loadbalancer_id``. If the user is not an administrative user and the
load balancer object does not belong to her tenant account, the service
returns the HTTP ``Forbidden (403)`` response code.

If this operation succeeds, it returns a load balancer element that can
contain the following attributes:

-  ``id``

-  ``tenant_id``

-  ``name``

-  ``description``

-  ``vip_subnet_id``

-  ``vip_address``

-  ``admin_state_up``

-  ``provisioning_status``

-  ``operating_status``

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
| 403     | Forbidden             | The server understood the request, but is   |
|         |                       | refusing to fulfill it.                     |
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

This operation does not accept a request body.

Response
""""""""""""""""

**Example. Show load balancer details: JSON response**

This table shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| loadbalancer     | plain     | xsd:string  | A loadbalancers object.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID for the load balancer.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name             | plain     | xsd:string  | The load balancer name.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The load balancer description.                                                     |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_address      | plain     | xsd:ip      | The IP address of the VIP.                                                         |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_subnet_id    | plain     | csapi:uuid  | The UUID of the subnet on which to allocate the virtual IP (VIP) address.          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| status           | plain     | xsd:string  | The status of the load balancer. Indicates whether the load balancer is            |
|                  |           |             | operational.                                                                       |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP. Only administrative users can specify a   |
|                  |           |             | tenant UUID other than their own.                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


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
       }
    }
