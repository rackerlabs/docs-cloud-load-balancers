.. _post-lb-ticket:

Add a ticket for a load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/loadbalancers/{loadBalancerId}/tickets  


This operation add a ticket for the specified load balancer.


The access levels for this operation are ``support`` and  ``service admin``. 




Response
""""""""""""""""

**Example: Create ticket for load balancer XML request**

.. code::  

    <ticket xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
        ticketId="1234"
        comment="My first ticket :)" />

                    


**Example: Create ticket for load balancer JSON request**

.. code::  

    {
        "ticketId": 1234,
        "comment": "My first ticket :)"
    }

