.. _using-cloud-load-balancers:

Create and manage load balancers
----------------------------------------

Use the examples in the following sections to create and manage load balancers
<<<<<<< HEAD
by using API operations. Before running the examples, review the
:ref:`load balancers concepts <concepts>` to understand the API workflow,
messaging patterns, and use cases.
=======
by using Cloud Load Balancers API operations. Before running the examples,
review the :ref:`Cloud Load Balancers concepts<concepts>` to understand the
API workflow, messaging patterns, and use cases.
>>>>>>> 660213457e71f50ec817f8678b4bfc452a5a0aa5

.. contents::
   :local:
   :depth: 1

.. note::
     These examples use the ``$API_ENDPOINT``, ``$AUTH_TOKEN``, and ``$TENANT_ID`` environment
     variables to specify the API endpoint, authentication token, and project ID values
     for accessing the service. Make sure you
     :ref:`configure these variables<configure-environment-variables>` before running the
     code samples.


.. include:: ../examples/create-cloud-servers-to-lb.rst
.. include:: ../examples/create-load-balancer.rst
.. include:: ../examples/list-load-balancer-details.rst
.. include:: ../examples/add-node.rst
.. include:: ../examples/update-load-balancer-attributes.rst
