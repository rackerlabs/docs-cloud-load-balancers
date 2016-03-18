.. _customer-lists:

=====================
Customer lists 
=====================


The generated customer list allows external services to query the load balancing 
service to determine which customers are associated with either a cluster or a host. 
If the external service has access to customer contact information, this can make it 
possible to automate the process of identifying and contacting customers affected by 
an environmental change.

.. include:: methods/post-host-customer-list.rst
.. include:: methods/post-cluster-customer-list.rst
.. include:: methods/get-cluster-customer-list.rst
.. include:: methods/get-host-customer-list.rst
