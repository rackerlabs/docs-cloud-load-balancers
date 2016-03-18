.. _get-cluster-vips:

Retrieve the virtual IPs for a cluster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/clusters/{clusterId}/virtualips


This operation retrieves a list of all virtual IPs that belong to the cluster specified by ``clusterId``.


The access level for this operation is ``service admin``. 



Response
""""""""""""""""


**Example: List all VIPs for a cluster XML response**

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
                    


**Example: List all VIPs for a cluster JSON response**

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