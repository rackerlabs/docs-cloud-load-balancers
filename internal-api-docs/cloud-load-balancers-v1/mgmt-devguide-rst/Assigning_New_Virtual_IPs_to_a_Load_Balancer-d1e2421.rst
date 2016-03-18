=====================================================================================================================================
3.1. Assigning New Virtual IPs to a Load Balancer - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
=====================================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.1. Assigning New Virtual IPs to a Load Balancer
   :name: assigning-new-virtual-ips-to-a-load-balancer
   :class: title

Verb
URI
Description
Access Level
**POST**
/management/loadbalancers/``loadBalancerId``/virtualips
Provision an additional virtual IP to a load balancer.
Support, Service Admin
This feature allows a user to provision a new PUBLIC or SERVICENET
address to the specified load balancer. This feature is restricted
because a user must justify the need for additional IP addresses due to
IANA requirements. Thus, a support ticket is required and must be
supplied in the request. An example of a reasonable justification would
be the need to have a dedicated IP address for SSL termination.

To retrieve the assigned virtual IP, the caller must perform a
subsequent **GET** on the /loadbalancers/loadBalancerId/virtualips URI.

`  <>`__
**Example 3.1. Assign VIP Request: XML**

.. code::  

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0" type="PUBLIC">
        <ticket ticketId="1234" comment="One vip is not enough!" />
    </virtualIp>

                    

`  <>`__
**Example 3.2. Assign VIP Request: JSON**

.. code::  

    {
        "type": "PUBLIC",
        "ticket": {
            "ticketId": 1234,
            "comment": "One vip is not enough!"
        }
    }

                    
