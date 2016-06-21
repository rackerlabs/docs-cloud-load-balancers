.. _persistent-connections:

Persistent connections
~~~~~~~~~~~~~~~~~~~~~~~~~~~

By default, the API supports persistent connections via `HTTP/1.1`
keepalives. All connections are kept alive unless the connection header
is set to close.

To prevent abuse, HTTP sessions have a timeout of 30 seconds before
being closed.

.. note::
    Because the server can close the connection at any time, clients should not
    rely on this default timeout behavior.
