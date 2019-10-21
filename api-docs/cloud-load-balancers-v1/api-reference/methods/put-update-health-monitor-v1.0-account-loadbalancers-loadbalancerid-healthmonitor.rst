.. _put-update-health-monitor:

Update health monitor
~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/healthmonitor

Updates the settings for a health monitor.

Every health monitor has a ``type`` attribute to signify what kind of monitor
it is.

The following table lists the health monitor types:

.. table:: Health monitor types

    +---------------------------------------+--------------------------------------+
    |Name                                   |Description                           |
    +=======================================+======================================+
    |CONNECT                                |Health monitor is a connect monitor.  |
    +---------------------------------------+--------------------------------------+
    |HTTP                                   |Health monitor is a HTTP monitor.    |
    +---------------------------------------+--------------------------------------+
    |HTTPS                                  |Health monitor is a HTTPS monitor.   |
    +---------------------------------------+--------------------------------------+

.. note::

   When deleting a health monitor of any type, every node on that load balancer
   that is enabled or has failed and is in OFFLINE status has its status updated
   to ONLINE regardless of the health of the node.

**Connect Monitor** The monitor connects to each node on its defined port to
ensure that the service is listening properly. The connect monitor is the most
basic type of health check and does no post-processing or protocol specific
health checks. It includes several configurable properties. The following
table lists the required and optional attributes for Monitor Connections:

.. table:: Required and Optional Attributes for Monitor Connections

    +---------------------------+-------------------------+------------------------+
    |Name                       |Description              |Required                |
    +===========================+=========================+========================+
    |attemptsBeforeDeactivation |Number of permissible    |Yes                     |
    |                           |monitor failures before  |                        |
    |                           |removing a node from     |                        |
    |                           |rotation. Must be a      |                        |
    |                           |number between 1 and 10. |                        |
    +---------------------------+-------------------------+------------------------+
    |delay                      |The minimum number of    |Yes                     |
    |                           |seconds to wait before   |                        |
    |                           |executing the health     |                        |
    |                           |monitor. Must be a       |                        |
    |                           |number between 1 and     |                        |
    |                           |3600.                    |                        |
    +---------------------------+-------------------------+------------------------+
    |timeout                    |Maximum number of        |Yes                     |
    |                           |seconds to wait for a    |                        |
    |                           |connection to be         |                        |
    |                           |established before       |                        |
    |                           |timing out. Must be a    |                        |
    |                           |number between 1 and 300.|                        |
    +---------------------------+-------------------------+------------------------+
    |type                       |Type of the health       |Yes                     |
    |                           |monitor. Must be         |                        |
    |                           |specified as "CONNECT"   |                        |
    |                           |to monitor connections.  |                        |
    +---------------------------+-------------------------+------------------------+

**Monitor HTTP and HTTPS**  The HTTP and HTTPS monitor is more intelligent than
the connect monitor. It is capable of processing a HTTP or HTTPS response to
determine the condition of a node. It supports the same basic properties as
the connect monitor and includes additional attributes that are used to
evaluate the HTTP response. The user can supply an optional ``hostHeader``
attribute for the HTTP and HTTPS health monitor to specify a host for which
the health monitors will check. The following table lists the required and
optional attributes for Monitor HTTP and HTTPS:

.. table:: Required and Optional Attributes for Monitor HTTP and HTTPS

    +---------------------------+---------------------------------+----------------+
    |Name                       |Description                      |Required        |
    +===========================+=================================+================+
    |attemptsBeforeDeactivation |Number of permissible monitor    |Yes             |
    |                           |failures before removing a node  |                |
    |                           |from rotation. Must be a number  |                |
    |                           |between 1 and 10.                |                |
    +---------------------------+---------------------------------+----------------+
    |bodyRegex                  |A regular expression that will   |No              |
    |                           |be used to evaluate the contents |                |
    |                           |of the body of the response. For |                |
    |                           |example you could use the        |                |
    |                           |regular expression               |                |
    |                           |"^.*(Unauthorized|Forbidden|Not  |                |
    |                           |Found|Timeout|Server Error).*$"  |                |
    |                           |to look for any of those         |                |
    |                           |potentially problematic strings  |                |
    |                           |in the body of the response or   |                |
    |                           |use the regular expression       |                |
    |                           |"^success$" to look for the      |                |
    |                           |string "success".                |                |
    |                           |                                 |                |
    |                           |**Note:**                        |                |
    |                           |The                              |                |
    |                           |system only evaluates the first  |                |
    |                           |2048 bytes of the response       |                |
    |                           |against the bodyRegex that is    |                |
    |                           |specified, so you will want to   |                |
    |                           |test accordingly. To debug the   |                |
    |                           |HTTP/HTTPS health monitoring you |                |
    |                           |will want to test the bodyRegex  |                |
    |                           |against the IP of the node(s)    |                |
    |                           |that are being disabled. You can |                |
    |                           |use the following cURL command   |                |
    |                           |to see what the health           |                |
    |                           |monitoring analyzes: curl -s -r  |                |
    |                           |0-2048 https://YOUR_IP_ADDRESS | |                |
    |                           |head -c 2048 | egrep             |                |
    |                           |"YOUR_REGULAR_EXPRESSION"        |                |
    +---------------------------+---------------------------------+----------------+
    |delay                      |The minimum number of seconds to |Yes             |
    |                           |wait before executing the health |                |
    |                           |monitor. Must be a number        |                |
    |                           |between 1 and 3600.              |                |
    +---------------------------+---------------------------------+----------------+
    |hostHeader                 |The name of a host for which the |No              |
    |                           |health monitors will check.      |                |
    +---------------------------+---------------------------------+----------------+
    |path                       |The HTTP path that will be used  |Yes             |
    |                           |in the sample request.           |                |
    +---------------------------+---------------------------------+----------------+
    |statusRegex                |A regular expression that will   |Yes             |
    |                           |be used to evaluate the HTTP     |                |
    |                           |status code returned in the      |                |
    |                           |response.                        |                |
    +---------------------------+---------------------------------+----------------+
    |timeout                    |Maximum number of seconds to     |Yes             |
    |                           |wait for a connection to be      |                |
    |                           |established before timing out.   |                |
    |                           |Must be a number between 1 and   |                |
    |                           |300.                             |                |
    +---------------------------+---------------------------------+----------------+
    |type                       |Type of the health monitor. Must |Yes             |
    |                           |be specified as "HTTP" to        |                |
    |                           |monitor a HTTP response or      |                |
    |                           |"HTTPS" to monitor a HTTPS      |                |
    |                           |response.                        |                |
    +---------------------------+---------------------------------+----------------+

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|422                       |ImmutableEntity          |This fault is returned   |
|                          |                         |when a user attempts to  |
|                          |                         |modify an item that is   |
|                          |                         |not currently in a state |
|                          |                         |that allows              |
|                          |                         |modification. For        |
|                          |                         |example, load balancers  |
|                          |                         |in a status of           |
|                          |                         |PENDING_UPDATE,BUILD, or |
|                          |                         |DELETED may not be       |
|                          |                         |modified.                |
+--------------------------+-------------------------+-------------------------+
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+

Request
-------

The following table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String                   |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+


**Example Update Connect health monitor: XML request**

.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <healthMonitor xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        type="CONNECT"
        delay="10"
        timeout="10"
        attemptsBeforeDeactivation="3" />

**Example Update Connect health monitor: JSON request**

.. code::

    {
        "healthMonitor":{
            "type": "CONNECT",
            "delay": 10,
            "timeout": 10,
            "attemptsBeforeDeactivation": 3
        }
    }

**Example Update HTTP health monitor: XML request**

.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <healthMonitor xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        type="HTTP"
        delay="10"
        timeout="10"
        attemptsBeforeDeactivation="3"
        path="/"
        statusRegex="^[234][0-9][0-9]$"
        bodyRegex="^[234][0-9][0-9]$"
        hostHeader="mysite.com"/>

**Example Update HTTP health monitor: JSON request**

.. code::

    {
        "healthMonitor": {
            "type": "HTTP",
            "delay": 10,
            "timeout":10,
            "attemptsBeforeDeactivation": 3,
            "path": "/",
            "statusRegex":"^[234][0-9][0-9]$",
            "bodyRegex": "^[234][0-9][0-9]$",
            "hostHeader": "mysite.com"
        }
    }

Response
--------


This operation does not return a response body.
