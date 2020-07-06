.. _monitors:

========
Monitors
========

.. contents::
   :local:
   :depth: 1

The load balancing service includes a health monitoring operation that
periodically checks your back-end nodes to ensure they are responding
correctly. If a node does not respond, it is removed from rotation until
the health monitor determines that the node is functional. In
addition to being performed periodically, the health check also is
performed against every node that is added to ensure that the node is
operating properly before allowing it to service traffic. Only one
health monitor is allowed to be enabled on a load balancer at a time.

As part of your strategy for monitoring connections, you should consider
defining secondary nodes that provide failover for effectively routing
traffic in case the primary node fails. This is an additional feature
that ensures that you remain up in case your primary node fails.

Every health monitor has a ``type`` attribute to signify what kind of
monitor it is, as shown in the following table:

.. table:: Health monitor types

+---------+--------------------------------------+
| Name    | Description                          |
+=========+======================================+
| CONNECT | Health monitor is a connect monitor. |
+---------+--------------------------------------+
| HTTP    | Health monitor is an HTTP monitor.   |
+---------+--------------------------------------+
| HTTPS   | Health monitor is an HTTPS monitor.  |
+---------+--------------------------------------+

For more information about the three types of monitors, including required and
optional parameters, see :ref:`get-show-health-monitor-configuration`.

..  note::

  When deleting a health monitor of any type, every node on that load
  balancer that is enabled or has failed and is in OFFLINE status has its
  status updated to ONLINE regardless of the health of the node.

.. include:: methods/get-show-health-monitor-configuration-v1.0-account-loadbalancers-loadbalancerid-healthmonitor.rst
.. include:: methods/put-update-health-monitor-v1.0-account-loadbalancers-loadbalancerid-healthmonitor.rst
.. include:: methods/delete-delete-health-monitor-v1.0-account-loadbalancers-loadbalancerid-healthmonitor.rst
