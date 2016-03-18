.. _get-specific-cluster:

Retrieve a specific cluster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/clusters/{clusterId}


This operation retrieves descriptive information about the cluster that is specified by ``clusterId``.

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






**Example: List specified cluster XML response**

.. code::  

    <cluster
          id="1"
          name="Cluster Alpha"
          description="The best cluster, ever."
          dataCenter="DFW"
          numberOfLoadBalancingConfigurations="410"
          numberOfUniqueCustomers="348"
          numberOfHostMachines="8"
          utilization="59%"
          status="ACTIVE"/>

                    


**Example: List specified cluster JSON response**

.. code::  

    {"cluster": {
            "id": 1,
            "name": "Cluster Alpha",
            "description": "The best cluster, ever.",
            "dataCenter": "DFW",
            "numberOfLoadBalancingConfigurations": 410,
            "numberOfUniqueCustomers": 348,
            "numberOfHostMachines": 8,
            "utilization": "59%",
            "status": "INACTIVE"
        }
    }

                    
