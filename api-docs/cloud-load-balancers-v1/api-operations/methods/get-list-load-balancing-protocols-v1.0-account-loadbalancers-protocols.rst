
.. _get-list-load-balancing-protocols-v1.0-account-loadbalancers-protocols:

List load balancing protocols
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{account}/loadbalancers/protocols

Lists supported load balancing protocols.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|422                       |ImmutableEntity          |This fault is returned   |
|                          |                         |when a user attempts to  |
|                          |                         |modify an item that is   |
|                          |                         |not currently in a state |
|                          |                         |that allows              |
|                          |                         |modification. For        |
|                          |                         |example, load balancers  |
|                          |                         |in a status of           |
|                          |                         |PENDING_UPDATE,BUILD, or |
|                          |                         |DELETED may not be       |
|                          |                         |modified.                |
+--------------------------+-------------------------+-------------------------+
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example List load balancing protocols: JSON response**


.. code::

    {"protocols": [
            {
                "name": "DNS_TCP",
                "port": 53
            },
            {
                "name": "DNS_UDP",
                "port": 53
            },
            {
                "name": "FTP",
                "port": 21
            },
            {
                "name": "HTTP",
                "port": 80
            },
            {
                "name": "HTTPS",
                "port": 443
            },
            {
                "name": "IMAPS",
                "port": 993
            },
            {
                "name": "IMAPv4",
                "port": 143
            },
            {
                "name": "LDAP",
                "port": 389
            },
            {
                "name": "LDAPS",
                "port": 636
            },
            {
                "name": "MYSQL",
                "port": 3306
            },
            {
                "name": "POP3",
                "port": 110
            },
            {
                "name": "POP3S",
                "port": 995
            },
            {
                "name": "SMTP",
                "port": 25
            },
            {
                "name": "TCP",
                "port": 0
            },
            {
                "name": "TCP_CLIENT_FIRST",
                "port": 0
            },
            {
                "name": "UDP",
                "port": 0
            },
            {
                "name": "UDP_STREAM",
                "port": 0
            },
            {
                "name": "SFTP",
                "port": 22
            },
            {
                "name": "TCP_STREAM",
                "port": 0
            }
        ]
    }
    


**Example List load balancing protocols: XML response**


.. code::

    <protocols xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <protocol name="DNS_TCP" port="53" />
        <protocol name="DNS_UDP" port="53" />
        <protocol name="FTP" port="21" />
        <protocol name="HTTP" port="80" />
        <protocol name="HTTPS" port="443" />
        <protocol name="IMAPS" port="993" />
        <protocol name="IMAPv4" port="143" />
        <protocol name="LDAP" port="389" />
        <protocol name="LDAPS" port="636" />
        <protocol name="MYSQL" port="3306" />
        <protocol name="POP3" port="110" />
        <protocol name="POP3S" port="995" />
        <protocol name="SMTP" port="25" />
        <protocol name="TCP" port="0" />
        <protocol name="TCP_CLIENT_FIRST" port="0" />
        <protocol name="UDP" port="0" />
        <protocol name="UDP_STREAM" port="0" />
        <protocol name="SFTP" port="22" />
        <protocol name="TCP_STREAM" port="0" />
    </protocols>
    

