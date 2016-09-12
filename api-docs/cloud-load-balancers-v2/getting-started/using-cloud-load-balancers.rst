.. _using-cloud-load-balancers:

======================================
Create and manage Cloud Load Balancers
======================================

You can use the examples in the following sections to create and manage load
balancers by using Cloud Load Balancers API operations.

.. contents::
   :local:
   :depth: 1


Before running the examples, review the :ref:`Cloud Load Balancers
concepts<concepts>` to understand the API workflow, messaging patterns, and use
cases.

.. note::
     These examples use the ``$API_ENDPOINT``, ``$AUTH_TOKEN``, and
     ``$TENANT_ID`` environment variables to specify the API endpoint,
     authentication token, and project ID values for accessing the service.
     Make sure you :ref:`configure these
     variables<configure-environment-variables>` before running the code
     samples.

.. include:: examples/create-cloud-servers-to-lb.rst
.. include:: examples/create-load-balancer.rst
.. include:: examples/get-lb-details.rst
.. include:: examples/create-listener.rst
.. include:: examples/create-pool.rst
.. include:: examples/add-pool-member.rst
.. include:: examples/create-healthmonitor.rst
