.. _get-host-capacity-all:

Retrieve a capacity planning report for all hosts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /management/hosts/capacityreport


This operation generates a capacity planning report for all load balancing hosts.

The access level for this operation is ``service admin``. 


  


Response
""""""""""""""""


**Example: Report host capacity - all hosts - XML response**

.. code::  

    <mgmt:hostCapacityReports xmlns:mgmt="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <mgmt:hostCapacityReport hostId="1"
                                 hostName="FirstBestHost"
                                 totalConcurrentConnectionCapacity="150000"/>
        <mgmt:hostCapacityReport hostId="2"
                                 hostName="SecondBestHost"
                                 totalConcurrentConnectionCapacity="150000"/>
    </mgmt:hostCapacityReports>

                    

**Example: Report host capacity - all hosts - JSON response**

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

                    
