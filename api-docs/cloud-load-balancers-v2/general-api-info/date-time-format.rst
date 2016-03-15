.. _date-time-format:

====================
Date and time format
====================

The Load Balancer service uses an ISO 8601 compliant date format for the
display and consumption of date and time values.

.. _clb-dg-datetime-loadbalance:


.. code:: 

    YYYY-MM-DD'T'hh:mm:ssZ


For example, May 19, 2016 at 8:07:08 AM, GMT-5 would have the following format:

.. code::

    2016-05-19T08:07:08-05:00

.. _clb-dg-datetime-codes:


The following table describes the date and time format codes.

**Date and time format codes**

+------+-----------------------------------------------------------+
| YYYY | Four-digit year                                           |
+------+-----------------------------------------------------------+
| MM   | Two-digit month                                           |
+------+-----------------------------------------------------------+
| DD   | Two-digit day                                             |
+------+-----------------------------------------------------------+
| T    | Separator for date and time                               |
+------+-----------------------------------------------------------+
| hh   | Two-digit hour (00-23)                                    |
+------+-----------------------------------------------------------+
| mm   | Two-digit minute                                          |
+------+-----------------------------------------------------------+
| ss   | Two-digit second                                          |
+------+-----------------------------------------------------------+
| Z    | RFC 822 time zone (offset from GMT). If Z is not replaced |
|      | with the offset from GMT, it indicates a 00:00 offset.    |
+------+-----------------------------------------------------------+

