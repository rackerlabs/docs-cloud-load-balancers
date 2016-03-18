.. _get-health-checks:

Retrieve health checks
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/healthcheck


This operation returns the status of zeus, database, and localized server.


The access levels for this operation are ``support`` and ``service admin``. 

This operations gives you a simple object that shows the health status of Zeus, the 
database, and the local machine where glassfish is running. It also returns the time 
it took for each check.

If the database is inaccessible, it is impossible to determine the health of 
Zeus. The call to reach Zeus system information through the API requires information 
stored in the database, so the status of Zeus will read ``UKNOWN``, and its message 
will read ``Database inactive, unable to determine status of zeus``. 


Response
""""""""""""""""


**Example: Health check XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <healthChecks xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <healthCheck type="ZEUS" status="ACTIVE" time="835"/>
        <healthCheck type="DATABASE" status="ACTIVE" time="72"/>
        <healthCheck type="LOCAL" status="ACTIVE" time="0"/>
    </healthChecks>
                    





**Example: Health check JSON response**

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


                    
