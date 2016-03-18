====================================================================================================
2.4. Virtual IPs - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
====================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.4. Virtual IPs
   :name: virtual-ips
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/virtualips
Retrieve a list of all virtual IPs associated with the region.
Service Admin
**GET**
/management/clusters/``clusterId``/virtualips
Retrieve a list of all virtual IPs associated with a cluster.
Service Admin
**GET**
/management/loadbalancers/``loadBalancerId``/virtualips
Retrieve a list of all virtual IPs associated with a load balancer.
Service Admin
**GET**
/management/virtualips/detailsbyip?ip=ipAddress
Retrieve a list of what kind of traffic (UDP or TCP) and which ports
should be considered valid traffic for an IP address (in order to help
mitigate DDoS attacks).

..  note:: 
Note
This operation does not officially support XML responses.

Service Admin
**POST**
/management/clusters/``clusterId``/virtualipblocks
Assign a set of IP blocks to the cluster.
Service Admin
**DELETE**
/management/virtualips/``virtualIpId``
Remove the specified virtual IP from the cluster.
Service Admin
The virtual IP operations allow the caller to view, create, and remove
virtual IPs from an environment. Virtual IPs are automatically assigned
to every newly created load balancer and can be added on-demand by a
support or service administrator with proper justification. Management
of the service requires blocks of IP addresses to be allocated from
time-to-time to ensure availability for customers.

In order to assign a virtual IP to the environment via the **POST**
operation, the caller must supply the address, and type attributes as
part of the virtualip element. A sample **POST** request can be found
below.

..  note:: 
Notes

-  In the event a virtual IP must be removed from the cluster, the
   **DELETE** operation can be used; however, to delete a virtual IP it
   must not have a load balancer associated to it.

-  To add single or multiple *specific* virtual IPs, simply specify the
   firstIp and lastIp fields identically (not as a range).

`  <>`__
**Example 2.15. List All VIPs Within Cluster Response: XML**

.. code::  

    <virtualips>
       <virtualip id="411"
          loadBalancerId="1"
          clusterId="1"
          address="98.128.33.1"
          type="PUBLIC" />
       <virtualip
          id="501"
          clusterId="1"
          address="10.41.133.4"
          type="SERVICENET" />
    </virtualips>

                    

`  <>`__
**Example 2.16. List All VIPs Within Cluster Response: JSON**

.. code::  

    {"virtualips": {
            "virtualip": [
                {
                    "id": 411,
                    "loadBalancerId": 1,
                    "clusterId": 1,
                    "address": "98.128.33.1",
                    "type": "PUBLIC"
                },
                {
                    "id": 501,
                    "loadBalancerId": 1,
                    "clusterId": 1,
                    "address": "10.41.133.4",
                    "type": "SERVICENET"
                }
            ]
        }
    }

                    

`  <>`__
**Example 2.17. Assign IP Blocks Response: XML**

.. code::  

    <virtualIpBlocks type="PUBLIC"
            xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
            xmlns:ns2="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <ns2:virtualIpBlock firstIp="10.0.0.5" lastIp="10.0.0.5"/>
        <ns2:virtualIpBlock firstIp="172.16.0.64" lastIp="172.16.0.64"/>
    </virtualIpBlocks>

                    

`  <>`__
**Example 2.18. Assign IP Blocks Response: JSON**

.. code::  

    {"virtualIpBlocks": [
            {
                "firstIp": "10.0.0.5",
                "lastIp": "10.0.0.5"
            },
            {
                "firstIp": "172.16.0.64",
                "lastIp": "172.16.0.64"
            },
            {
                "firstIp": "192.168.0.3",
                "lastIp": "192.168.0.3"
            }
        ],
        "type": "SERVICENET"
    }

                    

The following example assumes that the IP is bound to an
HTTPS-terminated load balancer that accepts mixed traffic.

`  <>`__
**Example 2.19. List Valid Traffic for IP: JSON**

.. code::  

    {
        "protocols": [
            {
                "port": 80,
                "protocol": "TCP"
            },
            {
                "port": 443,
                "protocol": "TCP"
            }
        ],
        "accountId": 123456,
        "virtualIpId": 7890
    }

                    

The following example shows the case where the IP is not bound to a load
balancer.

`  <>`__
**Example 2.20. List Valid Traffic for IP (not bound): JSON**

.. code::  

    {}
                    
