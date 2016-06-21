.. _limits:

Limits
~~~~~~~~~~~

All accounts, by default, have a preconfigured set of thresholds (or limits)
to manage capacity and prevent abuse of the system. The system recognizes two
kinds of limits: rate limits and absolute limits. Rate limits are thresholds
that are reset after a certain amount of time passes. Absolute limits are
fixed. Rate limits are processed via the `Repose service`_.

.. note::
  If the default limits are too low for your particular application, please
  contact Rackspace Cloud support to request an increase. All requests require
  reasonable justification.

.. _Repose service: http://www.openrepose.org

.. _clb-dg-api-info-limits-ratelimits:

Rate limits
^^^^^^^^^^^^^^

We specify rate limits in terms of both a human-readable wild-card URI and a
machine-processable regular expression. The regular expression boundary
matcher '^' takes effect after the root URI path. For example, the regular
expression `^/v1.0/1234/loadbalancers` would match the portion
`/v1.0/1234/loadbalancers` of the following URI:
`https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers`.

.. _clb-dg-api-info-limits-ratelimits-default:

**Default rate limits**

+--------+---------+----------+---------------+
| Verb   | URI     | RegEx    | Default limit |
+========+=========+==========+===============+
| GET    | /v1.0/* | ^/1.0/.* | 5/second      |
+--------+---------+----------+---------------+
| GET    | /v1.0/* | ^/1.0/.* | 100/minute    |
+--------+---------+----------+---------------+
| POST   | /v1.0/* | ^/1.0/.* | 2/second      |
+--------+---------+----------+---------------+
| POST   | /v1.0/* | ^/1.0/.* | 25/minute     |
+--------+---------+----------+---------------+
| PUT    | /v1.0/* | ^/1.0/.* | 5/second      |
+--------+---------+----------+---------------+
| PUT    | /v1.0/* | ^/1.0/.* | 50/minute     |
+--------+---------+----------+---------------+
| DELETE | /v1.0/* | ^/1.0/.* | 2/second      |
+--------+---------+----------+---------------+
| DELETE | /v1.0/* | ^/1.0/.* | 50/minute     |
+--------+---------+----------+---------------+

Rate limits are applied in order relative to the verb, going from least to
most specific. For example, although the threshold for **POST** to /v1.0/\* is
25 per minute, one cannot **POST** to /v1.0/\* more than 2 times per second
because the rate limit for any **POST** is 2 per second. In the event you
exceed the thresholds established for your account, a 413 (Rate Control) HTTP
response is returned with a `Retry-After` header to notify the client when they
can attempt to try again.

A request may be submitted to Cloud Support for an increase in load balancer
limits. Each request must be approved before limits can be modified. Limits
can only be increased up to the maximum limit (such as 50 nodes per load
balancer).

See :ref:`Determine limits programmatically <determine-limits>` to find your
current account settings for these limits.

Absolute limits
~~~~~~~~~~~~~~~

Absolute limits specify the maximum number of load balancers that can exist per
Cloud account and the maximum number of resources that can exist per load
balancer. The batch delete limit is the exception, since it is applied per
batch delete API request.

The system applies default values for load balancer account and/or resource
limits that can be increased by submitting a request to Cloud Support. Each
request must be approved internally before limits can be modified.

+--------------------+------------------------------------------------------------------------+---------+
| Name               | Description                                                            | Default |
+====================+========================================================================+=========+
| LOADBALANCER_LIMIT | Total number of load balancers that can be added to a Cloud account.   | 25      |
+--------------------+------------------------------------------------------------------------+---------+
| NODE_LIMIT         | Total number of nodes that can be added to a load balancer.            | 25      |
+--------------------+------------------------------------------------------------------------+---------+
| IPV6_LIMIT         | Total number of IPV6 addresses that can be added to a load balancer.   | 25      |
+--------------------+------------------------------------------------------------------------+---------+
| BATCH_DELETE_LIMIT | Total number of resources that can be listed per batch delete request. | 10      |
+--------------------+------------------------------------------------------------------------+---------+
| ACCESS_LIST_LIMIT  | Total number of network items that can be added to a load balancer.    | 100     |
+--------------------+------------------------------------------------------------------------+---------+

:ref:`Determine limits programmatically <determine-limits>` to find your
current account settings for these limits.

.. _determine-limits:

Determine limits programmatically
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Applications can programmatically determine current rate limits and absolute
limits for an account using the following URIs:

+------+-------------------------------+-----------------------------------------------------+
| Verb | URI                           | Description                                         |
+======+===============================+=====================================================+
| GET  | /limits                       | Return the current rate limits for the account.     |
+------+-------------------------------+-----------------------------------------------------+
| GET  | /loadbalancers/absolutelimits | Return the current absolute limits for the account. |
+------+-------------------------------+-----------------------------------------------------+

Error Response Code(s): loadbalancerFault (400, 500), serviceUnavailable (503),
unauthorized (401), badRequest (400), overLimit (413)

These operations do not require a request body.

**Example: List rate limits: XML response**

.. code::

    <limits xmlns="http://docs.openstack.org/common/api/v1.0">
        <rates>
            <rate uri="/v1.0/*" regex="^/1.0/.*">
                <limit
                    verb="GET"
                    value="600000"
                    remaining="426852"
                    unit="HOUR"
                    next-available="2011-02-22T19:32:43.835Z"/>
            </rate>
        </rates>
    </limits>

**Example: List rate limits: JSON response**

.. code::

    {
        "limits" : {
            "rate" : {
                "values": [
                    {
                        "uri" : "/v1.0/*",
                        "regex" : "^/1.0/.*",
                        "limit" : [
                            {
                                "verb" : "GET",
                                "value" : 600000,
                                "remaining" : 426852,
                                "unit" : "HOUR",
                                "next-available" : "2011-02-22T19:32:43.835Z"
                            }
                        ]
                    }
                ]
            }
        }
    }

**Example: List absolute limits: XML response**

.. code::

    <limits xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <absolute>
            <limit name="IPV6_LIMIT" value="25"/>
            <limit name="LOADBALANCER_LIMIT" value="25"/>
            <limit name="BATCH_DELETE_LIMIT" value="10"/>
            <limit name="ACCESS_LIST_LIMIT" value="100"/>
            <limit name="NODE_LIMIT" value="25"/>
        </absolute>
    </limits>

**Example: List absolute limits: JSON response**

.. code::

    {
        "absolute":
            [
                {"name":"IPV6_LIMIT","value":25},
                {"name":"LOADBALANCER_LIMIT","value":25},
                {"name":"BATCH_DELETE_LIMIT","value":10},
                {"name":"ACCESS_LIST_LIMIT","value":100},
                {"name":"NODE_LIMIT","value":25}
            ]
    }
