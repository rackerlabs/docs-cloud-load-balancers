=================================================================================================
2.2. Clusters - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
=================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.2. Clusters
   :name: clusters
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/clusters
Retrieve a list of all clusters.
Support, Service Admin
**GET**
/management/clusters/``clusterId``
Retrieve a cluster by id.
Support, Service Admin
Normal Response Code(s): 200

Error Response Code(s): loadBalancerManagementFault (400, 500),
serviceUnavailable (503), unauthorized ( 401), badRequest (400),
overLimit (413)

The cluster operations are used for retrieving descriptive information
about load balancing clusters.

The **GET** response contains attributes that are generated and
immutable: ``numberOfLoadBalancingConfigurations``,
``numberOfUniqueCustomers``, ``numberOfHostMachines``, ``utilization``,
and ``status``. A cluster's attributes are calculated based on
configurations associated with this cluster.

`  <>`__
**Example 2.5. List All Clusters Response: XML**

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

                    

`  <>`__
**Example 2.6. List All Clusters Response: JSON**

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

                    

`  <>`__
**Example 2.7. List Specified Cluster Response: XML**

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

                    

`  <>`__
**Example 2.8. List Specified Cluster Response: JSON**

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

                    
