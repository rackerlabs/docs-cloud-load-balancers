.. _remove-load-balancer-v2:

Remove load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    DELETE /v2.0/lbaas/loadbalancers/{loadbalancer_id}


Removes a load balancer and its associated configuration
from the tenant account.

Any and all configuration data is immediately purged and cannot be
recovered.

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 204     | No Content            | The server has fulfilled the request but    |
|         |                       | does not need to return an entity-body.     |
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

This operation does not accept a request body.

Response
""""""""""""""""


This operation does not return a response body.
