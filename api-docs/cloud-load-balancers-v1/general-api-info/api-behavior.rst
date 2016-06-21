.. _behavior:

======================================
API behavior and statuses
======================================

.. _clb-dg-behavior-api:


The Load Balancer API is considered to be asynchronous because mutable operations (that is,
POST, PUT, and DELETE) are often queued up and then handled accordingly. All successful
asynchronous API operations have a normal response code of 202.

The load balancer ``status`` attribute is closely linked to mutable operations because it is updated depending
on the operation or the state of the load balancer. The following table lists the possible load balancer statuses.


.. _clb-dg-behavior-api-status:

**Load balancer statuses**

+----------------+----------------------------------------------------+
| Name           | Description                                        |
+================+====================================================+
| ACTIVE         | The load balancer is active.                       |
+----------------+----------------------------------------------------+
| ERROR          | The load balancer is in an error state.            |
+----------------+----------------------------------------------------+
| PENDING_CREATE | The load balancer has a create action pending.     |
+----------------+----------------------------------------------------+
| PENDING_DELETE | The load balancer has a deletion pending.          |
+----------------+----------------------------------------------------+
| PENDING_UPDATE | The load balancer has an update action pending.    |
+----------------+----------------------------------------------------+

..  note::
    There is not currently a DELETED status, which means that if you use the
    API to request details about a DELETED object, you will receive a 404 Not
    Found response.

Any load balancer can have only one mutable operation requested at a time.
If concurrent mutable requests are issued for a load balancer, only one of
the requests is accepted. Issuing concurrent non-mutable requests (that is, GET)
is allowed.

.. _clb-dg-behavior-api-errors:

.. _clb-dg-behavior-suggestions:


To determine when a mutable operation is complete, poll the load balancer details
once every 5-10 seconds to determine if the load balancer has changed back to an
``ACTIVE`` status. After the load balancer is back in the ``ACTIVE`` status,
another mutable operation can be accepted.
