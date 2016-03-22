.. _post-create-vip:

Add virtual IPs to a load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/loadbalancers/{loadBalancerId}/virtualips


This operation enables you to provision a new PUBLIC or SERVICENET address to the specified load 
balancer. This feature is restricted because a user must justify the need for additional IP 
addresses due to IANA requirements. Thus, a support ticket is required and must be supplied in the 
request. An example of a reasonable justification would be the need to have a dedicated IP address 
for SSL termination.

The access levels for this operation are ``support`` and ``service admin``. 


To retrieve the assigned virtual IP, perform a subsequent 
``GET /loadbalancers/{loadBalancerId}/virtualips`` operation. 



Request
""""""""""""""""

**Example: Assign VIP XML request**

.. code::  

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0" type="PUBLIC">
        <ticket ticketId="1234" comment="One vip is not enough!" />
    </virtualIp>

                    


**Example: Assign VIP JSON request**

.. code::  

    {
        "type": "PUBLIC",
        "ticket": {
            "ticketId": 1234,
            "comment": "One vip is not enough!"
        }
    }
