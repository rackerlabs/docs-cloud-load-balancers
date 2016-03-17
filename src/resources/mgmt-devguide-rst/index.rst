=================================================================================
Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
=================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: 
   :name: section
   :class: author

Rackspace Cloud

API v1.0

©
2016
Rackspace US, Inc.

` <>`__
This document is intended for software developers interested in
developing service management applications using the Rackspace Cloud
Load Balancers Application Program Interface (API). The document is for
informational purposes only and is provided “AS IS.”

RACKSPACE MAKES NO REPRESENTATIONS OR WARRANTIES OF ANY KIND, EXPRESS OR
IMPLIED, AS TO THE ACCURACY OR COMPLETENESS OF THE CONTENTS OF THIS
DOCUMENT AND RESERVES THE RIGHT TO MAKE CHANGES TO SPECIFICATIONS AND
PRODUCT/SERVICES DESCRIPTION AT ANY TIME WITHOUT NOTICE. RACKSPACE
SERVICES OFFERINGS ARE SUBJECT TO CHANGE WITHOUT NOTICE. USERS MUST TAKE
FULL RESPONSIBILITY FOR APPLICATION OF ANY SERVICES MENTIONED HEREIN.
EXCEPT AS SET FORTH IN RACKSPACE GENERAL TERMS AND CONDITIONS AND/OR
CLOUD TERMS OF SERVICE, RACKSPACE ASSUMES NO LIABILITY WHATSOEVER, AND
DISCLAIMS ANY EXPRESS OR IMPLIED WARRANTY, RELATING TO ITS SERVICES
INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTY OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE, AND NONINFRINGEMENT.

Except as expressly provided in any written license agreement from
Rackspace, the furnishing of this document does not give you any license
to patents, trademarks, copyrights, or other intellectual property.

Rackspace®, Rackspace logo and Fanatical Support® are registered service
marks of Rackspace US, Inc. All other product names and trademarks used
in this document are for identification purposes only and are property
of their respective owners.

2015-04-09

--------------

**List of Examples**

2.1. `List Load Balancers by Virtual IP Response:
XML <List_Load_Balancers-d1e281.html#d6e442>`__
2.2. `List Load Balancers by Virtual IP Response:
JSON <List_Load_Balancers-d1e281.html#d6e445>`__
2.3. `List Load Balancers by Virtual IP Address Response:
XML <List_Load_Balancers-d1e281.html#d6e448>`__
2.4. `List Load Balancers by Virtual IP Address Response:
JSON <List_Load_Balancers-d1e281.html#d6e451>`__
2.5. `List All Clusters Response: XML <Clusters-d1e443.html#d6e494>`__
2.6. `List All Clusters Response: JSON <Clusters-d1e443.html#d6e497>`__
2.7. `List Specified Cluster Response:
XML <Clusters-d1e443.html#d6e500>`__
2.8. `List Specified Cluster Response:
JSON <Clusters-d1e443.html#d6e503>`__
2.9. `List All Hosts Within Cluster Response:
XML <Host_Machines-d1e596.html#d6e586>`__
2.10. `List All Hosts Within Cluster Response:
JSON <Host_Machines-d1e596.html#d6e589>`__
2.11. `Create Host Request:
XML <Creating_a_New_Host-d1e827.html#d6e635>`__
2.12. `Create Host Request:
JSON <Creating_a_New_Host-d1e827.html#d6e638>`__
2.13. `Update Host Request:
XML <Changing_Mutable_Attributes-d1e943.html#d6e678>`__
2.14. `Update Host Request:
JSON <Changing_Mutable_Attributes-d1e943.html#d6e681>`__
2.15. `List All VIPs Within Cluster Response:
XML <Virtual_IPs-d1e1074.html#d6e751>`__
2.16. `List All VIPs Within Cluster Response:
JSON <Virtual_IPs-d1e1074.html#d6e754>`__
2.17. `Assign IP Blocks Response:
XML <Virtual_IPs-d1e1074.html#d6e757>`__
2.18. `Assign IP Blocks Response:
JSON <Virtual_IPs-d1e1074.html#d6e760>`__
2.19. `List Valid Traffic for IP:
JSON <Virtual_IPs-d1e1074.html#d6e764>`__
2.20. `List Valid Traffic for IP (not bound):
JSON <Virtual_IPs-d1e1074.html#d6e768>`__
2.21. `Update Host Assignment Response:
XML <Associations_Between_Load_Balancers_and_Host_Machines-d1e1610.html#d6e834>`__
2.22. `Update Host Assignment Response:
JSON <Associations_Between_Load_Balancers_and_Host_Machines-d1e1610.html#d6e837>`__
2.23. `Update Host Assignment for Multiple Load Balancers with Specified
Host Request:
XML <Associations_Between_Load_Balancers_and_Host_Machines-d1e1610.html#d6e840>`__
2.24. `Update Host Assignment for Multiple Load Balancers with Specified
Host Request:
JSON <Associations_Between_Load_Balancers_and_Host_Machines-d1e1610.html#d6e843>`__
2.25. `Update Host Assignment for Multiple Load Balancers with Host
Chosen by Algorithm Request:
XML <Associations_Between_Load_Balancers_and_Host_Machines-d1e1610.html#d6e846>`__
2.26. `Update Host Assignment for Multiple Load Balancers with Host
Chosen by Algorithm Request:
JSON <Associations_Between_Load_Balancers_and_Host_Machines-d1e1610.html#d6e849>`__
2.27. `List Available Backups for All Hosts Response:
XML <Examining_Immutable_Parameters-d1e1962.html#d6e931>`__
2.28. `List Available Backups for All Hosts Response:
JSON <Examining_Immutable_Parameters-d1e1962.html#d6e934>`__
2.29. `List Available Backups for Specified Host Response:
XML <Examining_Immutable_Parameters-d1e1962.html#d6e937>`__
2.30. `List Available Backups for Specified Host Response:
JSON <Examining_Immutable_Parameters-d1e1962.html#d6e940>`__
2.31. `Add Subnet Mappings Response:
XML <Changing_Subnet_Mappings-d1e2065.html#d6e954>`__
2.32. `Add Subnet Mappings Request:
XML <Changing_Subnet_Mappings-d1e2065.html#d6e957>`__
2.33. `Add Subnet Mappings Request:
JSON <Changing_Subnet_Mappings-d1e2065.html#d6e960>`__
2.34. `Delete Subnet Mappings Request:
XML <Changing_Subnet_Mappings-d1e2065.html#d6e963>`__
2.35. `Delete Subnet Mappings Request:
JSON <Changing_Subnet_Mappings-d1e2065.html#d6e966>`__
2.36. `List Customers by Host or Cluster Name Request:
XML <Customer_Lists-d1e2131.html#d6e1006>`__
2.37. `List Customers by Host or Cluster Name Request:
JSON <Customer_Lists-d1e2131.html#d6e1009>`__
2.38. `List Customers by Cluster Id Request:
XML <Customer_Lists-d1e2131.html#d6e1012>`__
2.39. `List Customers by Cluster Id Request:
JSON <Customer_Lists-d1e2131.html#d6e1015>`__
2.40. `List Customers Response:
XML <Customer_Lists-d1e2131.html#d6e1018>`__
2.41. `List Customers Response:
JSON <Customer_Lists-d1e2131.html#d6e1021>`__
2.42. `List Customer Count by Host Id Response:
XML <Customer_Lists-d1e2131.html#d6e1024>`__
2.43. `List Customer Count by Host Id Response:
JSON <Customer_Lists-d1e2131.html#d6e1027>`__
2.44. `List Customer Count by Cluster Id Response:
XML <Customer_Lists-d1e2131.html#d6e1030>`__
2.45. `List Customer Count by Cluster Id Response:
JSON <Customer_Lists-d1e2131.html#d6e1033>`__
2.46. `Health Check: XML <Health_Check-d1e2342.html#d6e1054>`__
2.47. `Health Check: JSON <Health_Check-d1e2342.html#d6e1057>`__
2.48. `ZeusEvent: XML <Callback-d1e2342.html#d6e1082>`__
2.49. `ZeusEvent: JSON <Callback-d1e2342.html#d6e1085>`__
3.1. `Assign VIP Request:
XML <Assigning_New_Virtual_IPs_to_a_Load_Balancer-d1e2421.html#d6e1116>`__
3.2. `Assign VIP Request:
JSON <Assigning_New_Virtual_IPs_to_a_Load_Balancer-d1e2421.html#d6e1119>`__
3.3. `Add Suspension Request:
XML <Suspending_a_Load_Balancer-d1e2567.html#d6e1183>`__
3.4. `Add Suspension Request:
JSON <Suspending_a_Load_Balancer-d1e2567.html#d6e1186>`__
3.5. `List Suspension Response:
XML <Suspending_a_Load_Balancer-d1e2567.html#d6e1189>`__
3.6. `List Suspension Response:
JSON <Suspending_a_Load_Balancer-d1e2567.html#d6e1192>`__
3.7. `List Extended Load Balancer Details Response:
XML <Viewing_Extended_Details_of_a_Load_Balancer-d1e2709.html#d6e1216>`__
3.8. `List Extended Load Balancer Details Response:
XML <Viewing_Extended_Details_of_a_Load_Balancer-d1e2709.html#d6e1219>`__
3.9. `List Account Load Balancers Response:
XML <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1317>`__
3.10. `List Account Load Balancers Response:
JSON <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1320>`__
3.11. `List Extended Account Load Balancers Response:
XML <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1323>`__
3.12. `List Extended Account Load Balancers Response:
JSON <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1326>`__
3.13. `List Account Load Balancers Usage Response:
XML <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1329>`__
3.14. `List Accounts Usage Response (Paginated):
XML <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1332>`__
3.15. `List Accounts Usage Response (Paginated):
JSON <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1335>`__
3.16. `List Load Balancers Usage Response (Paginated):
XML <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1338>`__
3.17. `List Load Balancers Usage Response (Paginated):
JSON <Account_Loadbalancers_and_Usage_Billing_-d1e2791.html#d6e1341>`__
3.18. `List Alerts Response:
XML <Listing_and_Acknowledging_Alerts-d1e3019.html#d6e1452>`__
3.19. `List Alerts Response:
JSON <Listing_and_Acknowledging_Alerts-d1e3019.html#d6e1455>`__
3.20. `List Limits Groups Response:
JSON <API_Rate_Limiting-d1e3233.html#d6e1517>`__
3.21. `Get Limits Response:
XML <Absolute_Limits-d1e3397.html#d6e1598>`__
3.22. `Get Limits Response:
JSON <Absolute_Limits-d1e3397.html#d6e1601>`__
3.23. `Add Limits Request: XML <Absolute_Limits-d1e3397.html#d6e1604>`__
3.24. `Add Limits Request:
JSON <Absolute_Limits-d1e3397.html#d6e1607>`__
3.25. `Update Limits Request:
XML <Absolute_Limits-d1e3397.html#d6e1610>`__
3.26. `Update Limits Request:
JSON <Absolute_Limits-d1e3397.html#d6e1613>`__
3.27. `List Tickets for Load Balancer Response:
XML <Load_Balancer_Tickets-d1e3543.html#d6e1644>`__
3.28. `List Tickets for Load Balancer Response:
JSON <Load_Balancer_Tickets-d1e3543.html#d6e1647>`__
3.29. `Create Ticket for Load Balancer Request:
XML <Load_Balancer_Tickets-d1e3543.html#d6e1650>`__
3.30. `Create Ticket for Load Balancer Request:
JSON <Load_Balancer_Tickets-d1e3543.html#d6e1653>`__
3.31. `List Zeus Usage Response:
XML <Zeus_Usage-d1e3672.html#d6e1675>`__
3.32. `List Zeus Usage Response:
JSON <Zeus_Usage-d1e3672.html#d6e1678>`__
3.33. `List Account Events Response:
XML <Viewing_Events-d1e3739.html#d6e1722>`__
3.34. `List User Events Response:
XML <Viewing_Events-d1e3739.html#d6e1725>`__
3.35. `List User Events Response:
JSON <Viewing_Events-d1e3739.html#d6e1728>`__
3.36. `List Allowed Domains:
XML <Allowed-domains-d2f002eM.html#d6e1822>`__
3.37. `List Allowed Domains:
JSON <Allowed-domains-d2f002eM.html#d6e1825>`__
3.38. `Add Allowed Domains:
XML <Allowed-domains-d2f002eM.html#d6e1828>`__
3.39. `Add Allowed Domains:
JSON <Allowed-domains-d2f002eM.html#d6e1831>`__
3.40. `List Blacklist Response:
XML <Blacklist_Node_and_Access_List_Management-d1e3970.html#d6e1875>`__
3.41. `List Blacklist Response:
JSON <Blacklist_Node_and_Access_List_Management-d1e3970.html#d6e1878>`__
3.42. `Create Blacklist Request:
XML <Blacklist_Node_and_Access_List_Management-d1e3970.html#d6e1881>`__
3.43. `Create Blacklist Request:
JSON <Blacklist_Node_and_Access_List_Management-d1e3970.html#d6e1884>`__
3.44. `List Jobs Response: XML <Scheduled_Jobs-d1e4129.html#d6e1918>`__
3.45. `List Jobs Response: JSON <Scheduled_Jobs-d1e4129.html#d6e1921>`__
3.46. `List Job Response: XML <Scheduled_Jobs-d1e4129.html#d6e1924>`__
3.47. `List Job Response: JSON <Scheduled_Jobs-d1e4129.html#d6e1927>`__
4.1. `Report Host Capacity Response:
XML <Host_Capacity-d1e4265.html#d6e1963>`__
4.2. `Report Host Capacity Response:
JSON <Host_Capacity-d1e4265.html#d6e1966>`__
4.3. `Report VIP Availability Response:
XML <Virtual_IP_Availability-d1e4356.html#d6e1995>`__
4.4. `Report VIP Availability Response:
JSON <Virtual_IP_Availability-d1e4356.html#d6e1998>`__
4.5. `Report Load Balancer Audit Response:
XML <Load_Balancer_Audit-d1e4450.html#d6e2021>`__
4.6. `Report Load Balancer Audit Response:
JSON <Load_Balancer_Audit-d1e4450.html#d6e2024>`__
4.7. `Load Balancer State History Response:
XML <Load-balancer-state-history-d1e3774.html#d6e2055>`__
4.8. `Load Balancer State History Response:
JSON <Load-balancer-state-history-d1e3774.html#d6e2058>`__
