=============================================================================
List Allowed Domains -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Allowed Domains
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_allowed_domains_v1.0_account_loadbalancers_alloweddomains.rst#request>`__
`Response <GET_list_allowed_domains_v1.0_account_loadbalancers_alloweddomains.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/alloweddomains

Lists allowed domains.

The allowed domains are restrictions set for the allowed domain names used for adding load balancer nodes. In order to submit a domain name as an address for the load balancer node to add, the user must verify that the domain is valid by using the list allowed domains call. Once verified, simply supply the domain name in place of the address of the node in the add nodes call.

Currently only Rackspace-based domain names are supported.



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








Response
^^^^^^^^^^^^^^^^^^





**Example List Allowed Domains: JSON request**


.. code::

    
    {
        "allowedDomains":[
            {"allowedDomain":{
                "name":"rackspace.com"}},
    
            {"allowedDomain":{
                "name":"randomsite.org"}},
    
            {"allowedDomain":{
                "name":"org"}}
        ]
    }


**Example List Allowed Domains: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    
    <allowedDomains xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <allowedDomain name="rackspace.com"/>
        <allowedDomain name="randomsite.com"/>
        <allowedDomain name="org"/>
    </allowedDomains>

