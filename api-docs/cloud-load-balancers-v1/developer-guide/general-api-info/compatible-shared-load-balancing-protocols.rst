.. _compatible-shared-load-balancing-protocols:


Compatible shared load balancing protocols
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Load balancers utilizing shared Virtual IPs must select *unique* ports unless the load balancer protocols used are designed to work together on the same port. This section provides information on the-compatible load balancer protocols that are designed to share UDP and TCP based protocols on the same port.

.. note::
    Only a select set of protocols are allowed to share the same port across shared load balancers.

See below for the descriptions of these protocols.

.. _clb-dg-compatible-dns:

DNS-compatible load balancing protocols
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+--------------+-----------------------------------------------------------------------+
| Name         | Description                                                           |
+==============+=======================================================================+
| ``DNS_TCP``  | This protocol works with IPv6 and allows your DNS server to receive   |
|              | traffic using TCP port 53.                                            |
+--------------+-----------------------------------------------------------------------+
| ``DNS_UDP``  | This protocol works with IPv6 and allows your DNS server to receive   |
|              | traffic using UDP port 53.                                            |
+--------------+-----------------------------------------------------------------------+

.. note::
    The TCP and UDP protocols listed above are compatible and good for load balancing DNS based applications. These cannot be combined with the TCP and UDP protocols listed  below.

The TCP and UDP protocols listed below are compatible for sharing TCP and UDP based protocols on the same port. These protocols can be interchanged to achieve the proper setup for the user's TCP/UDP based application.

.. _clb-dg-compatible-tcp:

TCP-compatible load balancing protocols
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+--------------------+-----------------------------------------------------------------------+
| Name               | Description                                                           |
+====================+=======================================================================+
| ``TCP``            | The Transmission Control Protocol (TCP) is a part of the Transport    |
|                    | Layer Protocol and is one of the core protocols of the Internet       |
|                    | Protocol Suite. It provides a reliable, ordered delivery of a stream  |
|                    | of bytes from one program on a computer to another program on another |
|                    | computer. Applications that require an ordered and reliable delivery  |
|                    | of packets use this protocol.                                         |
+--------------------+-----------------------------------------------------------------------+
|``TCP_CLIENT_FIRST``| This protocol is similar to TCP, but is more efficient when a client  |
|                    | is expected to write the data first.                                  |
+--------------------+-----------------------------------------------------------------------+

.. _clb-dg-compatible-udp:

UDP-compatible load balancing protocols
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+--------------+-----------------------------------------------------------------------+
| Name         | Description                                                           |
+==============+=======================================================================+
| ``UDP``      | The User Datagram Protocol (UDP) provides a datagram service that     |
|              | emphasizes speed over reliability. It works well with applications    |
|              | that provide security through other measures.                         |
+--------------+-----------------------------------------------------------------------+
|``UDP_STREAM``| This protocol is designed to stream media over networks and is built  |
|              | on top of UDP.                                                        |
+--------------+-----------------------------------------------------------------------+
