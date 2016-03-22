.. _get-usage-all-accounts-single-day:

Retrieve usage for all accounts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/accounts/billing?startTime=YYYY-MM-DDT HH:mm:ss&endTime=YYYY-MM-DDT HH:mm:ss  


This operation retrieves usage for all accounts for a *single* day.

The date parameters follow the ``YYYY-MM-DD`` date format. Note that usage is retained for a maximum of 
90 days. The ``startTime`` and ``endTime`` parameters are required for the call. 


The access levels for this operation are ``support``, ``service admin``, and ``billing``. 

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

**Example: List account load balancers usage XML response**

.. code::  

    <accountBilling xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" accountId="1106">
        <accountUsage>
            <accountUsageRecord numLoadBalancers="2" numPublicVips="1" 
                numServicenetVips="0" startTime="2010-12-01T14:09:14-06:00"/>
        </accountUsage>
        <loadBalancerUsage loadBalancerId="66" loadBalancerName="My first loadbalancer">
            <loadBalancerUsageRecord id="394" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="1"
                numPolls="32" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T16:23:54-06:00"
                     vipType="PUBLIC"/>
            <loadBalancerUsageRecord id="473" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="2"
                numPolls="5" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T12:36:30-06:00"
                     vipType="PUBLIC"/>
            <loadBalancerUsageRecord id="474" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="2"
                numPolls="5" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T12:36:30-06:00"
                     vipType="PUBLIC"/>
            <loadBalancerUsageRecord id="475" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="2"
                numPolls="5" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T12:36:30-06:00"
                     vipType="PUBLIC"/>
        </loadBalancerUsage>
        <loadBalancerUsage loadBalancerId="77" loadBalancerName="My second loadbalancer">
            <loadBalancerUsageRecord id="394" averageNumConnections="0.0" 
                incomingTransfer="0" outgoingTransfer="0" numVips="1"
                numPolls="32" startTime="2010-12-21T12:32:07-06:00" 
                endTime="2010-12-21T16:23:54-06:00"
                     vipType="PUBLIC"/>
            <loadBalancerUsageRecord id="473" averageNumConnections="0.0"
                    incomingTransfer="0" outgoingTransfer="0" numVips="2" numPolls="5"
                    startTime="2010-12-21T12:32:07-06:00"
                    endTime="2010-12-21T12:36:30-06:00"
                     vipType="PUBLIC"/>
        </loadBalancerUsage>
    </accountBilling>

                    


