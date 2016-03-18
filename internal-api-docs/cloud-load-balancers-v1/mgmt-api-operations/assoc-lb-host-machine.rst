.. _assoc-lb-host-machine:

===============================================================
Associations between load balancers and host machines 
===============================================================

Service administrators may re-assign a load balancer to a different host machine within the same cluster. This action can be taken if capacity warrants it or if a particular configuration needs to be isolated from others within the environment. Both active and failover hosts may be changed.

Additionally, this operation allows for a service administrator to define a load balancer's host configurations as being "sticky" that prohibits the system from automatically moving this configuration between hosts to balance the host performance.

A load balancer that is defined as being ``ACTIVE`` on multiple hosts allows the load balancer host machines to service traffic for a single VIP across multiple systems. This is an advanced feature that should be used cautiously as it can potentially amplify DDoS and other types of malicious traffic. 



.. include:: methods/put-sticky-lb.rst
.. include:: methods/delete-sticky-lb.rst
.. include:: methods/get-host-assignments.rst
.. include:: methods/put-update-host-assignments.rst

