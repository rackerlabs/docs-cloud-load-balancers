===============================================================================================================
3.10. Load Balancer Tickets - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
===============================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.10. Load Balancer Tickets
   :name: load-balancer-tickets
   :class: title

Verb
URI
Description
Access Level
Optional Query Parameters
GET
/management/loadbalancers/``loadBalancerId``/tickets
List all tickets for the load balancer.
Support, Service Admin
offset, limit
POST
/management/loadbalancers/``loadBalancerId``/tickets
Add a ticket to the load balancer.
Support, Service Admin
Support tickets can be associated with load balancers so that Support
can keep track of tickets over the lifetime of a load balancer. While a
ticket can be identified here, there is no verification that the ticket
actually exists in Support's system.

..  note:: 
Note
Note: Tickets can also be added through calls to suspend a load
balancer, add a new virtual IP, or impose a rate limit. Support requires
tickets for these operations.

`  <>`__
**Example 3.27. List Tickets for Load Balancer Response: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <tickets xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <ticket id="1" ticketId="1234" comment="My first ticket :)"/>
        <ticket id="2" ticketId="4321" comment="My last ticket :("/>
    </tickets>

                    

`  <>`__
**Example 3.28. List Tickets for Load Balancer Response: JSON**

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

                    

`  <>`__
**Example 3.29. Create Ticket for Load Balancer Request: XML**

.. code::  

    <ticket xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
        ticketId="1234"
        comment="My first ticket :)" />

                    

`  <>`__
**Example 3.30. Create Ticket for Load Balancer Request: JSON**

.. code::  

    {
        "ticketId": 1234,
        "comment": "My first ticket :)"
    }

                    
