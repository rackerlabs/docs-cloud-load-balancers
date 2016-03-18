.. _virtual-IPs:

=====================
Virtual IPs 
=====================


The virtual IP operations allow the caller to view, create, and remove 
virtual IPs from an environment. Virtual IPs are automatically assigned 
to every newly created load balancer and can be added on-demand by a 
support or service administrator with proper justification. Management 
of the service requires blocks of IP addresses to be allocated from 
time-to-time to ensure availability for customers.



.. include:: methods/get-cluster-vips.rst
.. include:: methods/get-region-vips.rst
.. include:: methods/get-lb-vips.rst
.. include:: methods/get-traffic-ports.rst
.. include:: methods/post-cluster-ipblocks.rst
.. include:: methods/delete-cluster-vip.rst