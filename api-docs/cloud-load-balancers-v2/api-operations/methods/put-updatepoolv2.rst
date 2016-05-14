.. _update-pool-v2:

Update a pool
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v2.0/lbaas/pools/{pool_id}



The update operation enables you to change the
following pool attributes:

-  ``name``

-  ``description``

-  ``admin_state_up``

-  ``lb_algorithm``

-  ``session_persistence``

.. note::
  * You cannot update the pool ``id``, ``tenant_id``, ``listener_id``,
    ``listeners``, ``healthmonitor_id``, ``protocol``, and ``members``
    immutable attributes. If you try to update any of these attributes, the
    service returns the HTTP ``Immutable (422)`` response code. If the request
    is validated, the service returns the HTTP ``Accepted (202)`` response
    code.

  * You can update a pool only if the load balancer to which the pool is
    attached has a ``provisioning_status`` of ``ACTIVE``.

The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | The request succeeded.                      |
+---------+-----------------------+---------------------------------------------+
| 202     | Accepted              | The request is validated.                   |
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
| 413     | Over Limit            | The number of items returned is greater than|
|         |                       | the allowed limit.                          |
+---------+-----------------------+---------------------------------------------+
| 422     | Immutable             | The entity is unprocessable.                |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.      |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
~~~~~~~~~~~

The following table shows the URI parameters for the request.

+------------------+------------+--------------------------------------------------------------+
|Name              |Type        |Description                                                   |
+==================+============+==============================================================+
|pool_id           |csapi:uuid  | The UUID for the pool.                                       |
+------------------+------------+--------------------------------------------------------------+


The following table shows the body parameters for the request.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| pool                | plain     | xsd:dict    | A pool object.                                                                     |
| (*Required*)        |           |             |                                                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the pool, which is up (true) or down (false).          |
| (*Required*)        |           |             |                                                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | A human-readable description of the pool.                                          |
| (*Required*)        |           |             |                                                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm        | plain     | xsd:string  | The load-balancer algorithm - such as round robin (``ROUND_ROBIN``),               |
|                     |           |             | least-connections (``LEAST_CONNECTIONS``), and source IP (``SOURCE_IP``) - that is |
|                     |           |             | used to distribute traffic to the pool members. This value, which must be          |
|                     |           |             | supported,depends on the load-balancer provider. The round robin algorithm must be |
|                     |           |             | supported.                                                                          |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                | plain     | xsd:string  | A human-readable name for the pool. The name does not have to be unique.           |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| session_persistence | plain     | xsd:string  | The session persistence algorithm. This algorithm is a dictionary with ``type`` and|
| (*Required*)        |           |             | ``cookie_name`` keys.                                                              |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+



**Example: Update pool JSON request**

.. code::

    {
        "pool": {
            "admin_state_up": false,
            "description": "pool two",
            "lb_algorithm": "LEAST_CONNECTIONS",
            "name": "pool2",
            "session_persistence": {
                "type": "HTTP_COOKIE"
            }
        }
    }

Response
~~~~~~~~~~~~~~



The following table shows the body parameters for the response.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| pool                | plain     | xsd:list    | A list of pool objects.                                                            |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the pool, which is up (true) or down (false).          |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | The description of the pool.                                                       |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| healthmonitor_id    | plain     | xsd:string  | The UUID of the health monitor.                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                  | plain     | csapi:uuid  | The UUID of the pool.                                                              |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm        | plain     | xsd:string  | The load-balancer algorithm - such as round robin (``ROUND_ROBIN``), least         |
|                     |           |             | connections (``LEAST_CONNECTIONS``), and source IP (``SOURCE_IP``) - that is used  |
|                     |           |             | to distribute traffic to the pool members. This value, which must be supported,    |
|                     |           |             | depends on the load-balancer provider. The round robin algorithm must be supported.|
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners           | plain     | xsd:list    | A list of the ID of the listeners that belong to the pool.                         |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| members             | plain     | xsd:list    | A list of the members that belong to the pool.                                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                | plain     | xsd:string  | The pool name. The name does not have to be unique.                                |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol            | plain     | xsd:string  | The protocol of the pool, which is ``TCP``, ``HTTP``, or ``HTTPS``.                |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| session_persistence | plain     | xsd:string  | The session persistence algorithm. This algorithm is a dictionary with ``type`` and|
|                     |           |             | ``cookie_name`` keys.                                                              |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id           | plain     | csapi:uuid  | The UUID of the tenant who owns the pool. Only administrative users can specify a  |
|                     |           |             | tenant UUID other than their own.                                                  |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Update pool JSON response**

.. code::

    {
        "pool": {
            "admin_state_up": false,
            "description": "pool two",
            "healthmonitor_id": null,
            "id": "12ff63af-4127-4074-a251-bcb2ecc53ebe",
            "lb_algorithm": "LEAST_CONNECTIONS",
            "listeners": [
                {
                    "id": "39de4d56-d663-46e5-85a1-5b9d5fa17829"
                }
            ],
            "members": [],
            "name": "pool2",
            "protocol": "HTTP",
            "session_persistence": {
                "cookie_name": null,
                "type": "HTTP_COOKIE"
            },
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c"
        }
    }
