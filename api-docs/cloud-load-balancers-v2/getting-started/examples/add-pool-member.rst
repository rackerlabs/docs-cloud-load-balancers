.. _add-pool-member:

=====================
Add a member to pool
=====================

When a member is added to a pool, the member is assigned a unique identifier that you can use for management operations, such as changing the ``admin_state`` or removing the member.

For the member, enter the IP address that you recorded for your Cloud Server in :ref:`Creating a Cloud Server <create-cloud-servers>`. 

Assume that you to want to configure the member with the following configuration:  

-  ``address`` is the IP address of the first Cloud Server that you created and recorded at the beginning of this Getting Started Guide. Remember to replace the placeholder in the example with the actual value.

-  ``admin_state_up`` is ``true``.

-  ``protocol_port`` is ``80``. 

-  ``subnet_id`` is the UUID of the subnet in which to access this member. The UUID is determined 
   by what subnet the member is on and is the ID of the subnet returned from querying Neutron’s 
   subnets using the following endpoint: ``neutron.endpoint/v2.0/subnets?shared=True``.

   **Reviewer: Please specify the specific neutron.endpoint mentioned in the previous sentence.**

-  ``weight`` is ``1``. The ``weight`` parameter is a positive integer value that indicates the relative 
   portion of traffic that this member should receive from the pool. For example, a member with a weight 
   of 10 receives five times as much traffic as a member with a weight of 2.

The following example shows the cURL request for adding a member to a pool:

**Example. cURL add member to pool request: JSON**

.. code::  

   curl -s -d \
      '{
         "member": [
           {
               "address": "<IP address of Cloud Server>",
               "admin_state_up": true,
               "protocol_port": 80,
               "subnet_id": "subnet_id",
               "weight": 1
           }
       ]
   }' \
   -H "X-Auth-Token: $AUTH_TOKEN" \
   -H "Content-Type: application/json" \
   -X POST \
   "$API_ENDPOINT/pools/pool_id/members" | python -m json.tool


The following example shows the response returned when you add a member to a pool:

**Example. Add member to pool response: JSON**

.. code::  

    {
       "member": {
            "address": "10.0.0.8",
            "admin_state_up": true,
            "id": "9a7aff27-fd41-4ec1-ba4c-3eb92c629313",
            "protocol_port": 80,
            "subnet_id": "subnet_id",
            "tenant_id": "tenant_id",
            "weight": 1
        }
    }


In this example, you can see that a new member with ID ``9a7aff27-fd41-4ec1-ba4c-3eb92c629313`` has been added to the pool. You will need the pool ID for making the :ref:`Create a health monitor <create-health-monitor>` call, and you should supply this value wherever you see the ``pool_id`` in the examples in this guide.

