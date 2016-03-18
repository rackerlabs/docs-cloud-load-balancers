==============================================================================================================================================
2.6. Associations Between Load Balancers and Host Machines - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
==============================================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.6. Associations Between Load Balancers and Host
   Machines
   :name: associations-between-load-balancers-and-host-machines
   :class: title

Verb
URI
Description
Access Level
**PUT**
/management/loadbalancers/``loadBalancerId``/sticky
Make the specified load balancer sticky.
Support, Service Admin
**DELETE**
/management/loadbalancers/``loadBalancerId``/sticky
Turn off the "sticky" flag on the specified load balancer.
Support, Service Admin
**GET**
/management/loadbalancers/``loadBalancerId``/host
Get the host assignment(s) for a specified load balancer.
Service Admin
**PUT**
/management/loadbalancers/reassignhosts
Update the host assignment(s) for a list of load balancers.
Service Admin
Service administrators may re-assign a load balancer to a different host
machine within the same cluster. This action can be taken if capacity
warrants it or if a particular configuration needs to be isolated from
others within the environment. Both active and failover hosts may be
changed.

Additionally, this operation allows for a service administrator to
define a load balancer's host configurations as being "sticky", which
will prohibit the system from automatically moving this configuration
between hosts to balance the host performance.

A load balancer that is defined as being ACTIVE on multiple hosts will
allow the load balancer host machines to service traffic for a single
VIP across multiple systems. This is an advanced feature that should be
used cautiously as it can potentially amplify DDoS and other types of
malicious traffic.

`  <>`__
**Example 2.21. Update Host Assignment Response: XML**

.. code::  

    <host xmlns="http://docs.rackspacecloud.com/loadbalancers/api/management/v1.0"
            id="1"
            name="host1"
            clusterId="1"
            coreDeviceId="10"
            maxConcurrentConnections="1500"
            managementIp="10.2.2.3"
            trafficManagerName="ztm-n01.dev.lbaas.rackspace.com"
            managementSoapInterface="https://173.203.239.70:9090/soap" />

                    

`  <>`__
**Example 2.22. Update Host Assignment Response: JSON**

.. code::  

    {"host": [
            {
                "id": 1,
                "name": "host1",
                "clusterId": 1,
                "coreDeviceId": 10,
                "maxConcurrentConnections": 1500,
                "managementIp": "10.2.2.3",
                "trafficManagerName": "ztm-n01.dev.lbaas.rackspace.com",
                "managementSoapInterface": "https://173.203.239.70:9090/soap"
            }
        ]
    }

                    

`  <>`__
**Example 2.23. Update Host Assignment for Multiple Load Balancers with
Specified Host Request: XML**

.. code::  

    <loadBalancers xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
       <loadBalancer id="49" >
         <host id="2"/>
       </loadBalancer>
    </loadBalancers>

                    

`  <>`__
**Example 2.24. Update Host Assignment for Multiple Load Balancers with
Specified Host Request: JSON**

.. code::  

    {"loadBalancers": [
            {
                "host": {
                    "id": 2
                },
                "id": 1
            }
        ]
    }

                    

`  <>`__
**Example 2.25. Update Host Assignment for Multiple Load Balancers with
Host Chosen by Algorithm Request: XML**

.. code::  

    <loadBalancers xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
       <loadBalancer id="1" />
    </loadBalancers>

                    

`  <>`__
**Example 2.26. Update Host Assignment for Multiple Load Balancers with
Host Chosen by Algorithm Request: JSON**

.. code::  

    {"loadBalancers": [
            {
                "id": 1
            }
        ]
    }

                    
