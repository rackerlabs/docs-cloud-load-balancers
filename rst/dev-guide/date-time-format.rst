.. _general-api-info-date-time-format:

====================
Date and time format
====================

The Load Balancer service uses an ISO 8601 compliant date format for the
display and consumption of date/time values.

.. _clb-dg-datetime-loadbalance:

Load Balancer service date and time format
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: 

    yyyy-MM-dd'T'HH:mm:ssZ

See the table below for a description of the date/time format codes.

May 19th, 2011 at 8:07:08 AM, GMT-5 would have the following format:

.. code::

    2011-05-19T08:07:08-05:00

.. _clb-dg-datetime-codes:

Date and time format codes
~~~~~~~~~~~~~~~~~~~~~~~~~~

+------+-----------------------------------------------------------+
| yyyy | Four digit year                                           |
+------+-----------------------------------------------------------+
| MM   | Two digit month                                           |
+------+-----------------------------------------------------------+
| DD   | Two digit day                                             |
+------+-----------------------------------------------------------+
| T    | Separator for date/time                                   |
+------+-----------------------------------------------------------+
| HH   | Two digit hour (00-23)                                    |
+------+-----------------------------------------------------------+
| mm   | Two digit minute                                          |
+------+-----------------------------------------------------------+
| ss   | Two digit second                                          |
+------+-----------------------------------------------------------+
| Z    | RFC 8601 timezone (offset from GMT). If Z is not replaced |
|      | with the offset from GMT, it indicates a 00:00 offset.    |
+------+-----------------------------------------------------------+

