=============================================================================
Show Content Caching Configuration -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Content Caching Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_content_caching_configuration_v1.0_account_loadbalancers_loadbalancerid_contentcaching.rst#request>`__
`Response <GET_show_content_caching_configuration_v1.0_account_loadbalancers_loadbalancerid_contentcaching.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/contentcaching

Shows the current configuration of content caching.

This operation enables the user to view the current content caching configuration, enable content caching, or disable content caching.

When content caching is enabled, recently-accessed files are stored on the load balancer for easy retrieval by web clients. Content caching improves the performance of high traffic web sites by temporarily storing data that was recently accessed. While it's cached, requests for that data are served by the load balancer, which in turn reduces load off the back end nodes. The result is improved response times for those requests and less load on the web server.

For more information about content caching, see the following Knowledge Center article: `Content Caching for Cloud LoadBalancers <http://www.rackspace.com/knowledge_center/content/content-caching-cloud-load-balancers>`__.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|413                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
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





**Example Show Content Caching Configuration: JSON request**


.. code::

    {
       "contentCaching": {
          "enabled": true
       }
    }


**Example Show Content Caching Configuration: XML request**


.. code::

    <contentCaching xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true"/>

