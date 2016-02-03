.. _req-resp-types:

==========================
Request and response types
==========================

The Rackspace Cloud Load Balancers API supports the JSON data
serialization format. The request format is specified using the
``Content-Type`` header and is required for operations that have a
request body. The response format can be specified in requests using
either the ``Accept`` header or adding a ``.json`` extension to the
request URI. If no response format is
specified, JSON is the default. 

+--------+----------------------+-----------------+---------+
| Format | Accept Header        | Query Extension | Default |
+========+======================+=================+=========+
| JSON   | application/json     | .json           | Yes     |
+--------+----------------------+-----------------+---------+

