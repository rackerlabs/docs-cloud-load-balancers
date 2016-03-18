.. _get-host-capacity-specific:

Retrieve a capacity planning report for a specific host
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/hosts/{hostId}/capacityreport


This operation generates a capacity planning report for the load balancing host specified by `hostId`.

The access level for this operation is ``service admin``. 

The load balancing host capacity report provides insight into the available capacity of a given host machine. It also supplies an estimated runway of available capacity based on historical provisioning activity. The historical period consists of one week, reported as ``allocatedConcurrentConnectionsInLastSevenDays``.  

Response
""""""""""""""""


**Example: Report host capacity for a specified host XML response**

.. code::  

    <mgmt:hostCapacityReports xmlns:mgmt="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <mgmt:hostCapacityReport hostId="1"
                                 hostName="FirstBestHost"
                                 totalConcurrentConnectionCapacity="150000"/>
        </mgmt:hostCapacityReports>

                    

**Example: Report host capacity for a specified host JSON response**

.. code::  

    {
      "hostCapacityReports": [
        {
          "totalConcurrentConnectionCapacity": 150000,
          "hostName": "FirstBestHost",
          "hostId": 1
        }
      ]
    }
