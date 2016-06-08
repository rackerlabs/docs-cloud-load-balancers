.. _protocols:

Protocols
-------------

Use the `List load balancing protocols`_ API operation to review the
protocols associated with load balanced services.

All load balancers must define the protocol of the service which is
being load balanced. The protocol selection is based on the
protocol of the back-end nodes. When configuring a load balancer, the
default port for the given protocol is selected unless otherwise
specified.

..  note::

       -  UDP-Based protocols (DNS\_UDP, UDP, and UDP\_STREAM) have the
          following limitations:

          -  They are not capable of using the Health Monitor features.

          -  Also, SSL Termination is unavailable when using UDP-based ports.

       -  Changing the protocol or port for a load balancer will disable
          session persistence.

The following table lists the load balancing protocols that can be configured
for a service using the `Load balancers`_ configuration operations.

+----------------+---------------------------------------------------------------------+
| Name           | Description                                                         |
+================+=====================================================================+
| ``DNS_TCP``    | This protocol works with IPv6 and allows your DNS server to receive |
|                | traffic using TCP port 53.                                          |
+----------------+---------------------------------------------------------------------+
| ``DNS_UDP``    | This protocol works with IPv6 and allows your DNS server to receive |
|                | traffic using UDP port 53.                                          |
+----------------+---------------------------------------------------------------------+
| ``FTP``        | The File Transfer Protocol defines how files are transported over   |
|                | the Internet. It is typically used when downloading or uploading    |
|                | files to or from web servers.                                       |
+----------------+---------------------------------------------------------------------+
| ``HTTP``       | The Hypertext Transfer Protocol defines how communications occur    |
|                | on the Internet between clients and web servers. For example, if    |
|                | you request a web page in your browser, HTTP defines how the web    |
|                | server fetches the page and returns it your browser.                |
+----------------+---------------------------------------------------------------------+
| ``HTTPS``      | The Hypertext Transfer Protocol over Secure Socket Layer (SSL)      |
|                | provides encrypted communication over the Internet. It securely     |
|                | verifies the authenticity of the web server you are communicating   |
|                | with.                                                               |
+----------------+---------------------------------------------------------------------+
| ``IMAPS``      | The Internet Message Application Protocol over Secure Socket Layer  |
|                | (SSL) defines how an email client, such as Microsoft Outlook,       |
|                | retrieves and transfers email messages with a mail server.          |
+----------------+---------------------------------------------------------------------+
| ``IMAPv2``     | Version 2 of IMAPS.                                                 |
+----------------+---------------------------------------------------------------------+
| ``IMAPv3``     | Version 3 of IMAPS.                                                 |
+----------------+---------------------------------------------------------------------+
| ``IMAPv4``     | Version 4, the current version of IMAPS.                            |
+----------------+---------------------------------------------------------------------+
| ``LDAP``       | The Lightweight Directory Access Protocol provides access to        |
|                | distributed directory information services over the Internet. This  |
|                | protocol is typically used to access a large set of hierarchical    |
|                | records, such as corporate email or a telephone directory.          |
+----------------+---------------------------------------------------------------------+
| ``LDAPS``      | The Lightweight Directory Access Protocol over Secure Socket Layer  |
|                | (SSL).                                                              |
+----------------+---------------------------------------------------------------------+
| ``MYSQL``      | This protocol allows communication with MySQL, an open source       |
|                | database management system.                                         |
+----------------+---------------------------------------------------------------------+
| ``POP3``       | The Post Office Protocol is one of the two most common protocols    |
|                | for communication between email clients and email servers.          |
|                | Version 3 is the current standard of POP.                           |
+----------------+---------------------------------------------------------------------+
| ``POP3S``      | Post Office Protocol over Secure Socket Layer.                      |
+----------------+---------------------------------------------------------------------+
| ``SFTP``       | The SSH File Transfer Protocol is a secure file transfer and        |
|                | management protocol. This protocol assumes the files are using a    |
|                | secure channel, such as SSH, and that the identity of the client    |
|                | is available to the protocol.                                       |
+----------------+---------------------------------------------------------------------+
| ``SMTP``       | The Simple Mail Transfer Protocol is used by electronic mail        |
|                | servers to send and receive email messages. Email clients use this  |
|                | protocol to relay messages to another computer or web server, but   |
|                | use IMAP or POP to send and receive messages.                       |
+----------------+---------------------------------------------------------------------+
| ``TCP``        | The Transmission Control Protocol is a part of the Transport Layer  |
|                | protocol and is one of the core protocols of the Internet Protocol  |
|                | Suite. It provides a reliable, ordered delivery of a stream of      |
|                | bytes from one program on a computer to another program on another  |
|                | computer. Applications that require an ordered and reliable         |
|                | delivery of packets use this protocol.                              |
+----------------+---------------------------------------------------------------------+
|``TCP_CLIE``    | This protocol is similar to TCP, but is more efficient when a       |
|``(TCP_CLIENT_``| client is expected to write the data first.                         |
|``FIRST)``      |                                                                     |
+----------------+---------------------------------------------------------------------+
| ``TCP_STREAM`` | TCP Streaming allows either the client or server to send the first  |
|                | message when a connection is established. This option is for        |
|                | protocols where there is no request-response semantic. Either side  |
|                | of the connection can write the first message, with no response     |
|                | being necessarily required or expected.                             |
+----------------+---------------------------------------------------------------------+
| ``UDP``        | The User Datagram Protocol provides a datagram service that         |
|                | emphasizes speed over reliability, It works well with applications  |
|                | that provide security through other measures.                       |
+----------------+---------------------------------------------------------------------+
|``UDP_STRE``    | This protocol is designed to stream media over networks and is      |
|``(UDP_STREAM)``| built on top of UDP.                                                |
+----------------+---------------------------------------------------------------------+


.. include:: methods/get-list-load-balancing-protocols-v1.0-account-loadbalancers-protocols.rst
