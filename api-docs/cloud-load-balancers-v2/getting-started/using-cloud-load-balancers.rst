.. _using-cloud-load-balancers:

Create and manage Cloud Load Balancers
----------------------------------------

You can use the examples in this section to create and manage load balancers 
by using Cloud Load Balancers API operations. Before running the examples, 
review the :ref:`Cloud Load Balancers concepts<concepts>` to understand the 
API workflow, messaging patterns, and use cases.  

.. note:: 
     These examples use the ``$API_ENDPOINT`` and ``$AUTH_TOKEN`` environment 
     variables to specify the API endpoint and authentication token  
     for accessing the service. Be sure to 
     :ref:`configure these variables<configure-environment-variables>` before running the 
     code samples. 


.. include:: examples/create-cloud-servers-to-lb.rst
.. include:: examples/create-load-balancer.rst
.. include:: examples/get-lb-details.rst
.. include:: examples/create-listener.rst
.. include:: examples/create-pool.rst
.. include:: examples/add-pool-member.rst
.. include:: examples/create-healthmonitor.rst



