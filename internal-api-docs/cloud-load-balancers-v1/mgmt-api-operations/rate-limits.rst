.. _rate-limits:

=====================
Rate limits 
=====================


Rate limiting allows a service administrator to artificially limit the number of requests that are permitted to transit a given load balancer. This action can be taken when a particular load balancer is servicing questionable traffic, the victim of a DDoS, and so forth.

To modify a rate limit, the service administrator typically makes an Auth/Identity v2.0 call to remove a user from their previous group (if needed) and then adds the user to a group with the appropriate rate limits for that user. Please refer to the Cloud Identity Admin Developer Guide at http://docs-internal.rackspace.com/auth/api/v2.0/auth-admin-devguide/content/Group_Calls.html for information about adding and removing users from groups.

Additionally, for more information on how load balancer rate limits and authentication is handled via the Repose service please see the wiki located at https://one.rackspace.com/display/compute/Cloud+Load+Balancers+Repose+Implementation. Or for more information regarding Repose directly, refer to www.openrepose.org. 

.. include:: methods/get-rate-limits.rst
