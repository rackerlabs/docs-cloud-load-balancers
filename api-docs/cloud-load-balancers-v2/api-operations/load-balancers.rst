.. _load_balancers:

=====================
Load balancers 
=====================


Users can configure all documented features of the load balancer at
creation time by simply providing the additional elements or attributes
in the request. This document provides an overview of all the features
the load balancing service supports.

The ``vip_subnet_id`` specified for the load balancer determines the
type of IP and what network it is allocated on.

All load balancers also have a status attribute that shows current
configuration status of the device. This status is immutable by the
caller and is updated automatically based on state changes within the
service. When a load balancer is first created, it is placed into a
``PENDING_CREATE`` status while the configuration is being generated and
applied based on the request. Once the configuration is applied and
finalized, it is in an ``ACTIVE`` status. In the event of a
configuration change or update, the status of the load balancer changes
to ``PENDING_UPDATE`` to signify configuration changes are in progress
but are not yet been finalized. Load balancers in a ``SUSPENDED`` status
are configured to reject traffic and does not forward requests to
back-end members.

Table 4.1. Load balancer statuses

+---------------------+------------------------------------------------------------------------------------------+
|      **Name**       |       **Description**                                                                    |
+=====================+==========================================================================================+
| ``ACTIVE``          | Load balancer is configured properly and ready to serve traffic to incoming requests via |
|                     | the configured virtual IPs.                                                              |
+---------------------+------------------------------------------------------------------------------------------+
| ``PENDING_CREATE``  | Load balancer is being provisioned for the first time and configuration is being applied |
|                     | to bring the service online. The service cannot yet serve incoming requests.             |
+---------------------+------------------------------------------------------------------------------------------+
| ``PENDING_UPDATE``  | Load balancer is online but configuration changes are being applied to update the service|
|                     | based on a previous request.                                                             |
+---------------------+------------------------------------------------------------------------------------------+
| ``PENDING_DELETE``  | Load balancer is online but configuration changes are being applied to begin deletion of |
|                     | the service based on a previous request.                                                 |
+---------------------+------------------------------------------------------------------------------------------+
|  ``SUSPENDED``      | Load balancer has been taken offline and disabled; contact Support.                      |
+---------------------+------------------------------------------------------------------------------------------+
|  ``ERROR``          | The system encountered an error when attempting to configure the load balancer;          |
|                     | contact Support.                                                                         |
+---------------------+------------------------------------------------------------------------------------------+
|  ``DELETED``        | Load balancers in DELETED status can be displayed for at least 90 days after deletion.   |
+---------------------+------------------------------------------------------------------------------------------+


The update operation allows the caller to change one or more of the
following attributes:

-  ``name``

-  ``description``

-  ``admin_state_up``

.. include:: methods/get-listloadbalancersv2.rst
.. include:: methods/post-createloadbalancerv2.rst
.. include:: methods/get-showloadbalancerv2.rst
.. include:: methods/put-updateloadbalancerv2.rst
.. include:: methods/delete-deleteloadbalancerv2.rst

