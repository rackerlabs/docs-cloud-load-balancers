
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Content Caching Configuration -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Content Caching Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-content-caching-configuration-v1.0-account-loadbalancers-loadbalancerid-contentcaching.html#request>`__
`Response <get-show-content-caching-configuration-v1.0-account-loadbalancers-loadbalancerid-contentcaching.html#response>`__

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/contentcaching

Shows the current configuration of content caching.

This operation enables the user to view the current content caching configuration, enable content caching, or disable content caching.

When content caching is enabled, recently-accessed files are stored on the load balancer for easy retrieval by web clients. Content caching improves the performance of high traffic web sites by temporarily storing data that was recently accessed. While it's cached, requests for that data are served by the load balancer, which in turn reduces load off the back end nodes. The result is improved response times for those requests and less load on the web server.

For more information about content caching, see the following Knowledge Center article: `Content Caching for Cloud Load Balancers <http://www.rackspace.com/knowledge_center/content/content-caching-cloud-load-balancers>`__.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |xsd:string               |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |xsd:string *(Required)*  |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Show Content Caching Configuration: JSON response**


.. code::

    {
       "contentCaching": {
          "enabled": true
       }
    }


**Example Show Content Caching Configuration: XML response**


.. code::

    <contentCaching xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true"/>

