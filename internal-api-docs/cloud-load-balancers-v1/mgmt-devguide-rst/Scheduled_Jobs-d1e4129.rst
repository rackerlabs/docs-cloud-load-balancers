========================================================================================================
3.16. Scheduled Jobs - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
========================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.16. Scheduled Jobs
   :name: scheduled-jobs
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/jobs
Retrieve a list of jobss.
Operations
**GET**
/management/jobs?state=``SomeState``
Retrieve jobs by state.
Operations
**GET**
/management/jobs/``JobId``
Delete a specific job.
Operations, Support
Monitor usage poller to ensure it is working properly; alerts should be
produced when it is not working properly. All scheduled jobs need to be
monitored.

`  <>`__
**Example 3.44. List Jobs Response: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <jobs xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <job id="3" jobName="LB_USAGE_POLLER" state="FINISHED" startTime="2011-07-25T12:28:01-05:00"
             endTime="2011-07-25T12:28:14-05:00"/>
        <job id="4" jobName="HOST_ENDPOINT_POLLER" state="FINISHED" startTime="2011-07-25T12:28:01-05:00"
             endTime="2011-07-25T12:28:13-05:00"/>
    </jobs>

                    

`  <>`__
**Example 3.45. List Jobs Response: JSON**

.. code::  

    {
        "jobs":[{
                "id":3,
                "state":"FINISHED",
                "startTime":"2011-07-25T12:28:01-05:00",
                "endTime":"2011-07-25T12:28:14-05:00",
                "jobName":"LB_USAGE_POLLER"
            },
            {
                "id":4,
                "state":"FINISHED",
                "startTime":"2011-07-25T12:28:01-05:00",
                "endTime":"2011-07-25T12:28:13-05:00",
                "jobName":"HOST_ENDPOINT_POLLER"
            }
        ]
    }

                    

`  <>`__
**Example 3.46. List Job Response: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <job xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0" id="4" jobName="HOST_ENDPOINT_POLLER"
         state="FINISHED" startTime="2011-07-25T12:28:01-05:00" endTime="2011-07-25T12:28:13-05:00"/>

                    

`  <>`__
**Example 3.47. List Job Response: JSON**

.. code::  

    {
        "id":4,
        "state":"FINISHED",
        "startTime":"2011-07-25T12:28:01-05:00",
        "endTime":"2011-07-25T12:28:13-05:00",
        "jobName":"HOST_ENDPOINT_POLLER"
    }

                    
