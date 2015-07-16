====================
Cloud Load Balancers
====================

API Developer Guide
-------------------

.. toctree::
    :maxdepth: 2

    overview

Concepts
--------

.. toctree::
    :maxdepth: 2

    concepts

General API Information
-----------------------

.. toctree::
    :maxdepth: 2

    general-api-information
    authentication
    service-access
    request-response
    content-compression
    persistent-connections
    paginated-collections
    limits
    faults
    date-time-format
    api-behavior
    compatible-shared-load-balancing-protocols
    role-based-access-control

API Operations: Load Balancers
------------------------------

.. toctree::
    :maxdepth: 1

    List load balancers <api-operations/GET_list_load_balancers_v1.0_account_loadbalancers>
    Create load balancer <api-operations/POST_create_load_balancer_v1.0_account_loadbalancers>
    Bulk-delete load balancer <api-operations/DELETE_bulk-delete_load_balancers_v1.0_account_loadbalancers>
    Show load balancer details <api-operations/GET_show_load_balancer_details_v1.0_account_loadbalancers_loadbalancerid>
    Update load balancer properties <api-operations/PUT_update_load_balancer_properties_v1.0_account_loadbalancers_loadbalancerid>

API Operations: Error Pages
---------------------------

.. toctree::
    :maxdepth: 1

    Show custom error page <api-operations/GET_show_custom_error_page_v1.0_account_loadbalancers_loadbalancerid_errorpage>
    Set custom error page <api-operations/PUT_set_custom_error_page_v1.0_account_loadbalancers_loadbalancerid_errorpage>
    Delete custom error page <api-operations/DELETE_delete_custom_error_page_v1.0_account_loadbalancers_loadbalancerid_errorpage>

Glossary
--------

.. toctree::
    :maxdepth: 2
    
    glossary