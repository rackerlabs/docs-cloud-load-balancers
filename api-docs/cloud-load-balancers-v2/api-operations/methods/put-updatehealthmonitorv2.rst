.. _update-health-monitor-v2:

Update a health monitor
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v2.0/lbaas/healthmonitors/{healthmonitor_id}



This operation enables you to change one or more of the following health monitor
attributes:

-  ``delay``

-  ``timeout``

-  ``max_retries``

-  ``http_method``

-  ``url_path``

-  ``expected_codes``

-  ``admin_state_up``

The health monitor ``id``, ``tenant_id``, ``pool_id``, and ``type`` are
immutable attributes and cannot be updated. If you specify an
unsupported attribute, the service returns the HTTP ``Immutable (422)``
response code. If the request is successful, the service returns the HTTP
``Accepted (202)`` response code.

You can update a health monitor only if the attached load balancer has a
provisioning_status value of ``ACTIVE``.

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
""""""""""""""""

The following table shows the URI parameters for the request.

+-------------------+------------+--------------------------------------------------------------+
|Name               |Type        |Description                                                   |
+===================+============+==============================================================+
|healthmonitor_id   |csapi:uuid  | The UUID for the health monitor.                             |
+-------------------+------------+--------------------------------------------------------------+



The following table shows the body parameters for the request.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| healthmonitor    | plain     | xsd:dict    | A health monitor object.                                                           |
| (*Required*)     |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the health monitor, which is up (``true``) or down     |
|                  |           |             | (``false``). Set this attribute to ``false`` to create the listener in an          |
|                  |           |             | administratively down state.                                                       |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| delay            | plain     | xsd:int     | The time, in seconds, between sending probes to members.                           |
|                  |           |             |                                                                                    |
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
| max_retries      | plain     | xsd:int     | The number of connection failures that are allowed before the status of the member |
| (*Required*)     |           |             | is changed to ``INACTIVE``. Valid values are from 1 to 10.                         |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| timeout          | plain     | xsd:int     | The maximum number of seconds for a monitor to wait for a connection to be         |
|                  |           |             | established before it times out. This value must be less than the ``delay`` value. |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| url_path         | plain     | xsd:string  | The HTTP path of the request sent by the monitor to test the health of a member.   |
|(*Required*)      |           |             | A valid value is a string that begins with a forward slash (/).                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: Update a health monitor JSON request**

.. code::

    {
        "healthmonitor": {
            "admin_state_up": false,
            "delay": "2",
            "expected_codes": "200",
            "http_method": "POST",
            "max_retries": 2,
            "timeout": 2,
            "url_path": "/page.html"
        }
    }

Response
""""""""""""""""


The following table shows the body parameters for the response.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| healthmonitor    | plain     | xsd:dict    | A health monitor object.                                                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the health monitor, which is up (``true``) or down     |
|                  |           |             | (``false``). Set this attribute to ``false`` to create the listener in an          |
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
| id               | plain     | csapi:uuid  | The UUID for the health monitor.                                                   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| max_retries      | plain     | xsd:int     | The number of connection failures that are allowed before the status of the member |
|                  |           |             | is changed to ``INACTIVE``. Valid values are from 1 to 10.                         |
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
| (optional)       |           |             | A valid value is a string that begins with a forward slash (/).                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: Update a health monitor JSON response**

.. code::

    {
        "healthmonitor": {
            "admin_state_up": false,
            "delay": 2,
            "expected_codes": "200",
            "http_method": "POST",
            "id": "0a9ac99d-0a09-4b18-8499-a0796850279a",
            "max_retries": 2,
            "pools": [
                {
                    "id": "74aa2010-a59f-4d35-a436-60a6da882819"
                }
            ],
            "tenant_id": "6f3584d5754048a18e30685362b88411",
            "timeout": 2,
            "type": "HTTP",
            "url_path": "/page.html"
        }
    }
