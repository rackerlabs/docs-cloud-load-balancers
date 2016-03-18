======================================================================================================================
3.14.1. Allowed Domains Operations - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
======================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.14.1. Allowed Domains Operations
   :name: allowed-domains-operations
   :class: title

Name
URI
Description
**GET**
/management/alloweddomains
View a list of allowed domains.
**GET**
/management/alloweddomains?matches={``domainname``}
For testing purposes, a domain name can be specified to verify it is
allowed by the system. The query parameter for the specified domain name
must be supplied. The response provides a list of matched domain names
in which the FQDN was found.
**PUT**
/management/alloweddomains
Add an item to the list of allowed domains.
**DELETE**
/management/alloweddomains?name={``domainname``}
Specify an item to remove from the list of allowed domains. The query
parameter for the specified domain name must be supplied.
Normal Response Code(s): 200

Error Response Code(s): loadbalancerFault (400, 500), serviceUnavailable
(503), unauthorized (401), badRequest (400), overLimit (413)

This operation does not require a request body.

The allowed domains are restrictions set for allowed domain names used
for load balancer nodes. In order to submit a domain name as an address
for the load balancer node, the user must verify the domain is valid
against the List Allowed Domains call.

The operations/management users are allowed to submit new domains to the
list of allowed domains.

..  note:: 
Note
Currently only RackSpace-based domain names are supported.

One FQDN (fully qualified domain name) may contain only one 'A' or
'AAAA' record as per limitation of the system.

`  <>`__
**Example 3.36. List Allowed Domains: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>

    <allowedDomains xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <allowedDomain name="rackspace.com"/>
        <allowedDomain name="randomsite.com"/>
        <allowedDomain name="org"/>
    </allowedDomains>

                        

`  <>`__
**Example 3.37. List Allowed Domains: JSON**

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

                        

`  <>`__
**Example 3.38. Add Allowed Domains: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>

    <allowedDomain xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" name="rackspace.com"/>

                        

`  <>`__
**Example 3.39. Add Allowed Domains: JSON**

.. code::  

    {
        "name":"rackspace.com"

    }

                        
