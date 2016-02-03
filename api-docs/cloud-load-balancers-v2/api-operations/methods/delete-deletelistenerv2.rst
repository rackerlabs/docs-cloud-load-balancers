.. _remove-listener-v2:

Remove listener
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    DELETE /v2.0/lbaas/listeners/{listener_id}


This operation removes a listener and its associated configuration from
the tenant account. Any and all configuration data is immediately purged
and cannot be recovered.

You cannot delete a listener if the load balancer to which it is
attached does not have a ``provisioning_status`` of ``ACTIVE``.

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


This operation does not return a response body.
