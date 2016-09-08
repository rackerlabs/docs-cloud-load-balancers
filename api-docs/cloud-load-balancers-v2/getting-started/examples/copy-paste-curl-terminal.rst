
================================================================
Copying and Pasting cURL Request Examples into a Terminal Window
================================================================

To run the cURL request examples shown in this guide on Linux or Mac
systems, select the desired example from the HTML version of this guide
by clicking the Select Text icon to the right of the example and then
select Edit->Copy. Then paste it into an ASCII editor (for example
**vi** or **TextEdit**). Next modify the example with your required
account information and so forth, as detailed in this guide.

.. note::
   The carriage returns in the cURL request examples that are part of the
   cURL syntax are escaped with a backslash ('\\') in order to avoid
   prematurely terminating the command. However you should not escape
   carriage returns inside the xml or json message within the command.

Consider the following cURL Authenticate Request: XML example that is
described in detail in `Chapter 4, *Generate an Authentication
Token* <ch04.xhtml>`__:

**Example: cURL Authenticate Request: XML**

.. code::

    curl -i -d \
    '<?xml version="1.0" encoding="UTF-8"?>
     <auth>   
        <apiKeyCredentials     
            xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"     
            username="your_username"     
            apiKey="your_api_key"/>   
     </auth>' \
    'https://identity.api.rackspacecloud.com/v2.0/tokens'

You can see that the lines that are part of the cURL command syntax have
all been escaped with a backslash ('\\') to indicate that the command
continues on the next line:

.. code::

    curl -i -d \
             
    (... lines within the xml portion of the message are not shown in this
    example)
    (... the example only shows lines that are part of cURL syntax)     
                
     </auth>' \
    'https://identity.api.rackspacecloud.com/v2.0/tokens'

However the lines *within* the xml portion of the message are *not*
escaped with a backslash ('\\') in order to avoid issues with the xml
processing:

.. code::

    '<?xml version="1.0" encoding="UTF-8"?>
     <auth>   
        <apiKeyCredentials     
            xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"     
            username="your_username"     
            apiKey="your_api_key"/>   
     </auth>' \

.. note::
   The final line of the xml message is escaped since the backslash lies
   *outside* the xml message and continues the cURL command to the next
   line.

After you are finished modifying the text for the cURL request example
with your information (for example **``your_username``** and
**``your_api_key``**), paste it into your terminal window. Then execute
the cURL command by pressing Enter.

If you have trouble copying and pasting the examples as described, try
typing the entire example on one long line, removing all the backslash
line continuation characters.
