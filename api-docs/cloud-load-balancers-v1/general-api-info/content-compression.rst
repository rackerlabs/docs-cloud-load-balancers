.. _content-compression:

===================
Content compression
===================

.. COMMENT: Adapt this topic to provide information that is relevant for your
   product.

Request and response body data can be encoded with gzip compression to
accelerate interactive performance of API requests and responses. Compression
is controlled by using the ``Accept-Encoding`` header in the request from the
client and is indicated by the ``Content-Encoding`` header in the server
response. Unless the header is explicitly set, encoding is disabled.

+-------------------+------------------+-------+
| Header type       | Name             | Value |
+===================+==================+=======+
| HTTP/1.1 Request  | Accept-Encoding  | gzip  |
+-------------------+------------------+-------+
| HTTP/1.1 Response | Content-Encoding | gzip  |
+-------------------+------------------+-------+
