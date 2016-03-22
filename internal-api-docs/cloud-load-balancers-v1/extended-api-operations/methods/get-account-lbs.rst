.. _get-account-lbs:

Retrieve load balancers by account
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/accounts/{accountId}/loadbalancers 


This operation retrieves a list of load balancers for the specified account.



The access levels for this operation are ``support`` and  ``service admin``. 

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

**Example: List account load balancers XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <ns2:accountLoadBalancers xmlns:ns2="http://docs.openstack.org/loadbalancers/api/management/v1.0" accountId="5805065">
        <ns2:accountLoadBalancer loadBalancerId="321" loadBalancerName="a-new-loadbalancer" clusterId="1" clusterName="DEV"
                                  protocol="HTTP" status="BUILD"/>
        <ns2:accountLoadBalancer loadBalancerId="322" loadBalancerName="a-new-loadbalancer" clusterId="1" clusterName="DEV"
                                  protocol="HTTP" status="ACTIVE"/>
    </ns2:accountLoadBalancers>

                    


**Example: List account load balancers JSON response**

.. code::  

    {"accountId":5805065,"accountLoadBalancers":[
        {
            "protocol":"HTTP",
            "status":"BUILD",
            "loadBalancerId":321,
            "loadBalancerName":"a-new-loadbalancer",
            "clusterId":1,
            "clusterName":"DEV"
        },
        {
            "protocol":"HTTP",
            "status":"ACTIVE",
            "loadBalancerId":322,
            "loadBalancerName":"a-new-loadbalancer",
            "clusterId":1,
            "clusterName":"DEV"
        }
    ]}