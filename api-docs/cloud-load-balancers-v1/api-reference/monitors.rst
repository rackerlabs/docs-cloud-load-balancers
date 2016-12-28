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
monitor it is.

Table. Health monitor types

+---------+--------------------------------------+
| Name    | Description                          |
+=========+======================================+
| CONNECT | Health monitor is a connect monitor. |
+---------+--------------------------------------+
| HTTP    | Health monitor is an HTTP monitor.   |
+---------+--------------------------------------+
| HTTPS   | Health monitor is an HTTPS monitor.  |
+---------+--------------------------------------+


..  note::

  When deleting a health monitor of any type, every node on that load
  balancer that is enabled or has failed and is in OFFLINE status has its
  status updated to ONLINE regardless of the health of the node.

**Connect Monitor. **\ The monitor connects to each node on its defined
port to ensure that the service is listening properly. The connect
monitor is the most basic type of health check and does no
post-processing or protocol specific health checks. It includes several
configurable properties. The following table lists the required and
optional attributes for Monitor Connections:

Table. Required and Optional Attributes for Monitor Connections

+----------------------------+----------------------------------------------+----------+
| Name                       | Description                                  | Required |
+============================+==============================================+==========+
| attemptsBeforeDeactivation | Number of permissible monitor failures       | Yes      |
|                            | before removing a node from rotation.        |          |
|                            | Must be a number between 1 and 10.           |          |
+----------------------------+----------------------------------------------+----------+
| delay                      | The minimum number of seconds to wait before | Yes      |
|                            | executing the health monitor. Must be a      |          |
|                            | number between 1 and 3600.                   |          |
+----------------------------+----------------------------------------------+----------+
| timeout                    | Maximum number of seconds to wait for a      | Yes      |
|                            | connection to be established before timing   |          |
|                            | out. Must be a number between 1 and 300.     |          |
+----------------------------+----------------------------------------------+----------+
| type                       | Type of the health monitor. Must be          | Yes      |
|                            | specified as "CONNECT" to monitor            |          |
|                            | connections.                                 |          |
+----------------------------+----------------------------------------------+----------+

**Monitor HTTP and HTTPS. **\ The HTTP and HTTPS monitor is more
intelligent than the connect monitor. It is capable of processing an
HTTP or HTTPS response to determine the condition of a node. It supports
the same basic properties as the connect monitor and includes additional
attributes that are used to evaluate the HTTP response. The user can
supply an optional ``hostHeader`` attribute for the HTTP and HTTPS
health monitor to specify a host for which the health monitors will
check. The following table lists the required and optional attributes
for Monitor HTTP and HTTPS:

Table. Required and Optional Attributes for Monitor HTTP and HTTPS

+----------------------------+----------------------------------------------+----------+
| Name                       | Description                                  | Required |
+============================+==============================================+==========+
| attemptsBeforeDeactivation | Number of permissible monitor failures       | Yes      |
|                            | before removing a node from rotation.        |          |
|                            | Must be a number between 1 and 10.           |          |
+----------------------------+----------------------------------------------+----------+
| bodyRegex                  | A regular expression that will be used to    | Yes      |
|                            | evaluate the contents of the body of the     |          |
|                            | response.                                    |          |
|                            |                                              |          |
|                            | For example you could use the regular        |          |
|                            | expression "^.*(Unauthorized|Forbidden|      |          |
|                            | Not Found|Timeout|Server Error).*$"          |          |
|                            | to look for any of those problematic strings.|          |
|                            | in the body of the response or use the       |          |
|                            | regular expression "^success$" to look for   |          |
|                            | the string "success".                        |          |
|                            |                                              |          |
|                            | ..  note::                                   |          |
|                            |                                              |          |
|                            |   The system only evaluates the first 2048   |          |
|                            |   bytes of the response against the          |          |
|                            |   bodyRegex that is specified, so you        |          |
|                            |   will want to test accordingly.             |          |
|                            |                                              |          |
|                            | To debug the HTTP/HTTPS health monitoring    |          |
|                            | you will want to test the bodyRegex against  |          |
|                            | the IP of the node(s) that are being         |          |
|                            | disabled.                                    |          |
|                            |                                              |          |
|                            | You can use the following cURL command to    |          |
|                            | see what the health monitoring analyzes:     |          |
|                            |                                              |          |
|                            | curl -s -r 0-2048 https://YOUR_IP_ADDRESS |  |          |
|                            | head -c2048 | egrep                          |          |
|                            | "YOUR_REGULAR_EXPRESSION"                    |          |
+----------------------------+----------------------------------------------+----------+
| delay                      | The minimum number of seconds to wait before | Yes      |
|                            | executing the health monitor. Must be a      |          |
|                            | number between 1 and 3600.                   |          |
+----------------------------+----------------------------------------------+----------+
| hostHeader                 | The name of a host for which the health      | No       |
|                            | monitors will check.                         |          |
+----------------------------+----------------------------------------------+----------+
| path                       | The HTTP path that will be used in the       | Yes      |
|                            | sample request.                              |          |
+----------------------------+----------------------------------------------+----------+
| statusRegex                | A regular expression that will be used to    | Yes      |
|                            | evaluate the HTTP status code returned in    |          |
|                            | the response.                                |          |
+----------------------------+----------------------------------------------+----------+
| timeout                    | Maximum number of seconds to wait for a      | Yes      |
|                            | connection to be established before timing   |          |
|                            | out. Must be a number between 1 and 300.     |          |
+----------------------------+----------------------------------------------+----------+
| type                       | Type of the health monitor. Must be          | Yes      |
|                            | specified as "HTTP" to monitor an HTTP       |          |
|                            | response or "HTTPS" to monitor an HTTPS      |          |
|                            | response.                                    |          |
+----------------------------+----------------------------------------------+----------+

.. include:: methods/get-show-health-monitor-configuration-v1.0-account-loadbalancers-loadbalancerid-healthmonitor.rst
.. include:: methods/put-update-health-monitor-v1.0-account-loadbalancers-loadbalancerid-healthmonitor.rst
.. include:: methods/delete-delete-health-monitor-v1.0-account-loadbalancers-loadbalancerid-healthmonitor.rst
