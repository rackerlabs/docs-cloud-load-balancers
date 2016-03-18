.. _get-all-clusters:

Retrieve all clusters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/clusters


This operation retrieves descriptive information about all the clusters associated with the load balancer.

The access levels for this operation are ``support`` and ``service admin``. 


The **GET** response contains attributes that are generated and
immutable: ``numberOfLoadBalancingConfigurations``,
``numberOfUniqueCustomers``, ``numberOfHostMachines``, ``utilization``,
and ``status``. A cluster's attributes are calculated based on
configurations associated with this cluster.


The following table shows the possible response codes for this operation.

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



**Example: List all clusters XML response**

.. code::  

    <clusters xmlns="http://docs.openstack.org/loadbalancers/api/mgmt/v1.0">
       <cluster
          id="1"
          name="Cluster Alpha"
          description="The best cluster, ever."
          dataCenter="DFW"
          numberOfLoadBalancingConfigurations="410"
          numberOfUniqueCustomers="348"
          numberOfHostMachines="8"
          utilization="59%"
          status="ACTIVE" />
       <cluster
          id="2"
          name="Cluster Beta"
          description="The second best cluster, ever."
          dataCenter="ORD"
          numberOfLoadBalancingConfigurations="580"
          numberOfUniqueCustomers="490"
          numberOfHostMachines="8"
          utilization="76%"
          status="INACTIVE" />
    </clusters>

                    


**Example: List all clusters JSON response**

.. code::  

    {"clusters": [
            {
                "id": 1,
                "name": "Cluster Alpha",
                "description": "The best cluster, ever.",
                "dataCenter": "DFW",
                "numberOfLoadBalancingConfigurations": 410,
                "numberOfUniqueCustomers": 348,
                "numberOfHostMachines": 8,
                "utilization": "59%",
                "status": "INACTIVE"
            },
            {
                "id": 2,
                "name": "Cluster Beta",
                "description": "The second best cluster, ever.",
                "dataCenter": "DFW",
                "numberOfLoadBalancingConfigurations": 580,
                "numberOfUniqueCustomers": 490,
                "numberOfHostMachines": 8,
                "utilization": "76%",
                "status": "INACTIVE"
            }
        ]
    }

                    