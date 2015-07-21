==============
Load balancers
==============

Users can configure all documented features of the load balancer at creation time by simply providing the additional elements or attributes in the request. This document provides an overview of all the features the load balancing service supports.

Any protocol that is not listed in the protocols response, or is in the list but ``port=0``, requires port to be set. For example the TCP protocol is in the list, however it specifies port as 0 (``<protocol name="TCP" port="0" />``), therefore it requires ``port`` to be set.

You must specify the type of virtualIp to add along with the creation of a load balancer. The following table describes the options.

.. table:: 
    :name: Virtual IP types
    +===============+============+=================+
    | Version       | Type       | Outcome         |
    +===============+============+=================+
    | Not specified | PUBLIC     | IPV4 & IPV6     |
    +---------------+------------+-----------------+
    | IPV4          | PUBLIC     |                 |
    +---------------+------------+-----------------+
    | IPV6          | PUBLIC     | IPV6            |
    +---------------+------------+-----------------+
    | Not specified | SERVICENET | IPV4            |
    +---------------+------------+-----------------+
    | IPV4          | SERVICENET | IPV4            |
    +---------------+------------+-----------------+
    | IPV6          | SERVICENET | Failure message |
    +---------------+------------+-----------------+

Notice in the following examples that API users are now able to programmatically derive the source IP addresses of our load balancers using the sourceAddresses label included at the bottom of the create load balancer (required attributes) response. This feature is useful for customers who are automating the deployment of infrastructure and must determine the IP addresses of requests coming from our load balancers for the purpose of creating more robust firewall rules.

To conserve IPv4 address space, Rackspace highly recommends sharing Virtual IPs between your load balancers. If you have at least one load balancer, you may create subsequent load balancers that share a single virtual IPv4 and/or a single IPv6 by issuing a POST and supplying a virtual IP ID instead of a type. Additionally, this feature is highly desirable if you wish to load balance both an unsecured and secure protocol using one IP or DNS name. For example, this method makes it possible to use the same load balancing configuration to support HTTP and HTTPS.

.. note::
    Load balancers sharing a virtual IP must utilize a unique port. Also, to share both an IPv4 as well as an IPv6, you must supply an extra virtualIp object to the virtualIps container with the desired ID being shared.

    In addition, load balancers sharing Virtual IPs can utilize certain-compatible TCP/UDP and DNS based protocols on the same port. See Section 3.11, “Compatible shared load balancing protocols” for more details.

All load balancers also have a status attribute that shows current configuration status of the device. This status is immutable by the caller and is updated automatically based on state changes within the service. When a load balancer is first created, it is placed into a BUILD status while the configuration is being generated and applied based on the request. Once the configuration is applied and finalized, it is in an ACTIVE status. In the event of a configuration change or update, the status of the load balancer changes to PENDING_UPDATE to signify configuration changes are in progress but are not yet been finalized. Load balancers in a SUSPENDED status are configured to reject traffic and does not forward requests to back-end nodes.

.. table::
    :name: Load balancer statuses

    +================+============================================================+
    | Name           | Description                                                |
    +================+============================================================+
    | ACTIVE         | Load balancer is configured properly and ready to serve    |
    |                | traffic to incoming requests via the configured virtual    |
    |                | IPs.                                                       |
    +----------------+------------------------------------------------------------+
    | BUILD          | Load balancer is being provisioned for the first time and  |
    |                | configuration is being applied to bring the service online.|
    |                | The service cannot yet serve incoming requests.            |
    +----------------+------------------------------------------------------------+
    | PENDING_UPDATE | Load balancer is online but configuration changes are      |
    |                | being applied to update the service based on a previous    |
    |                | request.                                                   |
    +----------------+------------------------------------------------------------+
    | PENDING_DELETE | Load balancer is online but configuration changes are      |
    |                | being applied to begin deletion of the service based on    |
    |                | a previous request.                                        |
    +----------------+------------------------------------------------------------+
    | SUSPENDED      | Load balancer has been taken offline and disabled;         |
    |                | contact Support.                                           |
    +----------------+------------------------------------------------------------+
    | ERROR          | The system encountered an error when attempting to         |
    |                | configure the load balancer; contact Support.              |
    +----------------+------------------------------------------------------------+
    | DELETED        | Load balancers in DELETED status can be displayed          |
    |                | for at least 90 days after deletion.                       |
    +----------------+------------------------------------------------------------+

The update operation allows the caller to change one or more of the following attributes:

- name
- algorithm
- protocol
- halfClosed
- port
- timeout
- httpsRedirect

.. toctree::
    :maxdepth: 6
    :hidden:

    GET_list_load_balancers_v1.0_account_loadbalancers
    POST_create_load_balancer_v1.0_account_loadbalancers
    DELETE_bulk-delete_load_balancers_v1.0_account_loadbalancers
    GET_show_load_balancer_details_v1.0_account_loadbalancers_loadbalancerid
    PUT_update_load_balancer_properties_v1.0_account_loadbalancers_loadbalancerid