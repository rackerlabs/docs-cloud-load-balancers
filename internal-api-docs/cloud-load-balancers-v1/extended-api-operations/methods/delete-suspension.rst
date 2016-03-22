.. _delete-suspension:

Remove suspension for a load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   DELETE /management/loadbalancers/l{oadBalancerId}/suspension


This operation removes the suspension for the specified load balancer.

The access levels for this operation are ``support`` and ``service admin``. 

..  note:
  
     While customers are not permitted to delete suspended load balancers, a user 
     with elevated permissions may do so by issuing a **DELETE** request against 
     the ``/loadbalancers/loadBalancerId`` URI. 

