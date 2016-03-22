.. _view-events:

==============================================
View events
==============================================

This section descriptions operation for viewing events.

The ``startDate`` and ``endDate`` parameters are optional. The results list all load 
balancer service events that occurred between the start and end dates for the 
specified account or a specified user or author. By default, the start date is 60 
days from the time of the request and the end date is the date of the request. The 
results list is inclusive for both dates. 

.. include:: methods/get-recent-events.rst
.. include:: methods/get-user-events-with-range.rst
.. include:: methods/get-account-events-with-range.rst

