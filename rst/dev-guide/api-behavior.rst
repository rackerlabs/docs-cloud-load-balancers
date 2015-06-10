.. _clb-dg-behavior:

==========================
API Behavior & Suggestions
==========================

.. _clb-dg-behavior-api:

API Behavior
~~~~~~~~~~~~

The LBaaS API is considered to be asynchronous because mutable operations (that is, POST/PUT/DELETE) are often queued up and then handled accordingly. All successful asynchronous API operations have a normal response code of 202. The load balancer status attribute is closely linked to mutable operations as it is updated depending on the operation and/or state of the load balancer. Please see the table below for a list of possible load balancer statuses. Please note that any load balancer can have at most one operation requested at a time. Thus, issuing parallel mutable requests per load balancer is not allowed and only one of the requests will be accepted should concurrent mutable requests be issued. Issuing concurrent non-mutable requests (that is, GET) is allowed.

.. _clb-dg-behavior-api-status:

Load Balancer Statuses
----------------------

+----------------+----------------------------------------------------+
| Name           | Description                                        |
+================+====================================================+
| ACTIVE         | The load balancer is active.                       |
+----------------+----------------------------------------------------+
| BUILD          | The load balancer is undergoing its initial build. |
+----------------+----------------------------------------------------+
| DELETED        | The load balancer is deleted.                      |
+----------------+----------------------------------------------------+
| ERROR          | The load balancer is in an error state.            |
+----------------+----------------------------------------------------+
| PENDING_DELETE | The load balancer has a deletion pending.          |
+----------------+----------------------------------------------------+
| PENDING_UPDATE | The load balancer has a pending update.            |
+----------------+----------------------------------------------------+
| SUSPENDED      | The load balancer is suspended.                    |
+----------------+----------------------------------------------------+

.. _clb-dg-behavior-suggestions:

Suggestions
~~~~~~~~~~~

The most common issue an API user will come across is determining when a mutable action is complete. It is suggested that the API user poll the load balancer details (once per 5-10 seconds is recommended) in order to determine if the load balancer has changed back to an ACTIVE status. Once the load balancer is back in the ACTIVE status, another mutable operation can be accepted.
