.. _req-resp-types:

==========================
Request and response types
==========================

The Rackspace Cloud Load Balancers API supports the JSON data
serialization format. The request format is specified by using the
``Content-Type`` header and is required for operations that have a
request body. The response format can be specified in requests either by
using the ``Accept`` header or by adding a ``.json`` extension to the
request URI. If no response format is
specified, JSON is the default.

+--------+----------------------+-----------------+---------+
| Format | Accept header        | Query extension | Default |
+========+======================+=================+=========+
| JSON   | application/json     | .json           | Yes     |
+--------+----------------------+-----------------+---------+
