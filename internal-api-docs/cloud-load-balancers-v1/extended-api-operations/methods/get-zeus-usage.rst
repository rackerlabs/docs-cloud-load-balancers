.. _get-zeus-usage:

View usage of Zeus hosts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/hosts/usage?startDate=2011-05-01T00:00:00&endDate=2011-05-31T00:00:00


This operation retrieves information about the usage of Zeus hosts.


The ``startDate`` and ``endDate`` parameters are required for this call. The resulting list displays all usage occurring between the starting and ending dates provided, up to 31 days apart. 


The access levels for this operation are ``support`` and  ``service admin``. 





Response
""""""""""""""""

**Example: List Zeus usage XML response: XML**

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

                    

**Example: List Zeus usage JSON response**

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
