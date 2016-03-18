==============================================================================================================
2.7. Configuration Backups - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
==============================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.7. Configuration Backups
   :name: configuration-backups
   :class: title

`2.7.1. Examining Immutable
Parameters <Examining_Immutable_Parameters-d1e1962.html>`__
`2.7.2. Creating a New Backup <Creating_a_New_Backup-d1e2040.html>`__
`2.7.3. Changing Subnet
Mappings <Changing_Subnet_Mappings-d1e2065.html>`__

Verb
URI
Description
Access Level
**GET**
/management/hosts/backups
View a list of available backups for all host machines.
Service Admin
**GET**
/management/hosts/``hostId``/backups
View a list of available backups for a specified host machine.
Service Admin
**GET**
/management/hosts/``hostId``/subnetmappings
View the list of subnet mappings for this host.
Service Admin
**PUT**
/management/hosts/``hostId``/subnetmappings
Add subnet mappings on this host.
Service Admin
**DELETE**
/management/hosts/``hostId``/subnetmappings
Delete the specified subnet mappings on this host.
Service Admin
**POST**
/management/hosts/``hostId``/backups
Create a new backup of the host configuration.
Service Admin
**DELETE**
/management/hosts/``hostId``/backups/backupId
Purge a backup with the specified backup ID.
Service Admin
**PUT**
/management/hosts/``hostId``/backups/``backupId``/restore
Restore the specified backup to the host machine.
Service Admin
The host backup and restoration tools allow for service administrators
to take periodic backups of the current state of the configuration on
any given host machine. These functions allow the caller to view a list
of available backup configurations, create new backups, purge backups,
and restore any available configuration.
