.. _get-show-health-monitor-details-v2:

Show health monitor details
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/lbaas/healthmonitors/{healthmonitor_id}

This operation returns details about the specified health monitor. If the user
is not an administrative user and the health monitor object does not belong to
the user's tenant account, the service returns the HTTP ``Forbidden (403)``
response code.

The following table shows the possible response codes for this operation.

+---------+-----------------------+-------------------------------------------+
|Response | Name                  | Description                               |
|code     |                       |                                           |
+=========+=======================+===========================================+
| 200     | Success               | Request succeeded.                        |
+---------+-----------------------+-------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this   |
|         |                       | operation. This error can occur if the    |
|         |                       | request is submitted with an invalid      |
|         |                       | authentication token.                     |
+---------+-----------------------+-------------------------------------------+
| 403     | Forbidden             | The server understood the request, but    |
|         |                       | won't fulfill it.                         |
+---------+-----------------------+-------------------------------------------+
| 404     | Not Found             | The requested item was not found.         |
+---------+-----------------------+-------------------------------------------+
| 409     | Conflict              | The request could not be completed because|
|         |                       | of a conflict with the current state of   |
|         |                       | resource.                                 |
+---------+-----------------------+-------------------------------------------+
| 413     | Over Limit            | The number of items returned is greater   |
|         |                       | the allowed limit.                        |
+---------+-----------------------+-------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.    |
+---------+-----------------------+-------------------------------------------+
| 503     | Service Unavailable   | The service is not available.             |
+---------+-----------------------+-------------------------------------------+

Request
-------

The following table shows the URI parameters for the request.

+-------------------+------------+--------------------------------------------+
|Name               |Type        |Description                                 |
+===================+============+============================================+
|healthmonitor_id   |csapi:uuid  | The UUID for the health monitor.           |
+-------------------+------------+--------------------------------------------+

This operation does not accept a request body.

Response
--------

The following table shows the body parameters for the response.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| healthmonitor    | plain     | xsd:dict    | A health monitor object.                                                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (``true``) or down      |
| (optional)       |           |             | (``false``). Set this attribute to ``false`` to create the listener in an a        |
|                  |           |             | administratively down state.                                                       |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| delay            | plain     | xsd:int     | The time, in seconds, between sending probes to members.                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| expected_codes   | plain     | xsd:string  | The list of HTTP status codes expected in response from the member to declare it   |
|                  |           |             | healthy. Specify one of the following values:                                      |
|                  |           |             |                                                                                    |
|                  |           |             | - A single value, such as ``200``.                                                 |
|                  |           |             | - A list, such as ``200, 202``.                                                    |
|                  |           |             | - A range, such as ``200-204``.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| http_method      | plain     | xsd:string  | The HTTP method that the monitor uses for requests.                                |
|                  |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID of the health monitor.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| max_retries      | plain     | xsd:int     | The number of connection failures allowed before the status of the member is       |
|                  |           |             | changed to ``INACTIVE``. Valid values are from 1 to 10.                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| pools            | plain     | xsd:list    | A list of the UUID of the pools associated with the health monitor.                |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the health monitor. Only administrative users can  |
|                  |           |             | specify a tenant UUID other than their own.                                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| timeout          | plain     | xsd:int     | The maximum number of seconds for a monitor to wait for a connection to be         |
|                  |           |             | established before it times out. This value must be less than the ``delay`` value. |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| type             | plain     | xsd:string  | The type of probe sent by the load balancer to verify the member state.            |
|                  |           |             | Valid values are ``PING``, ``TCP``, ``HTTP``, or ``HTTPS``.                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| url_path         | plain     | xsd:string  | The HTTP path of the request sent by the monitor to test the health of a member.   |
|                  |           |             | A valid value is a string that begins with a forward slash (/).                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Show health monitor details JSON response**

.. code::

    {
        "healthmonitor": {
            "admin_state_up": true,
            "delay": 1,
            "expected_codes": "200,201,202",
            "http_method": "GET",
            "id": "0a9ac99d-0a09-4b18-8499-a0796850279a",
            "max_retries": 5,
            "pools": [
                {
                    "id": "74aa2010-a59f-4d35-a436-60a6da882819"
                }
            ],
            "tenant_id": "6f3584d5754048a18e30685362b88411",
            "timeout": 1,
            "type": "HTTP",
            "url_path": "/index.html"
        }
    }
