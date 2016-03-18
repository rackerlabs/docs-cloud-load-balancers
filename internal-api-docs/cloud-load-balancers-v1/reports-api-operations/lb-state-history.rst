.. _lb-state-history:

==================================
Load balancer state history
==================================

You can configure all documented features of the load balancer when you
create it by providing the additional elements or attributes
in the request. 

The ``vip_subnet_id`` specified for the load balancer determines the
type of IP address and what network it is allocated on.

All load balancers also have a ```status`` attribute that shows the current
configuration status of the device. This status is immutable by the
user and is updated automatically based on state changes within the
service. The following table describes the possible statuses.

**Load balancer statuses**

+---------------------+------------------------------------------------------------------------------------------+
| Name                | Description                                                                              |
+=====================+==========================================================================================+
| ``ACTIVE``          | The load balancer is configured properly and ready to serve traffic to incoming requests |
|                     | via the configured virtual IPs.                                                          |
+---------------------+------------------------------------------------------------------------------------------+
| ``PENDING_CREATE``  | The load balancer is being provisioned for the first time and configuration is being     |
|                     | applied to bring the service online. The service cannot yet serve incoming requests.     |
+---------------------+------------------------------------------------------------------------------------------+
| ``PENDING_UPDATE``  | The load balancer is online but configuration changes are being applied to update the    |
|                     | service based on a previous request.                                                     |
+---------------------+------------------------------------------------------------------------------------------+
| ``PENDING_DELETE``  | The load balancer is online but configuration changes are being applied to begin deletion|
|                     | of the service based on a previous request.                                              |
+---------------------+------------------------------------------------------------------------------------------+
|  ``SUSPENDED``      | The load balancer was taken offline and disabled; contact Support.                       |
+---------------------+------------------------------------------------------------------------------------------+
|  ``ERROR``          | The system encountered an error when attempting to configure the load balancer;          |
|                     | contact Support.                                                                         |
+---------------------+------------------------------------------------------------------------------------------+
|  ``DELETED``        | The load balancers in ``DELETED`` status can be displayed for at least 90 days after     |
|                     | deletion.                                                                                |
+---------------------+------------------------------------------------------------------------------------------+


.. include:: methods/get-listloadbalancersv2.rst
.. include:: methods/post-createloadbalancerv2.rst
.. include:: methods/get-showloadbalancerv2.rst
.. include:: methods/put-updateloadbalancerv2.rst
.. include:: methods/delete-deleteloadbalancerv2.rst

