.. _create-health-monitorv2:

Create health monitor
^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/healthmonitors


This operation provisions a new health monitor based on the
configuration defined in the request. After the request is
validated and progress has started on the provisioning process, a
response is returned. The response contains a unique identifier for the health
monitor.

The request must specify the following health monitor attributes, at a minimum:

-  ``tenant_id``

-  ``type``

-  ``delay``

-  ``timeout``

-  ``max_retries``

-  ``pool_id``

The following attributes receive default values if you omit them from the
request, and are useful only when you specify a health monitor type of
``HTTP`` or ``HTTPS``:

-  ``http_method``

-  ``url_path``

-  ``expected_codes``

-  ``admin_state_up``

If the request cannot be fulfilled because of insufficient data or data that
is not valid, an HTTP ``400 (Bad Request)`` error response is returned with
information regarding the nature of the failure in the response body.
Failures in the validation process are non-recoverable and require you to
correct the cause of the failure and resend the request.

Users with an administrative role can create health monitors on behalf
of other tenants by specifying a ``tenant_id`` attribute different than
their own.

To create a health monitor, the load balancer to which it is being
attached must have an ``ACTIVE`` provisioning status.

The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 201     | Created               | The request was fulfilled and a new resource|
|         |                       | was created.                                |
+---------+-----------------------+---------------------------------------------+
| 400     | Bad Request           | The request cannot be fulfilled due to      |
|         |                       | insufficient data or data that is not valid.|
|         |                       | Information about the failure is in the     |
|         |                       | response today. Correct the error and submit|
|         |                       | the request again.                          |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
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



The following table shows the body parameters for the request.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| healthmonitor    | plain     | xsd:dict    | A health monitor object.                                                           |
| (*Required*)     |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| delay            | plain     | xsd:int     | The time, in seconds, between sending probes to members.                           |
| (*Required*)     |           |             |                                                                                    |
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
| pool_id          | plain     | csapi:uuid  | The UUID of the pool associated with the health monitor.                           |
| (*Required*)     |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| timeout          | plain     | xsd:int     | The maximum number of seconds for a monitor to wait for a connection to be         |
| (*Required*)     |           |             | established before it times out. This value must be less than the ``delay`` value. |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| type             | plain     | xsd:string  | The type of probe sent by the load balancer to verify the member state.            |
| (*Required*)     |           |             | Valid values are ``PING``, ``TCP``, ``HTTP``, or ``HTTPS``.                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| url_path         | plain     | xsd:string  | The HTTP path of the request sent by the monitor to test the health of a member.   |
|                  |           |             | A valid value is a string that begins with a forward slash (/).                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the health monitor. Only administrative users can  |
|                  |           |             | specify a tenant UUID other than their own.                                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+




**Example: Create a health monitor JSON request**

.. code::

    {
        "healthmonitor": {
            "admin_state_up": true,
            "delay": "1",
            "expected_codes": "200,201,202",
            "http_method": "GET",
            "max_retries": 5,
            "pool_id": "74aa2010-a59f-4d35-a436-60a6da882819",
            "timeout": 1,
            "type": "HTTP",
            "url_path": "/index.html"
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
| id               | plain     | csapi:uuid  | The UUID of the health monitor.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| max_retries      | plain     | xsd:int     | The number of connection failures that are allowed before the status of the member |
|                  |           |             | is changed to ``INACTIVE``. Valid value are from 1 to 10.                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| pools            | plain     | xsd:list    | A list of the pool IDs associated with the health monitor.                         |
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


**Example: Create a health monitor JSON response**

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
