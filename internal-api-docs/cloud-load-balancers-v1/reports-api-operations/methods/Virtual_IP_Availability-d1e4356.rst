================================================================================================================
4.2. Virtual IP Availability - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 4.2. Virtual IP Availability
   :name: virtual-ip-availability
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/virtualips/availabilityreport
Generate an availability report for all virtual IPs associated with any
cluster.
Service Admin
**GET**
/management/clusters/``clusterId``/virtualips/availabilityreport
Generate an availability report for all virtual IPs associated with the
specific cluster
Service Admin
The virtual IP availability report provides insight into the
availability of both public and ServiceNet IP addresses that are
provisioned to a cluster. It also supplies an estimated runway of
available capacity based on historical provisioning activity. The
historical period consists of one week, reported as
``allocatedPublicIpAddressesInLastSevenDays`` and
``allocatedServiceNetAddressesInLastSevenDays``.

`  <>`__
**Example 4.3. Report VIP Availability Response: XML**

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

                    

`  <>`__
**Example 4.4. Report VIP Availability Response: JSON**

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

                    
