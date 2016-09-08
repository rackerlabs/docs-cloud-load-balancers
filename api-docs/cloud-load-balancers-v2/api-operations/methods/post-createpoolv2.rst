.. _create-pool-v2:

Create a pool
^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/pools

This operation provisions a new pool based on the configuration defined
in the request. After the request is validated and progress has
started on the provisioning process, a response is returned. The
response contains a unique identifier for the pool.

The request must specify the following pool attributes:

-  ``protocol``

-  ``lb_algorithm``

-  ``listener_id``

Some attributes receive default values if you omit them from the
request. For details, see the request parameters table.

If the request cannot be fulfilled because of insufficient or invalid data,
the service returns the HTTP ``Bad Request (400)``
response code with information about the failure in the response body.
Validation errors require that you correct the error and submit the
request again.

You cannot update a pool if the load balancer to which it is attempting
to attach does not have a ``provisioning_status`` of ``ACTIVE``.

The following table shows the possible response codes for this operation.

+---------+-----------------------+-------------------------------------------+
|Response | Name                  | Description                               |
|code     |                       |                                           |
+=========+=======================+===========================================+
| 201     | Created               | The request was fulfilled and a new       |
|         |                       | resource was created.                     |
+---------+-----------------------+-------------------------------------------+
| 400     | Bad Request           | The request cannot be fulfilled due to    |
|         |                       | insufficient data or data that is not     |
|         |                       | valid. Information about the failure is in|
|         |                       | the response today. Correct the error and |
|         |                       | submit the request again.                 |
+---------+-----------------------+-------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this   |
|         |                       | operation. This error can occur if the    |
|         |                       | request is submitted with an invalid      |
|         |                       | authentication token.                     |
+---------+-----------------------+-------------------------------------------+
| 404     | Not Found             | The requested item was not found.         |
+---------+-----------------------+-------------------------------------------+
| 409     | Conflict              | The request could not be completed because|
|         |                       | of a conflict with the current state of   |
|         |                       | the resource.                             |
+---------+-----------------------+-------------------------------------------+
| 413     | Over Limit            | The number of items returned is greater   |
|         |                       | than the allowed limit.                   |
+---------+-----------------------+-------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.    |
+---------+-----------------------+-------------------------------------------+
| 503     | Service Unavailable   | The service is not available.             |
+---------+-----------------------+-------------------------------------------+

Request
"""""""

The following table shows the body parameters for the request.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| pool (*Required*)   | plain     | xsd:list    | A list of the pool objects.                                                        |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
|                     |           |             | The default is ``true``.                                                           |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | The human-readable description for the pool. If you do not specify a value, the    |
|                     |           |             | default is an empty string.                                                        |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm        | plain     | xsd:string  | The load-balancer algorithm - such as round robin (``ROUND_ROBIN``), least         |
| (*Required*)        |           |             | connections (``LEAST_CONNECTIONS``) and source IP (``SOURCE_IP``) - that is used to|
|                     |           |             | distribute traffic to the pool members. This value, which must be supported,       |
|                     |           |             | depends on the load balancer provider. The round robin algorithm must be supported.|
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listener_id         | plain     | csapi:uuid  | The UUID of the listener in which this pool becomes the default pool. Each listener|
| (*Required*)        |           |             | can have only one default pool.                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                | plain     | xsd:string  | The pool name. The name does not have to be unique. If you do not specify a value, |
|                     |           |             | the default is an empty string.                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol            | plain     | xsd:string  | The protocol of the pool, which is ``TCP``, ``HTTP``, or ``HTTPS``.                |
| (*Required*)        |           |             |                                                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| session_persistence | plain     | xsd:list    | This list defines the cookie name and cookie type used for the pool.               |
|                     |           |             | The default is an empty dictionary.                                                |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Create a pool JSON request**

.. code::

    {
        "pool": {
            "admin_state_up": true,
            "description": "simple pool",
            "lb_algorithm": "ROUND_ROBIN",
            "listener_id": "39de4d56-d663-46e5-85a1-5b9d5fa17829",
            "name": "pool1",
            "protocol": "HTTP",
            "session_persistence": {
                "cookie_name": "my_cookie",
                "type": "APP_COOKIE"
            }
        }
    }

Response
""""""""

The following table shows the body parameters for the response.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| pool                | plain     | xsd:dict    | A pool object.                                                                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the pool, which is up (true) or down (false).          |
| (optional)          |           |             |                                                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | The description of the pool.                                                       |
| (optional)          |           |             |                                                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| healthmonitor_id    | plain     | xsd:string  | The UUID of the health monitor.                                                    |
| (optional)          |           |             |                                                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                  | plain     | csapi:uuid  | The UUID of the pool.                                                              |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm        | plain     | xsd:string  | The load-balancer algorithm - round robin (``ROUND_ROBIN``), least                 |
|                     |           |             | connections (``LEAST_CONNECTIONS``) and source IP (``SOURCE_IP``) - that is used to|
|                     |           |             | distribute traffic to the pool members. This value, which must be supported,       |
|                     |           |             | depends on the load balancer provider. The round robin algorithm must be supported.|
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners_id        | plain     | csapi:uuid  | The UUID of the listeners.                                                         |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| members             | plain     | xsd:list    | The list of members that belong to the pool.                                       |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                | plain     | xsd:string  | The pool name. The name does not have to be unique.                                |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol            | plain     | xsd:string  | The protocol of the pool, which is ``TCP``, ``HTTP``, or ``HTTPS``.                |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| session_persistence | plain     | xsd:string  | The session persistence algorithm. This algorithm is a dictionary with ``type`` and|
| (optional)          |           |             | ``cookie_name`` keys.                                                              |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id           | plain     | csapi:uuid  | The UUID of the tenant who owns the pool. Only administrative users can specify a  |
| (optional)          |           |             | tenant UUID other than their own.                                                  |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Create a pool JSON response**

.. code::

    {
        "pool": {
            "admin_state_up": true,
            "description": "simple pool",
            "healthmonitor_id": null,
            "id": "12ff63af-4127-4074-a251-bcb2ecc53ebe",
            "lb_algorithm": "ROUND_ROBIN",
            "listeners": [
                {
                    "id": "39de4d56-d663-46e5-85a1-5b9d5fa17829"
                }
            ],
            "members": [],
            "name": "pool1",
            "protocol": "HTTP",
            "session_persistence": {
                "cookie_name": "my_cookie",
                "type": "APP_COOKIE"
            },
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c"
        }
    }
