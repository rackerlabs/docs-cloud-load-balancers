.. _get-account-alerts:

Retrieve alerts for an account
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/management/alerts/account?account={accountId}&account={accountId} &startDate=Date&endDate=Date&showStackTrace=true


This operation retrieves all alerts, if any, for the specified account.

When getting alerts based on account IDs, you can specify any number of accounts as separate query parameters. You may also include the stack trace with the final query parameter. 

The access levels for this operation are ``support`` and  ``service admin``. 





