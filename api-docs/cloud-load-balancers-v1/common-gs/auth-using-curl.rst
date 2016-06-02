.. _authenticate-using-curl:

Follow these steps to authenticate to the Rackspace Cloud by
:ref:`using cURL <how-curl-commands-work>`.

- :ref:`Send authentication request <send-auth-req-curl>`
- :ref:`Review the authentication response <review-auth-resp>`
- :ref:`Configure environment variables <configure-environment-variables>`


.. _send-auth-req-curl:

Send an authentication request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From a command prompt, send a **POST tokens** request to the Rackspace Cloud Identity
service.  Include your username and :ref:`API key <get-credentials>`
as shown in the following example.

.. include:: ../common-gs/samples/auth-req-curl.rst


.. _review-auth-resp:

Review the authentication response
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If your credentials are valid, the Identity service returns an authentication response
that includes the following information:

- an authentication token
- a service catalog with information about the services you can access.
- user information and role assignments

.. note::
   For detailed information about the authentication response, see the
   :rax-devdocs:`Annotated authentication request and response<cloud-identity/v2/developer-guide/#document-authentication-info/sample-auth-req-response>`
   in the Rackspace Cloud API documentation.

In the following example, the ellipsis (...)  represents other service endpoints, which
are not shown. The values shown in this and other examples vary because the information
returned is specific to your account.

**Example: Authentication response**

.. include:: ../common-gs/samples/auth-resp-json.rst


If the request was successful, you can find the authentication token and other information in the
authentication response. You'll need these values to submit requests to the API. See
:ref:`Configure environment variables<configure-environment-variables>`.

If the request failed, review the response message and
the following error message descriptions to determine next steps.

.. code::

   400 Invalid request body: unable to parse Auth data. Please review XML or JSON formatting

Review the authentication request for syntax or coding errors.
If you are using cURL, see :ref:`Using cURL <how-curl-commands-work>`.


.. code::

   401 Unable to authenticate user with credentials provided.

Verify the authentication credentials submitted in the
authentication request. If necessary, contact your Rackspace
Cloud Administrator or Rackspace Support to get valid
credentials.

..  note::
       For additional information about authentication errors, see the
       :rax-devdocs:`Identity API Reference documentation <cloud-identity/v2/developer-guide/#document-api-operations/token-operations>`.


.. _configure-environment-variables:

Configure environment variables
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The authentication response returns the following values that you
need to include when you make service requests to the |apiservice|.


token ID
    The token ID value is required to confirm your identity each time you access the service.
    Include it in the ``X-Auth-Token`` header for each API request.

    The ``expires`` attribute indicates the date and time that the token will expire,
    unless it is revoked prior to the
    expiration. To get a new token, submit another authentication request. For more
    information, see
    :rax-devdocs:`Manage tokens and token expiration
    <cloud-identity/v2/developer-guide/#manage-authentication-tokens>`.

tenant ID
    The tenant ID provides your account number. For most Rackspace Cloud service APIs, the
    tenant ID is appended to the API endpoint in the service catalog automatically. For
    Rackspace Cloud Services, the tenant ID has the same value as the tenant name.

endpoint
	The API endpoint provides the URL that you use to access the API service. For guidance
	on choosing an endpoint, see :ref:`Service access <service-access>`.


To make it easier to include the values in API requests, use the export command to create
environment variables that can be substituted for the actual values. For example, you can
create an ``API_ENDPOINT`` variable to store the URL for accessing an API service.
To reference the value in an API request, prefix the variable name with a $, for example
``$API_ENDPOINT``.

.. include:: ../common-gs/using-env-variables.rst

**Create environment variables**

#. In the ``token`` section of the authentication response, copy the token ``id`` and
   tenant ``id`` values from the token object.

      .. include:: ../common-gs/samples/auth-token-object.rst

#. Export the token ID to an environment variable
   that can be supplied in the `X-Auth-Token` header required in each
   API request.

   .. code::

       $ export AUTH_TOKEN="token-id"

   Replace *token-id* with the authentication token ``id`` value returned
   in the authentication response.

#. Export the tenant ID to an environment variable
   that can be supplied in requests that require you to specify a tenant ID or tenant name.

   .. code::

       $ export TENANT_ID="tenant-id"

   Replace *tenant-id* with the authentication token ``id`` value returned
   in the authentication response.

#. In the ``service catalog`` section of the authentication response, copy the ``publicURL``
   value for the |apiservice|, version, and region that you want to access.

   This example shows the endpoints available for the |apiservice|.

   .. include:: ../common-gs/samples/service-catalog-endpoint.rst


#. Copy the URL, and then export it to an environment variable.

   .. code::

        $ export API_ENDPOINT="publicURL"


   Replace *publicURL* with the publicURL value listed in the service catalog.

   .. note::
       Rackspace Cloud Identity returns an endpoint URL with your tenant ID (account ID).
       With Cloud Load Balancers, you have two options for including the tenant ID in
       API requests.

       - Include it in the URL.

         .. code::

             https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/123456


       - Submit API requests to the base endpoint
         ``https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/``, and specify the tenant ID
         value in the ``X-Project-ID`` header in each request with the value set to the tenant
         ID.

       In the examples in this guide, the tenant ID is included in the URL.
