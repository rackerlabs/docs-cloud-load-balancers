.. _listener_protocols:

=====================
Listener protocols
=====================

The following table describes the supported listener protocols.

**Listener protocols**

+-----------------------+----------------------------------------------------------------------------------+
| Name                  | Description                                                                      |
+=======================+==================================================================================+
| ``TCP``               | Basic TCP. This protocol can be used as the protocol for any TCP-based protocol. |
+-----------------------+----------------------------------------------------------------------------------+
| ``HTTP``              | This protocol load balances HTTP traffic and passes it to the members.           |
+-----------------------+----------------------------------------------------------------------------------+
| ``HTTPS``             | HTTPS passthrough. This protocol does not inspect the packet  payloads, but just |
|                       | passes them to the pool of members.                                              |
+-----------------------+----------------------------------------------------------------------------------+
| ``TERMINATED_HTTPS``  | This protocol terminates HTTPS at the load balancer. It decrypts and passes      |
|                       | unencrypted data to the pool of members.                                         |
+-----------------------+----------------------------------------------------------------------------------+

The following table describes the supported protocols for pools.

**Supported protocols for pools**

+-----------+-------------------------------------+
| Name      | Description                         |
+===========+=====================================+
| ``TCP``   | Basic L4 protocol                   |
+-----------+-------------------------------------+
| ``HTTP``  | Higher layer protocol based on TCP  |
+-----------+-------------------------------------+
| ``HTTPS`` | Encrypted protocol based on TCP     |
+-----------+-------------------------------------+


