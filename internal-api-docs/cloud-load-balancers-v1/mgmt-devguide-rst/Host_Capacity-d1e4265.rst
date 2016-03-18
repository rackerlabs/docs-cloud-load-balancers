======================================================================================================
4.1. Host Capacity - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
======================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 4.1. Host Capacity
   :name: host-capacity
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/hosts/capacityreport
Generate a capacity planning report for all load balancing hosts.
Service Admin
**GET**
/management/hosts/``hostId``/capacityreport
Generate a capacity planning report for a specified load balancing host.
Service Admin
The load balancing host capacity report provides insight into the
available capacity of a given host machine. It also supplies an
estimated runway of available capacity based on historical provisioning
activity. The historical period consists of one week, reported as
``allocatedConcurrentConnectionsInLastSevenDays``.

`  <>`__
**Example 4.1. Report Host Capacity Response: XML**

.. code::  

    <mgmt:hostCapacityReports xmlns:mgmt="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <mgmt:hostCapacityReport hostId="1"
                                 hostName="FirstBestHost"
                                 totalConcurrentConnectionCapacity="150000"/>
        <mgmt:hostCapacityReport hostId="2"
                                 hostName="SecondBestHost"
                                 totalConcurrentConnectionCapacity="150000"/>
    </mgmt:hostCapacityReports>

                    

`  <>`__
**Example 4.2. Report Host Capacity Response: JSON**

.. code::  

    {
      "hostCapacityReports": [
        {
          "totalConcurrentConnectionCapacity": 150000,
          "hostName": "FirstBestHost",
          "hostId": 1
        },
        {
          "totalConcurrentConnectionCapacity": 150000,
          "hostName": "SecondBestHost",
          "hostId": 2
        },
      ]
    }

                    
