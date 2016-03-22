.. _get-jobs:

Retrieve a list of jobs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/jobs  


This operation retrieves a list of scheduled jobs.



The access levels for this operation is ``operations``. 





Response
""""""""""""""""

**Example: List jobs XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <jobs xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <job id="3" jobName="LB_USAGE_POLLER" state="FINISHED" startTime="2011-07-25T12:28:01-05:00"
             endTime="2011-07-25T12:28:14-05:00"/>
        <job id="4" jobName="HOST_ENDPOINT_POLLER" state="FINISHED" startTime="2011-07-25T12:28:01-05:00"
             endTime="2011-07-25T12:28:13-05:00"/>
    </jobs>

                    

**Example: List jobs JSON response**

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
