.. _get-absolute-limits:

Retrieve all absolute limits
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/accounts/{accountId}/loadbalancers/absolutelimits


This operation retrieves all absolute limits for the specified account, including IDs 
with custom limits.

To get the ID for a custom absolute limit, the call with the ``/management/clusters/clusterId/customlimitaccounts`` returns a response body with account numbers and an ID associated with the non-default limits. 

The access levels for this operation are ``support`` and  ``service admin``. 



Response
""""""""""""""""


**Example: Get limits XML responseL**

.. code::  

    <allAbsoluteLimits xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
                       xmlns:ns2="http://docs.openstack.org/loadbalancers/api/v1.0">
        <customLimits>
            <limit id="1" name="LOADBALANCER_LIMIT" value="30"/>
        </customLimits>
        <defaultLimits>
            <limit name="ACCESS_LIST_LIMIT" value="100"/>
            <limit name="BATCH_DELETE_LIMIT" value="10"/>
            <limit name="IPV6_LIMIT" value="25"/>
            <limit name="NODE_LIMIT" value="25"/>
        </defaultLimits>
    </allAbsoluteLimits>

                    


**Example: Get limits JSON response**

.. code::  

    {"defaultLimits": [
            {
                "name": "ACCESS_LIST_LIMIT",
                "value": 100
            },
            {
                "name": "BATCH_DELETE_LIMIT",
                "value": 10
            },
            {
                "name": "IPV6_LIMIT",
                "value": 25
            },
            {
                "name": "NODE_LIMIT",
                "value": 25
            }
        ],
        "customLimits": [
            {
                "name": "LOADBALANCER_LIMIT",
                "value": 30,
                "id": 2
            }
        ]
    }



