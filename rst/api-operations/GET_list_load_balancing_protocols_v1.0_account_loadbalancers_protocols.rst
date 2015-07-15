=============================================================================
List Load Balancing Protocols -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Load Balancing Protocols
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_load_balancing_protocols_v1.0_account_loadbalancers_protocols.rst#request>`__
`Response <GET_list_load_balancing_protocols_v1.0_account_loadbalancers_protocols.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/protocols

Lists supported load balancing protocols.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|413                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |xsd:string               |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example List Load Balancing Protocols: JSON request**


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
    


**Example List Load Balancing Protocols: XML request**


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
    

