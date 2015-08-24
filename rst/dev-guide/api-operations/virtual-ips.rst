.. _api-operations-virtual-ips: 

Virtual IPs 
~~~~~~~~~~~~~~~~~~~~

A `virtual IP <#>`__ (VIP) makes a load balancer accessible by clients.
The load balancing service supports either a public VIP, routable on the
public Internet, or a ServiceNet address, routable only within the
region in which the load balancer resides.

..  note:: 
Note
All load balancers must have at least one virtual IP associated with
them at all times. Attempting to delete the last virtual IP results in a
400 (badRequest) fault. To bulk-delete virtual IPs, provide a query
parameter list of virtual ip IDs. For example:
/virtualips?id=``virtualIpId``\ &id=\ ``virtualIpId``. The current
default limit is ten IDs per request. Any and all configuration data is
immediately purged and is not recoverable. If one or more of the items
in the list cannot be removed due to its current status, a 400
(badRequest) is returned along with the IDs of the ones the system
identified as potential failures for this request.

Table 4.5. Virtual IP types
Name
Description
``PUBLIC``
An address that is routable on the public Internet.
``SERVICENET``
An address that is routable only on ServiceNet.
The following table lists the required and optional attributes:

Table 4.6. Required and optional attributes
Name
Description
Required
ipVersion
IP Version: must be set to ``IPV6``.
Yes
type
Type of virtualIp to add:

-  ``PUBLIC`` – Virtual IP on the public internet.

-  ``SERVICENET`` – Virtual IP on the Rackspace private ServiceNet.

Yes

.. include::  get-listvirtualips-v1.0-account-loadbalancers-loadbalancerid-virtualips-virtual-ips.rst
.. include::  post-addvirtualipv6-v1.0-account-loadbalancers-loadbalancerid-virtualips-virtual-ips.rst
.. include::  delete-bulkdeletevirtualips-v1.0-account-loadbalancers-loadbalancerid-virtualips-virtual-ips.rst
.. include::  delete-deletevirtualip-v1.0-account-loadbalancers-loadbalancerid-virtualips-virtualipid-virtual-ips.rst