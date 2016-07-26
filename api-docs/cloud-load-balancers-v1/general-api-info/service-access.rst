.. _service-access:

========================
Service access endpoints
========================

.. COMMENT: Adapt this topic to provide information that is relevant for
   your product.

The |apiservice| service is a regionalized service. It allows the caller to
select the region into which a load balancer is provisioned.

The following table lists the |product name| endpoints that are available
for each region.

.. tip::
   To help you decide which regionalized endpoint to use, read about
   :how-to:`special considerations for choosing a region <about-regions>`.

.. _api-info-service-access-regional:

.. list-table:: **Regionalized service endpoints**
    :widths: 10 40
    :header-rows: 1

    * - Region
      - Endpoint
    * - Chicago (ORD)
      - ``https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234``
    * - Dallas/Ft. Worth (DFW)
      - ``https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/1234``
    * - Northern Virginia (IAD)
      - ``https://iad.loadbalancers.api.rackspacecloud.com/v1.0/1234``
    * - London (LON)
      - ``https://lon.loadbalancers.api.rackspacecloud.com/v1.0/1234``
    * - Sydney (SYD)
      - ``https://syd.loadbalancers.api.rackspacecloud.com/v1.0/1234``
    * - Hong Kong (HKG)
      - ``https://hkg.loadbalancers.api.rackspacecloud.com/v1.0/1234``


Replace the sample account ID number, ``1234``, with your actual account number
that is returned as part of the authentication response. The account number is
located  after the  final slash (/) in the ``publicURL`` field.

The service catalog returned in the authentication response specifies the
correct service access endpoint for your account to use for accessing Cloud
Load Balancers. Use the service type (``rax:load-balancer``) to locate the
correct endpoint in the service catalog. For an example of the service catalog,
see :ref:`authentication response examples <authentication-response-examples>`.

- If you are load balancing **cloud servers**, you can determine the
  appropriate region to select by viewing your Cloud Servers list and
  creating a load balancer within the same region as the data center in which
  your servers reside. When your resources reside in the same region as your
  load balancer, devices are in close proximity to each other and can take
  advantage of ServiceNet connectivity for free data transfer between
  services.

  .. note::

     ServiceNet is an internal Rackspace only, multitenant network connection
     within each Rackspace data center. ServiceNet IP addresses are not
     accessible via the public Internet. Rackspace customers can configure
     resources to use an internal IP address so that traffic over the
     ServiceNet network is not billed.

- If you are load balancing **external servers**, you can determine the
  appropriate region to select by choosing the region that is geographically
  as close to your external servers as possible.
