.. _get—user-events-with-range:

Retrieve recent load balancer service events for a user
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/event/user/{username}?startDate=YYYY-MM-DD&endDate=YYYY-MM-DD


This operation retrieves recent load balancer service events for the specified user and date range.

The ``startDate`` and ``endDate`` parameters are optional. The results list all load 
balancer service events that occurred between the start and end dates for the 
specified account or a specified user or author. By default, the start date is 60 
days from the time of the request and the end date is the date of the request. The 
results list is inclusive for both dates. 

The access levels for this operation are ``support`` and  ``service admin``. 



Response
""""""""""""""""


**Example: List user events XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <loadBalancerServiceEvents xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <loadBalancerServiceEvent
                id="46" loadbalancerId="10" accountId="123456" author="username"
                title="Load Balancer Successfully Created"
                description="Load balancer successfully created with name: 'a-new-new-loadbalancer', algorithm: 'RANDOM', protocol: 'HTTP', port: '80'"
                type="CREATE_LOADBALANCER" category="CREATE" severity="INFO"
                relativeUri="/123456/loadbalancers/10" created="11-20-2010 12:03:42"/>
    </loadBalancerServiceEvents>

                    


**Example: List user events JSON response**

.. code::  

    {
        "loadBalancerServiceEvents":[{
                "id":46,
                "type":"CREATE_LOADBALANCER",
                "description":"Load balancer successfully created with name: 'a-new-new-loadbalancer', algorithm: 'RANDOM', protocol: 'HTTP', port: '80'",
                "category":"CREATE",
                "relativeUri":"/123456/loadbalancers/10",
                "severity":"INFO",
                "accountId":123456,
                "loadbalancerId":10,
                "author":"username",
                "created":"11-20-2010 12:03:42",
                "title":"Load Balancer Successfully Created"
            }
        ]
    }
