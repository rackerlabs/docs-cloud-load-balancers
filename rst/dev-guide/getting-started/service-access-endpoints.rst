========================
Service Access/Endpoints
========================

Specify a region to operate against by selecting an endpoint from the
table below to use for your Cloud Load Balancer API calls.

.. tip::
   To help you decide which regionalized endpoint to use, read about
   special considerations for choosing a region at
   http://www.rackspace.com/knowledge_center/article/about-regions.

**Regionalized Service Endpoints**


Chicago (ORD)
``https://ord.loadbalancers.api.rackspacecloud.com/v1.0/``\ *``1234``*/

Dallas/Ft. Worth (DFW)
``https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/``\ *``1234``*/

Northern Virginia (IAD)
``https://iad.loadbalancers.api.rackspacecloud.com/v1.0/``\ *``1234``*/

London (LON)
``https://lon.loadbalancers.api.rackspacecloud.com/v1.0/``\ *``1234``*/

Sydney (SYD)
``https://syd.loadbalancers.api.rackspacecloud.com/v1.0/``\ *``1234``*/

Hong Kong (HKG)
``https://hkg.loadbalancers.api.rackspacecloud.com/v1.0/``\ *``1234``*/

**Since you are load balancing Cloud Servers** in this guide, you can
determine the appropriate endpoint to select by viewing your Cloud
Servers list and creating a load balancer within the same region as the
datacenter in which your Cloud Server resides. When your resources
reside in the same region as your load balancer, devices are in close
proximity to each other and can take advantage of ServiceNet
connectivity for free data transfer between services.

.. note::
   All examples in this guide assume that you are operating against the DFW
   datacenter, however if you are using a different datacenter, be sure to
   use the associated endpoint from the table above instead.

Replace the sample account ID number, *``1234``*, with your actual
account number returned as part of the authentication response. Use your
actual account number wherever you see the field **your\_acct\_id**
specified in this guide. Refer to `Chapter 4, *Generate an
Authentication Token* <ch04.xhtml>`__.

When making a Cloud Load Balancers API call, place the endpoint at the
beginning of the request URL, for example:
(``https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/``\ **your\_acct\_id**\ ``/``),
as you can see in the cURL Create Load Balancer Request examples in
`Chapter 6, *Create a Load Balancer* <ch06.xhtml>`__. Note that the
``v1.0`` component in the URL indicates that you are using version 1.0
of the Cloud Load Balancers API.
