:original_name: waf_01_0287.html

.. _waf_01_0287:

Connecting a Website to WAF (ELB Access Mode)
=============================================

If your service servers are deployed on the cloud, you can select WAF ELB access mode to add your website IP address or domain name to WAF.

.. note::

   If you have enabled enterprise projects, you can select an enterprise project from the **Enterprise Project** drop-down list and add websites to be protected in the project.

Prerequisites
-------------

-  You have :ref:`applied for a dedicated WAF instance <waf_01_1072>`.
-  You have contacted technical support to apply for the ELB access mode.
-  You have applied for a dedicated load balancer. Its specifications must be **Application load balancing (HTTP/HTTPS)**. Note that the account you use to apply for the load balancer must have WAF dedicated mode enabled.

Connecting Your Website to WAF ELB Access Mode
----------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the upper left corner of the website list, click **Add Website**.

#. Choose **ELB access** and click **OK**.

#. On the displayed domain name details page, configure basic settings by referring to :ref:`Table 1 <waf_01_0287__en-us_topic_0000001871474014_table7692122554811>`.

   .. _waf_01_0287__en-us_topic_0000001871474014_table7692122554811:

   .. table:: **Table 1** Parameter description

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                            | Example Value                            |
      +=======================+========================================================================================================================================================================================================================================================================================================================+==========================================+
      | ELB (Load Balancer)   | Select an ELB load balancer from the drop-down list. Make sure the server address of the protected website has been added to the ELB load balancer.                                                                                                                                                                    | elb-waf-test                             |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | ELB Listener          | Listener configured for the selected ELB load balancer.                                                                                                                                                                                                                                                                | All listeners                            |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | -  **All listeners**                                                                                                                                                                                                                                                                                                   |                                          |
      |                       | -  **Specific listener**                                                                                                                                                                                                                                                                                               |                                          |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Website Name          | (Optional) You can specify a name for your website.                                                                                                                                                                                                                                                                    | None                                     |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Domain Name           | Set this parameter to the domain name or IP address you want to protect. Make sure that the domain name has been resolved to the EIP of the load balancer.                                                                                                                                                             | Single domain name: **www.example.com**  |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | Single domain names or wildcard domain names are supported.                                                                                                                                                                                                                                                            | Wildcard domain name: **\*.example.com** |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | -  Single domain name: Enter a single domain name, for example, www.example.com.                                                                                                                                                                                                                                       | IP Address:                              |
      |                       | -  Wildcard domain name                                                                                                                                                                                                                                                                                                |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                        | XXX.XXX.1.1                              |
      |                       |    -  If the server IP address of each subdomain name is the same, enter a wildcard domain name. For example, if the subdomain names **a.example.com**, **b.example.com**, and **c.example.com** have the same server IP address, you can add the wildcard domain name **\*.example.com** to WAF to protect all three. |                                          |
      |                       |    -  If the server IP addresses of subdomain names are different, add subdomain names as single domain names one by one.                                                                                                                                                                                              |                                          |
      |                       |    -  Wildcard domain name\ **\*** can be added.                                                                                                                                                                                                                                                                       |                                          |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Website Remarks       | (Optional) You can enter a description for your website.                                                                                                                                                                                                                                                               | ``-``                                    |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Policy                | The **system-generated policy** is selected by default. You can select a policy you configured before. You can also customize rules after the domain name is connected to WAF.                                                                                                                                         | System-generated policy                  |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | System-generated policies                                                                                                                                                                                                                                                                                              |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | -  Basic web protection (**Log only** mode and common checks)                                                                                                                                                                                                                                                          |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       |    The basic web protection defends against attacks such as SQL injections, XSS, remote overflow vulnerabilities, file inclusions, Bash vulnerabilities, remote command execution, directory traversal, sensitive file access, and command/code injections.                                                            |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | -  Anti-crawler (**Log only** mode and **Scanner** feature)                                                                                                                                                                                                                                                            |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       |    WAF only logs web scanning tasks, such as vulnerability scanning and virus scanning, such as crawling behavior of OpenVAS and Nmap.                                                                                                                                                                                 |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | .. note::                                                                                                                                                                                                                                                                                                              |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       |    -  **Log only**: WAF only logs detected attacks instead of blocking them.                                                                                                                                                                                                                                           |                                          |
      |                       |    -  Only the professional and platinum editions allow you to specify a custom policy for **Policy**.                                                                                                                                                                                                                 |                                          |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+

#. Click **OK**.

   You can view the added websites in the protected website list.

Follow-up Operations
--------------------

The initial **Access Progress** of a domain name is **Inaccessible**. When a certain number of requests for the website reach WAF, WAF changes the access status of the website to **Accessible**. To address access failure, see

After the domain name is connected to WAF, there is one step required to enable WAF protection. You need to configure WAF protection policy for the domain name. For details, see :ref:`Configuring Protection <waf_01_0129>`.

.. |image1| image:: /_static/images/en-us_image_0000001882710280.jpg
.. |image2| image:: /_static/images/en-us_image_0000001982966364.png
