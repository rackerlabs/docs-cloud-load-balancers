===================================================================================================================
3.3. Suspending a Load Balancer - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
===================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.3. Suspending a Load Balancer
   :name: suspending-a-load-balancer
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/loadbalancers/``loadBalancerId``/suspension
Retrieve the current suspension information, if any, for the load
balancer.
Support, Service Admin
**POST**
/management/loadbalancers/``loadBalancerId``/suspension
Issue an immediate service suspension for a load balancer.
Support, Service Admin
**DELETE**
/management/loadbalancers/``loadBalancerId``/suspension
Remove the suspension for a load balancer.
Support, Service Admin
This feature allows for a caller to suspend and or unsuspend the
specified load balancer. In order to suspend a load balancer, the caller
must supply a reason, the ticket issuer (user) and a ticket identifier,
which can be viewed by other users with support and service admin access
levels.

If a caller requests suspension details for an unsuspended load
balancer, an empty suspension element (<suspension />) will be returned.

..  note:: 
Note
While customers are not permitted to delete suspended load balancers, a
user with elevated permissions may do so by issuing a **DELETE** request
against the /loadbalancers/loadBalancerId URI.

`  <>`__
**Example 3.3. Add Suspension Request: XML**

.. code::  

    <suspension xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            reason="Non-payment"
            user="bob">
        <ticket ticketId="1234" comment="Late payment" />
    </suspension>

                    

`  <>`__
**Example 3.4. Add Suspension Request: JSON**

.. code::  

    {
        "reason": "Non-payment",
        "user": "bob",
        "ticket": {
            "ticketId": 1234,
            "comment": "Late Payment"
        }
    }

                    

`  <>`__
**Example 3.5. List Suspension Response: XML**

.. code::  

    <suspension xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.00"
            reason="User suspected of fraud"
            user="jdoe" />

                    

`  <>`__
**Example 3.6. List Suspension Response: JSON**

.. code::  

    {
        "reason": "User suspected of fraud",
        "user": "jdoe"
    }

                    
