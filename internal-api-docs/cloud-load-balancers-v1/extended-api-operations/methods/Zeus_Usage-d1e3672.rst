====================================================================================================
3.11. Zeus Usage - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
====================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.11. Zeus Usage
   :name: zeus-usage
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/hosts/usage?startDate=2011-05-01T00:00:00&endDate=2011-05-31T00:00:00
View usage of Zeus hosts.
Support, Service Admin
The ``startDate`` and ``endDate`` parameters are required for this call.
The resulting list displays all usage occurring between the starting and
ending dates provided, up to 31 days apart.

`  <>`__
**Example 3.31. List Zeus Usage Response: XML**

.. code::  

    <hostUsageList xmlns="http://docs.rackspacecloud.com/loadbalancers/api/management/v1.0">
        <hostUsageRecords>
            <hostUsageRecord hostId="1">
                <hostUsages>
                    <hostUsage bandwidthIn="0" bandwidthOut="0" day="2011-02-01Z"/>
                </hostUsages>
            </hostUsageRecord>
        </hostUsageRecords>
    </hostUsageList>

                    

`  <>`__
**Example 3.32. List Zeus Usage Response: JSON**

.. code::  

    {"hostUsageRecords": [
            {
                "hostId": 1,
                "hostUsages": [
                    {
                        "day": "2011-02-14T00:00:00-0600",
                        "bandwidthIn": 0,
                        "bandwidthOut": 0
                    }
                ]
            }
        ]
    }

                    
