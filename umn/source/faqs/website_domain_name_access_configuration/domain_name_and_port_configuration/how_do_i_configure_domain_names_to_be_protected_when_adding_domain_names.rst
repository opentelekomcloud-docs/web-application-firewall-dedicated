:original_name: waf_01_0105.html

.. _waf_01_0105:

How Do I Configure Domain Names to Be Protected When Adding Domain Names?
=========================================================================

Before using WAF, you need to add domain names to be protected to WAF based on your web service protection requirements. WAF supports addition of single domain names and wildcard domain names. This section describes how to configure domain names to be protected.

Basic Concepts
--------------

-  Wildcard domain name

   A wildcard domain name is a domain name that contains the wildcard **\*** and starts with **\*.**.

   For example, **\*.example.com** is a correct wildcard domain name, but **\*.*.example.com** is not.

   .. note::

      A wildcard domain name counts as one domain name.

-  Single domain name

   A single domain name is also called a common domain name and is a specific domain name (a non-wildcard domain name).

   For example, **www.example.com** or **example.com** is a single domain name.

   .. note::

      For example, **www.example.com** counts as a domain name and so does **a.www.example.com**.

Selecting a Domain Name Type
----------------------------

WAF supports single domain names and wildcard domain names.

The domain name purchased from the DNS service provider is a single domain name (example.com). The domain name added to WAF can be example.com, a subdomain name (for example, a.example.com), or wildcard domain name (``*``.example.com). You can select a domain name type based on the following scenarios:

-  If services of a domain name to be protected are the same, enter a single domain name. For example, if all the services of www.example.com to be protected are services on port 8080, set **Domain Name** to a single domain name **www.example.com**.
-  If the server IP address of each subdomain name is the same, enter a wildcard domain name to be protected. For example, if the server IP addresses corresponding to a.example.com, b.example.com, and c.example.com are the same, **Domain Name** can be set to a wildcard domain name **\*.example.com**.
-  If the server IP addresses of subdomain names are different, add subdomain names as single domain names one by one.

.. note::

   You are advised to set the added domain name to be protected to be the same as the domain name that is set at the DNS provider.
