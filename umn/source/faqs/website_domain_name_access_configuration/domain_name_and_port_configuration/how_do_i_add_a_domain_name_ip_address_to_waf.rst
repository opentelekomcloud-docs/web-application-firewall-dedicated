:original_name: waf_01_0176.html

.. _waf_01_0176:

How Do I Add a Domain Name/IP Address to WAF?
=============================================

After you connect a domain name or IP address of the website you want to protect to WAF, WAF works as a reverse proxy between the client and the server. The real IP address of the server is hidden and only the IP address of WAF is visible to web visitors. For details, see :ref:`Step 1: Add a Website to WAF <waf_01_0250>`.

.. important::

   -  You can enter a multi-level single domain name (for example, top-level domain name example.com or second-level domain name www.example.com) or a wildcard domain name (``*``.example.com). The processes of connecting domain names to different WAF instance types are the same.

      -  If the server IP address of each subdomain name is the same, enter a wildcard domain name. For example, if the subdomain names **a.example.com**, **b.example.com**, and **c.example.com** have the same server IP address, you can add the wildcard domain name **\*.example.com** to WAF to protect all three.
      -  If the server IP addresses of subdomain names are different, add subdomain names as single domain names one by one.

   -  Each combination of a domain name and a non-standard port is counted towards the domain name quota of the WAF edition you are using. For example, www.example.com:8080 and www.example.com:8081 use two domain names of the quota. If you want to protect web services over multiple ports with the same domain name, add the domain name and each port to WAF.

The following figure shows the process of connecting a website to WAF in each mode.


.. figure:: /_static/images/en-us_image_0000001171626489.png
   :alt: **Figure 1** Process of connecting a website to a dedicated WAF instance

   **Figure 1** Process of connecting a website to a dedicated WAF instance

-  If **Access Status** for protected website is **Inaccessible**, rectify the fault by referring to :ref:`Why Is My Domain Name or IP Address Inaccessible? <waf_01_0278>`
-  If your website becomes inaccessible after it is connected to WAF, rectify the issue by referring to :ref:`How Do I Troubleshoot 404/502/504 Errors? <waf_01_0066>`
