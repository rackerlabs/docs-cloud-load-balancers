.. _get-show-health-monitor-details-v2:

Show health monitor details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/healthmonitors/{healthmonitor_id}


This operation returns a health monitor object identified by
``healthmonitor_id``. If the user is not an administrative user and the
health monitor object does not belong to her tenant account, the service
returns the HTTP ``Forbidden (403)`` response code.

If this operation succeeds, it returns a health monitor element that can
contain the following attributes:

-  ``id``

-  ``tenant_id``

-  ``type``

-  ``delay``

-  ``timeout``

-  ``max_retries``

-  ``http_method``

-  ``url_path``

-  ``expected_codes``

-  ``admin_state_up``

-  ``pool_id``

-  ``pools``

Example: Show health monitor details

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

**Example. Show health monitor details: JSON response**

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
