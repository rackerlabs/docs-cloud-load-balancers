.. _post-suspension:

Issue a service suspension
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/loadbalancers/{loadBalancerId}/suspension


This operation issues an immediate service suspension for the specified load balancer. 

In order to suspend a load balancer, you must supply a reason, the ticket issuer (user), and a ticket identifier, which can be viewed by other users with support and service admin access levels. 


The access levels for this operation are ``support`` and ``service admin``. 




Request
""""""""""""""""

**Example: Add suspension XML request**

.. code::  

    <suspension xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            reason="Non-payment"
            user="bob">
        <ticket ticketId="1234" comment="Late payment" />
    </suspension>

                    


**Example: Add suspension JSON request**

.. code::  

    {
        "reason": "Non-payment",
        "user": "bob",
        "ticket": {
            "ticketId": 1234,
            "comment": "Late Payment"
        }
    }
