========================================================================================================
3.9. Absolute Limits - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
========================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.9. Absolute Limits
   :name: absolute-limits
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/accounts/``accountId``/loadbalancers/absolutelimits
Retrieve all absolute limits, ids included with custom limits.
Support, Service Admin
**POST**
/management/accounts/``accountId``/loadbalancers/absolutelimits
Add an absolute limit.
Support, Service Admin
**DELETE**
/management/accounts/``accountId``/loadbalancers/absolutelimits/``id``
Delete the specific absolute limit.
Support, Service Admin
**PUT**
/management/accounts/``accountId``/loadbalancers/absolutelimits/``id``
Update an absolute limit.
Support, Service Admin
Absolute limits encapsulates other LoadBalancer API limits that the
system provides into one manageable entity.

The values for the absolute limits are shown below:

Name
Description
Default Limit
Absolute Limit
LOADBALANCER\_LIMIT
Total number of load balancers that can be added to a Cloud account.
25
50
NODE\_LIMIT
Total number of nodes that can be added to a load balancer.
25
50
IPV6\_LIMIT
Total number of IPV6 addresses that can be added to a load balancer.
25
50
BATCH\_DELETE\_LIMIT
Total number of resources that can be listed per batch delete request.
10
10
ACCESS\_LIST\_LIMIT
Total number of network items that can be added to a load balancer.
100
contact Operations
To get the id for a custom absolute limit, the call with url
/management/clusters/``clusterId``/customlimitaccounts returns a
response body with account numbers and an id associated with the
non-default limits.

POST, PUT, and DELETE operations do not provide response bodies.

`  <>`__
**Example 3.21. Get Limits Response: XML**

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

                    

`  <>`__
**Example 3.22. Get Limits Response: JSON**

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

                    

`  <>`__
**Example 3.23. Add Limits Request: XML**

.. code::  

    <limit xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" name="LOADBALANCER_LIMIT" value="333"/>

                    

`  <>`__
**Example 3.24. Add Limits Request: JSON**

.. code::  

    {
        "name":"LOADBALANCER_LIMIT","value":101111
    }

                    

`  <>`__
**Example 3.25. Update Limits Request: XML**

.. code::  

    <limit xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" value="100"/>

                    

`  <>`__
**Example 3.26. Update Limits Request: JSON**

.. code::  

    {
         "value":101111
    }

                    
