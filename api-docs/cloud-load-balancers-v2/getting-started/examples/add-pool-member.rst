.. _add-pool-member:

Adding a member to the pool
~~~~~~~~~~~~~~~~~~~~~~~~~~~

When a member is added to a pool (``POST /pools/pool_id/members``), the member
is assigned a unique identifier that you can use for management operations,
such as changing the ``admin_state`` or removing the member.

Assume that you to want to configure the member with the following
configuration:

-  ``address`` is the IP address of the cloud server that you created and
   decided to use at the beginning of this guide. Remember to replace the
   placeholder in the example with the actual IP address of the service.

-  ``admin_state_up`` is ``true``.

-  ``protocol_port`` is ``80``.

-  ``subnet_id`` is the UUID of the subnet on which the member resides. This
   parameter is the ID of a subnet returned from querying neutron’s
   subnets by using the endpoint
   ``https://iad.networks.api.rackspacecloud.com/v2.0/subnets?shared=True``.
   Replace ``subnet_id`` in the example with the actual value.

-  ``weight`` is ``1``. This parameter is a positive integer value that
   indicates the relative portion of traffic that this member should receive
   from the pool. For example, a member with a weight of 10 receives five times
   as much traffic as a member with a weight of 2.

The following example shows the cURL request for adding a member to a pool.

**Example: cURL command for adding a member to a pool with a JSON body**

.. code::

   curl -s -d \
      '{
         "member": [
           {
               "address": "<IP address of Cloud Server>",
               "admin_state_up": true,
               "protocol_port": 80,
               "subnet_id": "00000000-0000-0000-0000-000000000000",
               "weight": 1
           }
       ]
   }' \
   -H "X-Auth-Token: $AUTH_TOKEN" \
   -H "Content-Type: application/json" \
   -X POST \
   "$API_ENDPOINT/pools/pool_id/members" | python -m json.tool

The following example shows the response returned when you add a member to a
pool.

**Example: Add a member to a pool response in JSON**

.. code::

    {
       "member": {
            "address": "10.0.0.8",
            "admin_state_up": true,
            "id": "9a7aff27-fd41-4ec1-ba4c-3eb92c629313",
            "protocol_port": 80,
            "subnet_id": "00000000-0000-0000-0000-000000000000",
            "tenant_id": "tenant_id",
            "weight": 1
        }
    }

You need the ID (in this example, ``9a7aff27-fd41-4ec1-ba4c-3eb92c629313``) to
:ref:`create a health monitor <create-healthmonitor>`.
