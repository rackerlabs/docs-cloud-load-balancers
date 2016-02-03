.. _create-health-monitor-v2:

Create health monitor
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/healthmonitors


This operation provisions a new health monitor based on the
configuration defined in the request object. After the request is
validated and progress has started on the provisioning process, a
response object is returned. The object contains a unique identifier.

The caller of this operation must specify these health monitor
attributes, at a minimum:

-  ``tenant_id``. Only required if the caller has an administrative role
   and wants to create a health monitor for another tenant.

-  ``type``. The type of health monitor. Must be one of TCP, HTTP, HTTPS

-  ``delay``. The interval in seconds between health checks.

-  ``timeout``. The time in seconds that a health check times out.

-  ``max_retries``. Number of failed health checks before marked as
   OFFLINE.

-  ``pool_id``. The pool that this health monitor will monitor.

Some attributes receive default values if you omit them from the
request, and are only useful when you specify a health monitor type of
HTTP(S):

-  ``http_method``. Default is GET.

-  ``url_path``. Default is ``/``.

-  ``expected_codes``. The expected http status codes to get from a
   successful health check. Default is 200.

-  ``admin_state_up``. Default is true.

If the request cannot be fulfilled due to insufficient data or data that
is not valid, an HTTP 400 (Bad Request) error response is returned with
information regarding the nature of the failure in the response body.
Failures in the validation process are non-recoverable and require the
caller to correct the cause of the failure and **POST** the request
again.

You can configure all documented features of the health monitor at
creation time by specifying the additional elements or attributes in the
request.

Users with an administrative role can create health monitors on behalf
of other tenants by specifying a ``tenant_id`` attribute different than
their own.

To update a health monitor, the load balancer to which it is being
attached must have an ACTIVE provisioning status.

Example: Create a health monitor

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 201     | Created               | The request has been fulfilled and resulted |
|         |                       | in a new resource being created.            |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
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

**Example. Create health monitor: JSON request**

This table shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
+==================+===========+=============+====================================================================================+
| healthmonitor    | plain     | xsd:dict    | A healthmonitor object.                                                            |
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
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
| (optional)       |           |             | Set this attribute to false to create the listener in an administratively down     |
|                  |           |             | state.                                                                             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+



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

**Example. Create health monitor: JSON response**

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
