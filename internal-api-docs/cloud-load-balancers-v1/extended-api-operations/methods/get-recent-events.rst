.. _get-recent-events:

Retrieve recent load balancer service events
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/event/account/{accountId}/loadbalancer?startDate=YYYY-MM-DD&endDate=YYYY-MM-DD


This operation retrieves recent load balancer service events for the specified account and date range.

The ``startDate`` and ``endDate`` parameters are optional. The results list all load 
balancer service events that occurred between the start and end dates for the 
specified account or a specified user or author. By default, the start date is 60 
days from the time of the request and the end date is the date of the request. The 
results list is inclusive for both dates. 

The access levels for this operation are ``support`` and  ``service admin``. 



Response
""""""""""""""""


**Example: List account events XML response**

.. code::  

    <accountLoadBalancerServiceEvents xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" accountId="546428">
        <loadBalancerServiceEvents loadbalancerId="8">
            <loadBalancerServiceEvent
                    author="abc"
                    description="LoadBalancer successfully created"
                    category="CREATE"
                    severity="INFO"
                    created="01/06/2011 10:37" />
        </loadBalancerServiceEvents>
    </accountLoadBalancerServiceEvents>
