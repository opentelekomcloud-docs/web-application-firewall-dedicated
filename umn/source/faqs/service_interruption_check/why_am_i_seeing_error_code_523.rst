:original_name: waf_01_0199.html

.. _waf_01_0199:

Why Am I Seeing Error Code 523?
===============================

If a request passes through WAF twice, WAF blocks the request to prevent an infinite loop. In this case, error 523 is displayed when you access the domain name protected by WAF.

Use the following methods to resolve the issue:

-  Direct the request to the internal DNS server so that the request can bypass the public network.

-  Configure the hosts file of the origin server.

   The following uses the Windows operating system as an example.

   #. Use a text editor to open the **hosts** file. Generally, the **hosts** file is stored in the **C:\\Windows\\System32\\drivers\\etc\\** directory.
   #. Add a record about the IP address of the origin server to the hosts file.
   #. Save the modification and exit.
