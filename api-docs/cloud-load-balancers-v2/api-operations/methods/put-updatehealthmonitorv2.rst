.. _update-health-monitor-v2:

Update health monitor
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v2.0/lbaas/healthmonitors/{healthmonitor_id}


Upon successful validation of the request, the service returns the HTTP
``Accepted (202)`` response code.

The update operation enables you to change one or more health monitor
attributes:

-  ``delay``

-  ``timeout``

-  ``max_retries``

-  ``http_method``

-  ``url_path``

-  ``expected_codes``

-  ``admin_state_up``

.. note::
  The health monitor ID, ``tenant_id``, ``pool_id``, and type are
  immutable attributes and cannot be updated. If you specify an
  unsupported attribute, the service returns the HTTP ``Immutable (422)``
  response code.

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | Request succeeded.                          |
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

**Example. Update health monitor: JSON request**

This table shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| healthmonitor    | plain     | xsd:dict    | A healthmonitor object.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| delay            | plain     | xsd:int     | The time, in seconds, between sending probes to members.                           |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| timeout          | plain     | xsd:int     | The maximum number of seconds for a monitor to wait for a connection to be         |
| (optional)       |           |             | established before it times out. This value must be less than the delay value.     |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| max_retries      | plain     | xsd:int     | The number of allowed connection failures before changing the status of the member |
|                  |           |             | to INACTIVE. A valid value is from 1 to 10.                                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| http_method      | plain     | xsd:string  | The HTTP method that the monitor uses for requests.                                |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| url_path         | plain     | xsd:string  | The HTTP path of the request sent by the monitor to test the health of a member.   |
|                  |           |             | A valid value is a string that begins with a forward slash (/).                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| expected_codes   | plain     | xsd:string  | The list of HTTP status codes expected in response from the member to declare it   |
| (optional)       |           |             | healthy. Specify one of the following values:                                      |
|                  |           |             |                                                                                    |
|                  |           |             | - A single value, such as 200.                                                     |
|                  |           |             | - A list, such as 200, 202.                                                        |
|                  |           |             | - A range, such as 200-204.                                                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the health monitor, which is up (true) or down (false).|
| (optional)       |           |             | Set this attribute to false to create the listener in an administratively down     |
|                  |           |             | state.                                                                             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


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

**Example. Update health monitor: JSON response**

This table shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| healthmonitor    | plain     | xsd:dict    | A healthmonitor object.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID for the health monitor.                                                   |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the healthmonitor. Only administrative users can   |
|                  |           |             | specify a tenant UUID other than their own.                                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| type             | plain     | xsd:string  | The type of probe sent by the load balancer to verify the member state.            |
|                  |           |             | A valid value is PING, TCP, HTTP, or HTTPS.                                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| delay            | plain     | xsd:int     | The time, in seconds, between sending probes to members.                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| timeout          | plain     | xsd:int     | The maximum number of seconds for a monitor to wait for a connection to be         |
|                  |           |             | established before it times out. This value must be less than the delay value.     |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| max_retries      | plain     | xsd:int     | The number of allowed connection failures before changing the status of the member |
|                  |           |             | to INACTIVE. A valid value is from 1 to 10.                                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| http_method      | plain     | xsd:string  | The HTTP method that the monitor uses for requests.                                |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| url_path         | plain     | xsd:string  | The HTTP path of the request sent by the monitor to test the health of a member.   |
| (optional)       |           |             | A valid value is a string that begins with a forward slash (/).                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| expected_codes   | plain     | xsd:string  | The list of HTTP status codes expected in response from the member to declare it   |
| (optional)       |           |             | healthy. Specify one of the following values:                                      |
|                  |           |             |                                                                                    |
|                  |           |             | - A single value, such as 200.                                                     |
|                  |           |             | - A list, such as 200, 202.                                                        |
|                  |           |             | - A range, such as 200-204.                                                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the health monitor, which is up (true) or down (false).|
| (optional)       |           |             | Set this attribute to false to create the listener in an administratively down     |
|                  |           |             | state.                                                                             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| status           | plain     | xsd:string  | The status of the health monitor, which indicates whether the health monitor is    |
|                  |           |             | operational.                                                                       |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


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
