=====================================================================================================
2.9. Health Check - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
=====================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.9. Health Check
   :name: health-check
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/healthcheck
Returns status of zeus, database, and localized server
Support, Service Admin
This call will give you a simple object that will show the health status
of Zeus, the database, and the local machine where glassfish is running.
Also returns the time it took for each check.

If the database is inaccessible, it will be impossible to determine the
health of Zeus. The call to reach Zeus system information through the
API requires information stored in the database, so the status of Zeus
will read "UKNOWN", and its message will read "Database inactive, unable
to determine status of zeus."

`  <>`__
**Example 2.46. Health Check: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <healthChecks xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <healthCheck type="ZEUS" status="ACTIVE" time="835"/>
        <healthCheck type="DATABASE" status="ACTIVE" time="72"/>
        <healthCheck type="LOCAL" status="ACTIVE" time="0"/>
    </healthChecks>

                    

`  <>`__
**Example 2.47. Health Check: JSON**

.. code::  

    {
        "healthChecks":[{
                "type":"ZEUS",
                "time":4328,
                "status":"ACTIVE"
            },
            {
                "type":"DATABASE",
                "time":89,
                "status":"ACTIVE"
            },
            {
                "type":"LOCAL",
                "time":0,
                "status":"ACTIVE"
            }
        ]
    }

                    
