
.. _put-enable-content-caching-v1.0-account-loadbalancers-loadbalancerid-contentcaching:

Enable content caching
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/contentcaching

Enables or disables content caching.

This operation enables the user to view the current content caching configuration, enable content caching, or disable content caching.

When content caching is enabled, recently-accessed files are stored on the load balancer for easy retrieval by web clients. Content caching improves the performance of high traffic web sites by temporarily storing data that was recently accessed. While it's cached, requests for that data are served by the load balancer, which in turn reduces load off the back end nodes. The result is improved response times for those requests and less load on the web server.

For more information about content caching, see :how-to:`Content Caching for Cloud Load Balancers <content-caching-for-cloud-load-balancers>`.



This table shows the possible response codes for this operation:


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
^^^^^^^^^^^^




This table shows the URI parameters for the request:

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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|enabled                   |Boolean                  |If set to true, enables  |
|                          |                         |content caching. If set  |
|                          |                         |to false, disables       |
|                          |                         |content caching.         |
+--------------------------+-------------------------+-------------------------+





**Example Enable content caching: XML request**


.. code::

    <contentCaching xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true"/>


**Example Enable content caching: JSON request**


.. code::

    {
       "contentCaching":{
          "enabled":true
       }
    }


Response
^^^^^^^^^^^^^






This operation does not return a response body.




