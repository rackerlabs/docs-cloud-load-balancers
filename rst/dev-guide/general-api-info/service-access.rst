.. _service-access:

============================
Service access and endpoints
============================

The load balancing service is a regionalized service. It allows the caller to select a region into which a load balancer is to be provisioned.

To determine which region to operate against, select an endpoint from
the table below.

.. tip::
   To help you decide which regionalized endpoint to use, read about `special considerations for choosing a region`_.

.. _special considerations for choosing a region: http://www.rackspace.com/knowledge_center/article/about-regions

.. _clb-dg-api-info-service-access-regional:

Regionalized service endpoints
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------------------------+-------------------------------------------------------------+
| Region                  | Endpoint                                                    |
+=========================+=============================================================+
| Chicago (ORD)           | https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234  |
+-------------------------+-------------------------------------------------------------+
| Dallas/Ft. Worth (DFW)  | https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/1234  |
+-------------------------+-------------------------------------------------------------+
| Northern Virginia (IAD) | https://iad.loadbalancers.api.rackspacecloud.com/v1.0/1234  |
+-------------------------+-------------------------------------------------------------+
| London (LON)            | https://lon.loadbalancers.api.rackspacecloud.com/v1.0/1234  |
+-------------------------+-------------------------------------------------------------+
| Sydney (SYD)            | https://syd.loadbalancers.api.rackspacecloud.com/v1.0/1234  |
+-------------------------+-------------------------------------------------------------+
| Hong Kong (HKG)         | https://hkg.loadbalancers.api.rackspacecloud.com/v1.0/1234  |
+-------------------------+-------------------------------------------------------------+

Replace the sample account ID number, ``1234``, with your actual account number returned as 
part of the authentication service response. You find the actual account number after the 
final `/` in the ``publicURL`` field returned by the authentication response. In 
:ref:`Review the authentication response <review-auth-resp>`, 
the account (tenant) ID is ``110011``, as you can see from the ``publicURL`` field for 
``cloudDatabases``: ``https://dfw.databases.api.rackspacecloud.com/v1.0/110011``.

**If load balancing Cloud Servers**, you can determine the appropriate region to select 
by viewing your Cloud Servers list and creating a load balancer within the same region as the datacenter in which your Cloud Server resides. When your resources reside in the same region as your load balancer, devices are in close proximity to each other and can take advantage of ServiceNet connectivity for free data transfer between services.

.. note::
   ServiceNet is an internal Rackspace-only, multi-tenant network connection within each Rackspace datacenter. ServiceNet IPs are not accessible via the public internet. Rackspace customers may configure resources to utilize an internal IP address so that traffic over the ServiceNet network is not billed.

**If load balancing external servers**, you can determine the appropriate region to select by choosing the region that is geographically as close to your external servers as possible.
