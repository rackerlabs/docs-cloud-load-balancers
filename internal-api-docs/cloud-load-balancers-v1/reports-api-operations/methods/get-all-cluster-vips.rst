.. _get-all-cluster-vips:

Retrieve all virtual IPs associated with any cluster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /management/virtualips/availabilityreport


This operation generates an availability report for all virtual IPs associated with any cluster.

The access level for this operation is ``service admin``. 

The virtual IP availability report provides insight into the availability 
of both public and ServiceNet IP addresses that are provisioned to a cluster. 
It also supplies an estimated runway of available capacity based on 
historical provisioning activity. The historical period consists 
of one week, reported as ``allocatedPublicIpAddressesInLastSevenDays`` 
and ``allocatedServiceNetAddressesInLastSevenDays``.   


Response
""""""""""""""""


**Example: Report VIP availability XML response**

.. code::  

    <virtualipavailabilityreports>
        <virtualipavailabilityreport
                clusterId="1"
                clusterName="My Little Cluster"
                totalPublicIpAddresses="254"
                totalServiceNetAddresses="254"
                freeAndClearPublicIpAddresses="128"
                freeAndClearServiceNetIpAddresses="128"
                publicIpAddressesInHolding="14"
                serviceNetIpAddressesInHolding="21"
                publicIpAddressesAllocatedToday="15"
                serviceNetIpAddressesAllocatedToday="4"
                allocatedPublicIpAddressesInLastSevenDays="45"
                allocatedServiceNetIpAddressesInLastSevenDays="15"
                remainingDaysOfPublicIpAddresses="50.11"
                remainingDaysOfServiceNetIpAddresses="14.41" />
    </virtualipavailabilityreports>

                    

**Example: Report VIP availability JSON response**

.. code::  

    {"virtualipavailabilityreport": {
            "clusterId": 1,
            "clusterName": "My Little Cluster",
            "totalPublicIpAddresses": 254,
            "totalServiceNetAddresses": 254,
            "freeAndClearPublicIpAddresses": 128,
            "freeAndClearServiceNetIpAddresses": 128,
            "publicIpAddressesInHolding": 14,
            "serviceNetIpAddressesInHolding": 21,
            "publicIpAddressesAllocatedToday": 15,
            "serviceNetIpAddressesAllocatedToday": 4,
            "allocatedPublicIpAddressesInLastSevenDays": 45,
            "allocatedServiceNetIpAddressesInLastSevenDays": 15,
            "remainingDaysOfPublicIpAddresses": 50.11,
            "remainingDaysOfServiceNetIpAddresses": 14.41
        }
    }

                    
