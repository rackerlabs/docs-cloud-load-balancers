.. _get-lb-state—history-report:

Retrieve a load balancer state history report
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /management/loadbalancers/{accountId}/lbstatehistory


This operation generates a load balancer state history report.

The access level for this operation is ``service admin``. 

States are collected and stored in the state history table. Requesting a GET against 
this resource will list all available state information for the account specified 
by ``accountId``.

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

This operation does not require a request body. 


Response
""""""""""""""""


**Example: Load balancer state history report XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <mgmt:loadBalancersStatusHistory xmlns:mgmt="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <mgmt:loadBalancerStatusHistory accountId="5806065" loadBalancerId="9730" status="BUILD" created="2012-04-11T15:25:49-05:00"/>
        <mgmt:loadBalancerStatusHistory accountId="5806065" loadBalancerId="9731" status="BUILD" created="2012-04-11T15:53:53-05:00"/>
        <mgmt:loadBalancerStatusHistory accountId="5806065" loadBalancerId="9731" status="ACTIVE" created="2012-04-11T15:54:05-05:00"/>
        <mgmt:loadBalancerStatusHistory accountId="5806065" loadBalancerId="9731" status="PENDING_DELETE" created="2012-04-11T15:54:32-05:00"/>
        <mgmt:loadBalancerStatusHistory accountId="5806065" loadBalancerId="9731" status="DELETED" created="2012-04-11T15:54:36-05:00"/>
    </mgmt:loadBalancersStatusHistory>
                    


**Example: Load balancer state history report JSON response**

.. code::  

    {
        "loadBalancerStatusHistories":
                [
                    {
                        "status":"BUILD",
                        "accountId":5806065,
                        "created":"2012-04-11T15:53:53-05:00",
                        "loadBalancerId":9731},
                    {
                        "status":"ACTIVE",
                        "accountId":5806065,
                        "created":"2012-04-11T15:54:05-05:00",
                        "loadBalancerId":9731},
                    {
                        "status":"PENDING_DELETE",
                        "accountId":5806065,
                        "created":"2012-04-11T15:54:32-05:00",
                        "loadBalancerId":9731},
                    {
                        "status":"DELETED",
                        "accountId":5806065,
                        "created":"2012-04-11T15:54:36-05:00",
                        "loadBalancerId":9731
                    }
                ]
    }

