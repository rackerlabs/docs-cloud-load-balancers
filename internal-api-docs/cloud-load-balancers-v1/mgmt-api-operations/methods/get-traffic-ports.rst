.. _get-traffic-ports:

Retrieve the traffic and the ports of an IP address
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/virtualips/detailsbyip?ip=ipAddress


This operation retrieves a list of what kind of traffic (UDP or TCP) and which ports should be considered valid traffic for an IP address (in order to help mitigate DDoS attacks).


The access level for this operation is ``service admin``.

 
..  note:
  
    This operation does not officially support XML responses.


Response
""""""""""""""""


The following example assumes that the IP is bound to an
HTTPS-terminated load balancer that accepts mixed traffic.


**Example: List valid traffic for IP JSON response**

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

