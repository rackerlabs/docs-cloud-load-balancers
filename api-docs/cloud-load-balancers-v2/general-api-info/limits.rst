.. _limits:

======
Limits
======

All accounts, by default, have a preconfigured set of thresholds (or limits) to manage 
capacity and prevent abuse of the system. The system recognizes two kinds of limits: 
*rate limits* and *absolute limits*. Rate limits are thresholds that are reset after a 
certain amount of time passes. Absolute limits, also called *quotas*, are fixed. 


.. note::
   You can submit a request to Rackspace Support for an increase in load balancer limits. 
   Each request must be approved before limits can be modified. Limits can be increased 
   only up to the maximum limit (such as 50 nodes per load balancer).


.. _clb-dg-api-info-limits-ratelimits:

Rate limits
~~~~~~~~~~~

Rate limits are specified in both a human-readable wild-card URI and a 
machine-processable regular expression. The regular expression boundary matcher ``^`` 
takes effect after the root URI path. For example, the regular expression 
``^/v2.0/lbaas`` matches the ``/v2.0/lbaas`` portion of the 
following URI: ``https://iad.networks.api.rackspacecloud.com/v2.0/lbaas/``.

Rate limits are processed via the `Repose service`_.


The following table shows the default rate limits for each method.

.. _clb-dg-api-info-limits-ratelimits-default:

**Default rate limits**

+--------+-------------+--------------+---------------+
| Method | URI         | Regex        | Default limit |
+========+=============+==============+===============+
| GET    | ``/v2.0/*`` | ``^/2.0/.*`` | 5 per second  |
+--------+-------------+--------------+---------------+
| GET    | ``/v2.0/*`` | ``^/2.0/.*`` | 100 per minute|
+--------+-------------+--------------+---------------+
| POST   | ``/v2.0/*`` | ``^/2.0/.*`` | 2 per second  |
+--------+-------------+--------------+---------------+
| POST   | ``/v2.0/*`` | ``^/2.0/.*`` | 25 per minute |
+--------+-------------+--------------+---------------+
| PUT    | ``/v2.0/*`` | ``^/2.0/.*`` | 5 per second  |
+--------+-------------+--------------+---------------+
| PUT    | ``/v2.0/*`` | ``^/2.0/.*`` | 50 per minute |
+--------+-------------+--------------+---------------+
| DELETE | ``/v2.0/*`` | ``^/2.0/.*`` | 2 per second  |
+--------+-------------+--------------+---------------+
| DELETE | ``/v2.0/*`` | ``^/2.0/.*`` | 50 per minute |
+--------+-------------+--------------+---------------+

Rate limits are applied in order relative to the method, going from least to most specific. 
For example, although the threshold for submitting a  **POST** request to ``/v2.0/\*`` is 
25 per minute, you cannot submit a **POST** request to ``/v2.0/\*`` more than 2 times per 
second because the rate limit for any **POST** request is 2 per second. If you exceed the 
thresholds established for your account, a 413 (Rate Control) HTTP response is returned with 
a ``Retry-After`` header to notify the client when it can attempt to try again.

To find your account's settings for these rate limits, see 
:ref:`Determine limits programmatically <determine-limits>`.





.. _Repose service: http://www.openrepose.org

Quotas
~~~~~~~~~~~~~~~

Quotas, also called absolute limits, specify the maximum number of load balancers that can exist per
Cloud account and the maximum number of resources that can exist per
load balancer. The batch delete limit is the exception, because it is
applied per batch delete API request.

The system applies default values for each quota, as shown in the following table.

+--------------------+------------------------------------------------------------------------+---------+
| Name               | Description                                                            | Default |
+====================+========================================================================+=========+
| loadbalancer       | Total number of load balancers that can be added to a Cloud account    | 10      |
+--------------------+------------------------------------------------------------------------+---------+
| listener           | Total number of listeners that can be added to a load balancer         | 20      |
+--------------------+------------------------------------------------------------------------+---------+
| pool               | Total number of pools that can be added to a listener                  | 20      |
+--------------------+------------------------------------------------------------------------+---------+
| member             | Total number of members that can be added to a load balancer           | 75      |
+--------------------+------------------------------------------------------------------------+---------+
| healthmonitor      | Total number of health monitors that can be added to a pool            | 20      |
+--------------------+------------------------------------------------------------------------+---------+

To find your account's settings for these quotas, see :ref:`Determine limits programmatically <determine-limits>`. 



.. _determine-limits:

Determine limits programmatically
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Applications can programmatically determine current limits for an account by using the following URI:

+-------+-------------------------------+-----------------------------------------------------+
| Method| URI                           | Description                                         |
+=======+===============================+=====================================================+
| GET   | /limits                       | Return the current rate limits for the account.     |
+-------+-------------------------------+-----------------------------------------------------+


Error response codes: loadbalancerFault (400, 500), serviceUnavailable (503), unauthorized (401), badRequest (400), overLimit (413)

This operation does not require a request body. Following is an example response


**Example: List rate limits JSON response**

.. code::

    {
        "limits" : {
            "rate" : {
                "values": [
                    {
                        "uri" : "/v2.0/*",
                        "regex" : "^/2.0/.*",
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


