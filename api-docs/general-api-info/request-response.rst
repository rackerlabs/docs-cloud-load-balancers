.. _req-resp-types:

==========================
Request and response types
==========================

The Rackspace Cloud Load Balancers API supports both the JSON and XML data serialization formats. The request format is specified using the `Content-Type` header and is required for operations that have a request body. The response format can be specified in requests using either the `Accept` header or adding an `.xml` or `.json` extension to the request URI. Note that it is possible for a response to be serialized using a format different from the request. If no response format is specified, JSON is the default. If conflicting formats are specified using both an `Accept` header and a query extension, the query extension takes precedence.

Some operations support an Atom representation that can be used to efficiently determine when the state of services has changed.

**JSON and XML response formats**

+--------+----------------------+-----------------+---------+
| Format | Accept Header        | Query Extension | Default |
+========+======================+=================+=========+
| JSON   | application/json     | .json           | Yes     |
+--------+----------------------+-----------------+---------+
| XML    | application/xml      | .xml            | No      |
+--------+----------------------+-----------------+---------+
| Atom   | application/atom+xml | .atom           | No      |
+--------+----------------------+-----------------+---------+
