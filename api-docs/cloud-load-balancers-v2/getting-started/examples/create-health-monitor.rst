.. _create-health-monitor:

=======================
Create a health monitor
=======================

Next you create a health monitor for your pool.

Assume that you want to create a health monitor with the
following configuration:

-  ``admin_state_up`` is ``true``.

-  ``delay`` is ``1``.

-  ``expected_codes`` are ``200, 201, 201``.

-  ``http_method`` is ``GET``.

-  ``max_retries`` is ``5``.

-  ``pool_id`` is ``your_pool_id``. For your pool ID, see :ref:`Add member to pool <add-pool-member>`.

-  ``timeout`` is ``1``.

-  ``type`` is ``HTTP``.

-  ``url_path`` is ``/index/html``.
   

The following example shows the cURL request for create health monitor:

**Example. cURL create health monitor request: JSON**

.. code::  

   curl -s -d \
      '{
          "healthmonitor": {
              "admin_state_up": true,
              "delay": "1",
              "expected_codes": "200,201,202",
              "http_method": "GET",
              "max_retries": 5,
              "pool_id": “your_pool_id",
              "timeout": 1,
              "type": "HTTP",
              "url_path": "/index.html"
          }
   }' \
   -H "X-Auth-Token: $AUTH_TOKEN" \
   -H '"Content-Type: application/json" \
   -X POST \
   "$API_ENDPOINT/healthmonitors/" | python -m json.tool




The following example shows the response for create health monitor:

**Example. Create health monitor response: JSON**

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

Congratulations! You now have a health monitor for your load balancer configuration.
