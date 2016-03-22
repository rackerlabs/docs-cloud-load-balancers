.. _put-add-allowed-domain:

Add an item to the allowed domains
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: 

   PUT  /management/alloweddomains  


This operations adds an item to the list of allowed domains.



..  note:: 

     Currently only RackSpace-based domain names are supported.

     One FQDN (fully qualified domain name) may contain only one 'A' or
     'AAAA' record as per limitation of the system.



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


Request
""""""""""""""""

**Example: Add allowed domains XML request**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>

    <allowedDomain xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" name="rackspace.com"/>

                        


**Example: Add allowed domains JSON request**

.. code::  

    {
        "name":"rackspace.com"

    }

