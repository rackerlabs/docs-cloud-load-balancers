
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-show-health-monitor-configuration-v1.0-account-loadbalancers-loadbalancerid-healthmonitor:

Show health monitor configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/healthmonitor

Shows the health monitor configuration, if one exists.

**Connect Monitor.** The monitor connects to each node on its defined port to ensure that the service is listening properly. The connect monitor is the most basic type of health check and does no post-processing or protocol specific health checks. It includes several configurable properties. The following table lists the required and optional attributes for Monitor Connections:

.. table:: Attributes for Connect Monitor


    +---------------------------------------+--------------------------------------+
    |Name                                   |Description                           |
    +=======================================+======================================+
    |attemptsBeforeDeactivation             |Number of permissible monitor         |
    |                                       |failures before removing a node from  |
    |                                       |rotation. Must be a number between 1  |
    |                                       |and 10.                               |
    +---------------------------------------+--------------------------------------+
    |delay                                  |The minimum number of seconds to wait |
    |                                       |before executing the health monitor.  |
    |                                       |Must be a number between 1 and 3600.  |
    +---------------------------------------+--------------------------------------+
    |timeout                                |Maximum number of seconds to wait for |
    |                                       |a connection to be established before |
    |                                       |timing out. Must be a number between  |
    |                                       |1 and 300.                            |
    +---------------------------------------+--------------------------------------+
    |type                                   |Type of the health monitor. Must be   |
    |                                       |specified as "CONNECT" to monitor     |
    |                                       |connections.                          |
    +---------------------------------------+--------------------------------------+




**Monitor HTTP and HTTPS.** The HTTP and HTTPS monitor is more intelligent than the connect monitor. It is capable of processing an HTTP or HTTPS response to determine the condition of a node. It supports the same basic properties as the connect monitor and includes additional attributes that are used to evaluate the HTTP response. The user can supply an optional ``hostHeader`` attribute for the HTTP and HTTPS health monitor to specify a host for which the health monitors will check. The following table lists the required and optional attributes for Monitor HTTP and HTTPS:

.. table:: Attributes for HTTP and HTTPS Monitor


    +---------------------------------------+--------------------------------------+
    |Name                                   |Description                           |
    +=======================================+======================================+
    |attemptsBeforeDeactivation             |Number of permissible monitor         |
    |                                       |failures before removing a node from  |
    |                                       |rotation. Must be a number between 1  |
    |                                       |and 10.                               |
    +---------------------------------------+--------------------------------------+
    |bodyRegex                              |A regular expression that will be     |
    |                                       |used to evaluate the contents of the  |
    |                                       |body of the response. For example you |
    |                                       |could use the regular expression      |
    |                                       |"^.*(Unauthorized|Forbidden|Not       |
    |                                       |Found|Timeout|Server Error).*$" to    |
    |                                       |look for any of those potentially     |
    |                                       |problematic strings in the body of    |
    |                                       |the response or use the regular       |
    |                                       |expression "^success$" to look for    |
    |                                       |the string "success".                 |
    |                                       |                                      |
    |                                       |**Note:**                             |
    |                                       |The                                   |
    |                                       |system only evaluates the first 2048  |
    |                                       |bytes of the response against the     |
    |                                       |bodyRegex that is specified, so you   |
    |                                       |will want to test accordingly. To     |
    |                                       |debug the HTTP/HTTPS health           |
    |                                       |monitoring you will want to test the  |
    |                                       |bodyRegex against the IP of the       |
    |                                       |node(s) that are being disabled. You  |
    |                                       |can use the following cURL command to |
    |                                       |see what the health monitoring        |
    |                                       |analyzes: curl -s -r 0-2048           |
    |                                       |https://YOUR_IP_ADDRESS | head -c     |
    |                                       |2048 | egrep "YOUR_REGULAR_EXPRESSION"|
    +---------------------------------------+--------------------------------------+
    |delay                                  |The minimum number of seconds to wait |
    |                                       |before executing the health monitor.  |
    |                                       |Must be a number between 1 and 3600.  |
    +---------------------------------------+--------------------------------------+
    |hostHeader                             |The name of a host for which the      |
    |                                       |health monitors will check.           |
    +---------------------------------------+--------------------------------------+
    |path                                   |The HTTP path that will be used in    |
    |                                       |the sample request.                   |
    +---------------------------------------+--------------------------------------+
    |statusRegex                            |A regular expression that will be     |
    |                                       |used to evaluate the HTTP status code |
    |                                       |returned in the response.             |
    +---------------------------------------+--------------------------------------+
    |timeout                                |Maximum number of seconds to wait for |
    |                                       |a connection to be established before |
    |                                       |timing out. Must be a number between  |
    |                                       |1 and 300.                            |
    +---------------------------------------+--------------------------------------+
    |type                                   |Type of the health monitor. Must be   |
    |                                       |specified as "HTTP" to monitor an     |
    |                                       |HTTP response or "HTTPS" to monitor   |
    |                                       |an HTTPS response.                    |
    +---------------------------------------+--------------------------------------+






This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Show connect monitor configuration: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    
    <healthMonitor xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        type="CONNECT"
        delay="10"
        timeout="10"
        attemptsBeforeDeactivation="3" />


**Example Show connect monitor configuration: JSON response**


.. code::

    {
        "healthMonitor":{
            "type": "CONNECT",
            "delay": 10,
            "timeout": 10,
            "attemptsBeforeDeactivation": 3
        }
    }


**Example Show http monitor configuration: ATOM/XML response**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next"
              href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/healthmonitor.atom?page=2"/>
        <title type="text">Health Monitor Feed</title>
        <id>1234-loadbalancers-141-healthmonitor</id>
        <author>
            <name>Rackspace Cloud</name>
        </author>
        <entry>
            <title type="text">Health Monitor Successfully Updated</title>
            <summary
                    type="text">Health monitor successfully updated with type: 'HTTP', delay: '10', timeout: '10', attemptsBeforeDeactivation: '3', path: '/', statusRegex: '^[234][0-9][0-9]$', bodyRegex: '^[234][0-9][0-9]$'
            </summary>
            <author>
                <name>tvardema</name>
            </author>
            <link href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/healthmonitor/"/>
            <id>1234-loadbalancers-141-healthmonitor-201142022120</id>
            <category term="UPDATE"/>
            <updated>2011-02-11T00:22:12.000Z</updated>
        </entry>
    </feed>


**Example Show http monitor configuration: JSON response**


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
            "hostHeader": "myrack.com"
        }
    }


**Example Show http monitor configuration: XML response**


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
        hostHeader="myrack.com"/>


**Example Show https monitor configuration: JSON response**


.. code::

    {
        "healthMonitor": {
            "type": "HTTPS",
            "delay": 10,
            "timeout":10,
            "attemptsBeforeDeactivation": 3,
            "path": "/",
            "statusRegex":"^[234][0-9][0-9]$",
            "bodyRegex": "^[234][0-9][0-9]$",
            "hostHeader": "myrack.com"
        }
    }


**Example Show https monitor configuration: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    
    <healthMonitor xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        type="HTTPS"
        delay="10"
        timeout="10"
        attemptsBeforeDeactivation="3"
        path="/"
        statusRegex="^[234][0-9][0-9]$"
        bodyRegex=""
        hostHeader="myrack.com"/>

