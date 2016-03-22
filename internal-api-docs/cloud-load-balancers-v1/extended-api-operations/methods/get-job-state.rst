.. _get-job-state:

Retrieve a list of jobs by state
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/jobs?state=SomeState 


This operation retrieves a list of jobs by state.



The access levels for this operation is ``operations``. 





Response
""""""""""""""""

**Example: List job by state XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <job xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0" id="4" jobName="HOST_ENDPOINT_POLLER"
         state="FINISHED" startTime="2011-07-25T12:28:01-05:00" endTime="2011-07-25T12:28:13-05:00"/>

                    


**Example: List job by state JSON response**

.. code::  

    {
        "id":4,
        "state":"FINISHED",
        "startTime":"2011-07-25T12:28:01-05:00",
        "endTime":"2011-07-25T12:28:13-05:00",
        "jobName":"HOST_ENDPOINT_POLLER"
    }
