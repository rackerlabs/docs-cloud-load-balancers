.. _get-list-allowed-domains:

List allowed domains
~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/alloweddomains

Lists allowed domains.

The allowed domains are restrictions set for the allowed domain names used for
adding load balancer nodes. In order to submit a domain name as an address for
the load balancer node to add, the user must verify that the domain is valid by
using the list allowed domains call. Once verified, simply supply the domain
name in place of the address of the node in the add nodes call.

.. note::

   Currently only Rackspace-based domain names are supported.

The following table shows the possible response codes for this operation:

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

This operation does not accept a request body.

Response
--------

**Example List allowed domains: JSON response**

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

**Example List allowed domains: XML response**

.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <allowedDomains xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <allowedDomain name="rackspace.com"/>
        <allowedDomain name="randomsite.com"/>
        <allowedDomain name="org"/>
    </allowedDomains>
