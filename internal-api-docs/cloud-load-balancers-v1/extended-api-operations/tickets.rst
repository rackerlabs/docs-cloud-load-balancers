.. _tickets:

==============================================
Load balancer tickets
==============================================

Support tickets can be associated with load balancers so that Support can keep track of tickets over the lifetime of a load balancer. While a ticket can be identified here, there is no verification that the ticket actually exists in Support's system. 


..  note:: 

    Tickets can also be added through calls to suspend a load
    balancer, add a new virtual IP, or impose a rate limit. Support requires
    tickets for these operations.

.. include:: methods/get-all-lb-tickets.rst
.. include:: methods/post-lb-ticket.rst
