.. _get-list-health-monitors-v2:

List health monitors
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/healthmonitors


This operation lists all health monitors associated with your tenant
account.


The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | The request succeeded.                      |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.      |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

This operation does not accept a request body.

Response
""""""""""""""""



The following table shows the body parameters for the response.

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| healthmonitor    | plain     | xsd:dict    | A health monitor object.                                                           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the health monitor, which is up (``true``) or down     |
|                  |           |             | (``false``). Set this attribute to ``false`` to create the listener in an a        |
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
| max_retries      | plain     | xsd:int     | The number of allowed connection failures that are allowed before the status of the|
|                  |           |             | member is changed to INACTIVE. Valid value are from 1 to 10.                       |
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
|                  |           |             | Valid values are ``PING``, ``TCP``, ``HTTP``, or ``HTTPS.``                        |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| url_path         | plain     | xsd:string  | The HTTP path of the request sent by the monitor to test the health of a member.   |
|                  |           |             | A valid value is a string that begins with a forward slash (/).                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: List health monitors JSON response**

.. code::

    {
        "healthmonitors": [
            {
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
        ]
    }
