.. _limits:

======
Limits
======

.. COMMENT: Adapt this topic to provide information that is relevant for
   your product.

All accounts, by default, have a preconfigured set of thresholds, or *limits*,
to manage capacity and prevent abuse of the system. The system recognizes two
kinds of limits: *rate limits* and *absolute limits*. Rate limits are thresholds
that are reset after a certain amount of time passes. Absolute limits are fixed.
Rate limits are processed via the `Repose service`_.

.. note::

    If the default limits are too low for your particular application,
    contact Rackspace Cloud support to request an increase. All requests
    require reasonable justification.

.. _Repose service: http://www.openrepose.org

.. _clb-dg-api-info-limits-ratelimits:

Rate limits
~~~~~~~~~~~

Rate limits are specified in terms of both a human-readable wildcard URI and a
machine-processable regular expression. The regular expression boundary matcher
``^`` takes effect after the root URI path. For example, the regular expression
``^/v1.0/1234/loadbalancers`` would match the ``/v1.0/1234/loadbalancers``
portion  of the following URI:

``https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers``

.. _clb-dg-api-info-limits-ratelimits-default:

.. list-table:: **Default rate limits**
   :widths: 20 40 10 20
   :header-rows: 1

   * - Method
     - URI
     - RegEx
     - Default Limit
   * - GET
     - ``/v1.0/*``
     - ``^/1.0/.*``
     - 10 per second
   * - GET
     - ``/v1.0/*``
     - ``^/1.0/.*``
     - 600 per minute
   * - POST
     - ``/v1.0/*``
     - ``^/1.0/.*``
     - 5 per second
   * - POST
     - ``/v1.0/*``
     - ``^/1.0/.*``
     - 300 per minute
   * - PUT
     - ``/v1.0/*``
     - ``^/1.0/.*``
     - 10 per second
   * - PUT
     - ``/v1.0/*``
     - ``^/1.0/.*``
     - 600 per minute
   * - DELETE
     - ``/v1.0/*``
     - ``^/1.0/.*``
     - 5 per second
   * - DELETE
     - ``/v1.0/*``
     - ``^/1.0/.*``
     - 300 per minute

Rate limits are applied in order relative to the method, going from least to
most specific. For example, although the threshold for **POST** requests to
``/v1.0/*``  is 300 per minute, you cannot send a **POST** request to ``/v1.0/*``
more than 5  times per second because the rate limit for any **POST** request
is 5 per second.  If you exceed the limits established for your account, a
``413 (Rate Control)`` HTTP  response is returned with a ``Retry-After`` header
to notify the client when it can  attempt to try again.

You can submit a request to Rackspace Support for an increase in load balancer
limits. Each request must be approved before limits can be modified. Limits can
be increased only up to the maximum limit (such as 50 nodes per load balancer).

To find your current account settings for these limits, see
:ref:`Retrieve account limits <determine-limits>`.

Absolute limits
~~~~~~~~~~~~~~~

Absolute limits specify the maximum number of load balancers that can exist
per account and the maximum number of resources that can exist per load
balancer. The batch delete limit is the exception, because it is applied per
batch delete API request.

The system applies default values for load balancer account and resource
limits that can be increased by submitting a request to Support. Each
request must be approved internally before limits can be modified.


.. list-table:: **Absolute limits**
   :widths: 20 40 10
   :header-rows: 1

   * - Name
     - Description
     - Default
   * - LOADBALANCER_LIMIT
     - Total number of load balancers that can be added to a Cloud account
     - 25
   * - NODE_LIMIT
     - Total number of nodes that can be added to a load balancer
     - 25
   * - IPV6_LIMIT
     - Total number of IPv6 addresses that can be added to a load balancer
     - 25
   * - BATCH_DELETE_LIMIT
     - Total number of resources that can be listed per batch delete request
     - 10
   * - ACCESS_LIST_LIMIT
     - Total number of network items that can be added to a load balancer
     - 100

To find your current account settings for these limits, see
:ref:`Retrieve account limits <determine-limits>`.

.. _determine-limits:

Retrieve account limits
~~~~~~~~~~~~~~~~~~~~~~~

Applications can programmatically determine current rate limits and absolute
limits for an account by using the following URIs.

.. list-table::
   :widths: 20 40 10
   :header-rows: 1

   * - Method
     - URI
     - Description
   * - GET
     - ``/limits``
     - Return the current rate limits for the account.
   * - GET
     - ``/loadbalancers/absolutelimits``
     - Return the current absolute limits for the account.

Possible error response codes for these operations are ``loadbalancerFault
(400, 500)``, ``serviceUnavailable (503)``, ``unauthorized (401)``,
``badRequest (400)``, and ``overLimit (413)``.

These operations do not require a request body.

**Example: Retrieve rate limits: XML response**

.. code::

   <limits xmlns="http://docs.openstack.org/common/api/v1.0">
       <rates>
           <rate uri="/v1.0/*" regex=".*/([0-9]+)/loadbalancers.*">
               <limit verb="GET" value="600" remaining="600" unit="MINUTE" next-available="2011-02-22T19:32:43.835Z"/>
               <limit verb="PUT" value="600" remaining="600" unit="MINUTE" next-available="2011-02-22T19:32:43.835Z"/>
               <limit verb="DELETE" value="300" remaining="300" unit="MINUTE" next-available="2011-02-22T19:32:43.835Z"/>
               <limit verb="POST" value="300" remaining="300" unit="MINUTE" next-available="2011-02-22T19:32:43.835Z"/>
           </rate>
       </rates>
   </limits>

**Example: Retrieve rate limits: JSON response**

.. code::

    {
       "limits": {
           "rate": [
               {
                   "limit": [
                       {
                           "next-available": "2011-02-22T19:32:43.835Z",
                           "remaining": 600,
                           "unit": "MINUTE",
                           "value": 600,
                           "verb": "GET"
                       },
                       {
                           "next-available": "2011-02-22T19:32:43.835Z",
                           "remaining": 600,
                           "unit": "MINUTE",
                           "value": 600,
                           "verb": "PUT"
                       },
                       {
                           "next-available": "2011-02-22T19:32:43.835Z",
                           "remaining": 300,
                           "unit": "MINUTE",
                           "value": 300,
                           "verb": "DELETE"
                       },
                       {
                           "next-available": "2011-02-22T19:32:43.835Z",
                           "remaining": 300,
                           "unit": "MINUTE",
                           "value": 300,
                           "verb": "POST"
                       }
                   ],
                   "regex": ".*/([0-9]+)/loadbalancers.*",
                   "uri": "/v1.0/*"
               }
           ]
       }
   }

**Example: Retrieve absolute limits: XML response**

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

**Example: Retrieve absolute limits: JSON response**

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
