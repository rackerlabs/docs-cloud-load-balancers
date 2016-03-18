.. _post-cluster-ipblocks:

Assign IP blocks to a cluster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/clusters/{clusterId}/virtualipblocks


This operation assigns a set of IP blocks to the cluster specified by ``clusterId``.


The access level for this operation is ``service admin``. 

..  note:
  
     -  In order to assign a virtual IP to the environment via the **POST** 
        operation, you must supply the address, and type attributes as part 
        of the virtualip element.

     -  To add single or multiple *specific* virtual IPs, specify the ``firstIp`` 
        and ``lastIp`` fields identically (not as a range). 



Response
""""""""""""""""

**Example: Assign IP blocks XML response**

.. code::  

    <virtualIpBlocks type="PUBLIC"
            xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
            xmlns:ns2="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <ns2:virtualIpBlock firstIp="10.0.0.5" lastIp="10.0.0.5"/>
        <ns2:virtualIpBlock firstIp="172.16.0.64" lastIp="172.16.0.64"/>
    </virtualIpBlocks>                      


**Example: Assign IP blocks JSON response**

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


