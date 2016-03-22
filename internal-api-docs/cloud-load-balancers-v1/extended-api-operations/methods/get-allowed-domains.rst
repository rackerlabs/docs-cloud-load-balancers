.. _get-allowed-domains:

Retrieve a list of allowed domains
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/alloweddomains  


This operation retrieves a list of allowed domains.

The allowed domains are restrictions set for allowed domain names used
for load balancer nodes. In order to submit a domain name as an address
for the load balancer node, the user must verify the domain is valid
against the List Allowed Domains call.


..  note:: 

     Currently only RackSpace-based domain names are supported.

     One FQDN (fully qualified domain name) may contain only one 'A' or
     'AAAA' record as per limitation of the system.

This operation does not require a request body.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response code             |Name                     |Description              |
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
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+




Response
""""""""""""""""

**Example: List allowed domains XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>

    <allowedDomains xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <allowedDomain name="rackspace.com"/>
        <allowedDomain name="randomsite.com"/>
        <allowedDomain name="org"/>
    </allowedDomains>

                        

**Example: List allowed domains JSON response**

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
