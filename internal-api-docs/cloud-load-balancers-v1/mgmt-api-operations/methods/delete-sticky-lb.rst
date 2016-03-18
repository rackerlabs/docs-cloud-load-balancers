.. _delete-sticky-lb:

Turn off the sticky flag on a load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   DELETE /management/loadbalancers/{loadBalancerId}/sticky


This operation turns off the sticky flag on the load balancer specified by ``loadbalancerId``.

The access levels for this operation are ``support`` and ``service admin``. 
