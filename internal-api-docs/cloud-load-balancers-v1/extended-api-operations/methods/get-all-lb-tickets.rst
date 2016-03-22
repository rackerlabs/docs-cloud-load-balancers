.. _get-all-lb-tickets:

Retrieve all tickets for a load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/loadbalancers/{loadBalancerId}/tickets  


This operation retrieves all tickets for the specified load balancer.

The following parameters are optional:

-  ``offset``

-  ``limit``


The access levels for this operation are ``support`` and  ``service admin``. 




Response
""""""""""""""""

**Example: List tickets for load balancer XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <tickets xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <ticket id="1" ticketId="1234" comment="My first ticket :)"/>
        <ticket id="2" ticketId="4321" comment="My last ticket :("/>
    </tickets>

                    


**Example: List tickets for load balancer JSON response**

.. code::  

    {
        "tickets": [
            {
                "id": 1,
                "comment": "My first ticket :)",
                "ticketId": 1
            },
            {
                "id": 2,
                "comment": "My last ticket :(",
                "ticketId": 2
            }
        ]
    }
