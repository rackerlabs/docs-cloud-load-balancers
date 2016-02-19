.. _behavior:

======================================
API behavior, errors, and suggestions
======================================

This section describes the behavior of the API, errors, and provides
suggestions for working with the API.

.. _clb-dg-behavior-api:

API behavior
~~~~~~~~~~~~

The LBaaS API is considered to be asynchronous because mutable operations (that is, 
POST/PUT/DELETE) are often queued up and then handled accordingly. All successful 
asynchronous API operations have a normal response code of 202. The load balancer 
``status`` attribute is closely linked to mutable operations as it is updated depending 
on the operation and/or state of the load balancer. Please see the table below for a 
list of possible load balancer statuses. Please note that any load balancer can have 
at most one operation requested at a time. Thus, issuing parallel mutable requests 
per load balancer is not allowed and only one of the requests will be accepted should 
concurrent mutable requests be issued. Issuing concurrent non-mutable requests (that is, 
GET) is allowed.

.. _clb-dg-behavior-api-status:

Load balancer statuses
----------------------

+----------------+----------------------------------------------------+
| Name           | Description                                        |
+================+====================================================+
| ACTIVE         | The load balancer is active.                       |
+----------------+----------------------------------------------------+
| ERROR          | The load balancer is in an error state.            |
+----------------+----------------------------------------------------+
| PENDING_CREATE | The load balancer has a create pending.            |
+----------------+----------------------------------------------------+
| PENDING_DELETE | The load balancer has a deletion pending.          |
+----------------+----------------------------------------------------+
| PENDING_UPDATE | The load balancer has an update pending.           |
+----------------+----------------------------------------------------+

..  note:: 
    There is not currently a DELETED status, which means that if you use the
    API to request details on a DELETED object, you will receive a 404 Not
    Found response.


.. _clb-dg-behavior-api-errors:

API errors
~~~~~~~~~~~

Error responses contain a body with the validation error, code, and specific message 
related to the error. Use this information to diagnose what went wrong during the API 
operation.


.. _clb-dg-behavior-suggestions:

Suggestions
~~~~~~~~~~~

The most common issue an API user will come across is determining when a mutable 
action is complete. It is suggested that the API user poll the load balancer details 
(once per 5-10 seconds is recommended) in order to determine if the load balancer has 
changed back to an ``ACTIVE`` status. Once the load balancer is back in the ``ACTIVE`` 
status, another mutable operation can be accepted.
