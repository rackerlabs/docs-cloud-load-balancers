.. _overview:

========
Overview
========

.. _overview-audience:

Intended audience
~~~~~~~~~~~~~~~~~

This guide is intended for software developers who want to create applications using the Rackspace Cloud Load Balancers API. It assumes the reader has a general understanding of load balancing concepts and is familiar with:

-  ReSTful web services

-  HTTP/1.1 conventions

-  JSON and/or XML serialization formats

-  Atom syndication format

.. _clb-dg-overview-dochistory:

Document change history
~~~~~~~~~~~~~~~~~~~~~~~

This version of the Developer Guide replaces and obsolesces all previous versions. The most recent changes are described in the table below:

.. _clb-dg-overview-dochistory-14072015:

July 14, 2015
--------------

Removed information about node status going from OFFLINE to ONLINE after changing
condition to ENABLED from DRAINING until that feature is working correctly again in section 4.4.2 "Add
node".

.. _clb-dg-overview-dochistory-08072015:

July 8, 2015
--------------

Removed information about setting the maxConnections body parameter to zero to enable
unlimited simultaneous connections until that feature is working correctly again in section 4.12.2 "Create
or update connection throttling configuration".

.. _clb-dg-overview-dochistory-07052015:

May 7, 2015
--------------

Added information for HTTP and HTTPS health monitors for attribute bodyRegex in Section 4.9, “Monitors”.

.. _overview-additional-resources:

Additional resources
~~~~~~~~~~~~~~~~~~~~

You can download the most current version of this document from the Rackspace Cloud website at http://docs.rackspace.com/.

For information about getting started using Cloud Load Balancers and Cloud Servers, refer to Getting Started with Rackspace Cloud Load Balancers and Servers at http://docs.rackspace.com/.

For more details about the Rackspace Cloud Load Balancer service, refer to http://www.rackspace.com/cloud/load-balancing/. This site also offers links to Rackspace official support channels, including knowledge base articles, forums, phone, chat, and email.

You can also follow updates and announcements via twitter at http://www.twitter.com/Rackspace.

.. _overview-pricing:

Pricing and service level
~~~~~~~~~~~~~~~~~~~~~~~~~

Cloud Load Balancers is part of the Rackspace Cloud and your use through the API is billed as per the pricing schedule at http://www.rackspace.com/cloud/load-balancing/pricing/.

The Service Level Agreement (SLA) for Cloud Load Balancers is available at http://www.rackspace.com/information/legal/cloud/sla#cloud_load_balancers.