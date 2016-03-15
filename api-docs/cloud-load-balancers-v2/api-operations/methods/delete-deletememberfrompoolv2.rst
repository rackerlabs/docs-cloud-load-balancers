.. _remove-member-from-pool-v2:

Remove a member from a pool
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    DELETE /v2.0/lbaas/pools/{pool_id}/members/{member_id}


This operation removes the specified member from the specified pool and removes
its associated configuration from the tenant account. All configuration data is
immediately purged and cannot be recovered.

A member can be deleted only if the attached load balancer has a
``provisioning_status`` of ``ACTIVE``.

The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 204     | No Content            | The server has fulfilled the request but    |
|         |                       | does not need to return a response body.    |
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
|{pool_id}         |csapi:uuid  | The UUID of the pool.                                        |
+------------------+------------+--------------------------------------------------------------+
|{member_id}       |csapi:uuid  | The UUID of the member.                                      |
+------------------+------------+--------------------------------------------------------------+

This operation does not accept a request body.

Response
""""""""""""""""


This operation does not return a response body.
