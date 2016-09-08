.. _service-access:

============================
Service access and endpoints
============================

The Load Balancers service is a regionalized service. It allows the user to
select a region into which a load balancer is to be provisioned.

To determine which region to operate against, select an endpoint from
the following table.

.. tip::
   To help you decide which regionalized endpoint to use, read about
   :how-to:`special considerations for choosing a region <about-regions>`.

.. _clb-dg-api-info-service-access-regional:

Regionalized service endpoints
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------------------------+-------------------------------------------------------------+
| Region                  | Endpoint                                                    |
+=========================+=============================================================+
| Northern Virginia (IAD) | https://iad.networks.api.rackspacecloud.com/v2.0/lbaas/     |
+-------------------------+-------------------------------------------------------------+

..  note::
    The service catalog returned in the authentication response specifies the
    correct service access endpoint for your account to use for accessing Cloud
    Load Balancers. Use the service ``type`` (``rax:load-balancer-v2``) to
    locate the correct endpoint in the service catalog.


When making a Cloud Load Balancers API call, place the endpoint at the
beginning of the request URL. For example, the URL to use to
:ref:`create a load balancer<create-load-balancers-v2>` is 
``https://iad.networks.api.rackspacecloud.com/v2.0/lbaas/``\ ``loadbalancers``.
Note that the ``v2.0`` component in the URL indicates that you are using
version 2.0 of the Cloud Load Balancers API.
