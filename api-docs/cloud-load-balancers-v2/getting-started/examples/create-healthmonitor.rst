.. _create-healthmonitor:

=========================
Creating a health monitor
=========================

A health monitor determines whether a member of a pool is usable for processing
a request.

Assume that you want to create a health monitor (``POST /healthmonitors``) with
the following configuration:

-  ``admin_state_up`` is ``true``.

-  ``delay`` is ``1``.

-  ``expected_codes`` is ``200, 201, 201``.

-  ``http_method`` is ``GET``.

-  ``max_retries`` is ``5``.

-  ``pool_id`` is the ID of the pool member that you added (see
   :ref:`Add member to pool <add-pool-member>`).
   Remember to replace ``pool_id`` in the example with the actual value that
   was returned in the response.

-  ``timeout`` is ``1``.

-  ``type`` is ``HTTP``.

-  ``url_path`` is ``/index/html``.

The following example shows the cURL request for creating a health monitor.

**Example: cURL command for creating a health monitor with a JSON body**

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

The following example shows the response for creating a  health monitor.

**Example: Create a health monitor response in JSON**

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

Congratulations! You have completed the basic actions for load balancing your
configuration.
