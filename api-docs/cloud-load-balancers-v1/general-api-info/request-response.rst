.. _req-resp-types:

==========================
Request and response types
==========================

.. COMMENT: Adapt this topic to provide information that is relevant for your
   product.

The Rackspace Cloud Load Balancers API supports both the JSON and XML data
serialization formats.

The request format is specified by using the ``Content-Type`` header and is
required for operations that have a request body.

The response format can be specified in requests either by using the ``Accept``
header or adding an ``.xml`` or ``.json`` extension to the request URI. A
response  can be serialized using a format that is different from the request.
If no response format is specified, JSON is the default. If conflicting formats
are specified by using both an ``Accept`` header and a query extension, the
query extension takes precedence.

Some operations support an Atom representation that can be used to efficiently
determine when the state of services has changed.

.. list-table:: **JSON and XML response formats**
   :widths: 10 20 10 10
   :header-rows: 1

   * - Format
     - Accept header
     - Query extension
     - Default
   * - JSON
     - application/json
     - .json
     - Yes
   * - XML
     - application/xml
     - .xml
     - No
   * - Atom
     - application/atom+xml
     - .atom
     - No
