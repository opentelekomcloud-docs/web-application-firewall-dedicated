:original_name: waf_01_0278.html

.. _waf_01_0278:

Why Is My Domain Name or IP Address Inaccessible?
=================================================

Symptoms
--------

If **Access Progress/Status** for a website you have added to WAF is **Inaccessible**, the connection between WAF and the website domain name or IP address fails to be established.


.. figure:: /_static/images/en-us_image_0000001345493078.png
   :alt: **Figure 1** Website list

   **Figure 1** Website list

.. important::

   WAF automatically checks the access status of protected websites every hour. If WAF detects that a protected website has received 20 access requests within 5 minutes, it considers that the website has been successfully connected to WAF.

Troubleshooting and Solutions for WAF Instances
-----------------------------------------------

Refer to :ref:`Figure 2 <waf_01_0278__fig1680743491611>` and :ref:`Table 1 <waf_01_0278__table439923118137>` to fix connection failures.

.. _waf_01_0278__fig1680743491611:

.. figure:: /_static/images/en-us_image_0000001119487028.png
   :alt: **Figure 2** Troubleshooting for dedicated mode

   **Figure 2** Troubleshooting for dedicated mode

.. _waf_01_0278__table439923118137:

.. table:: **Table 1** Solutions for dedicated mode

   +---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Possible Cause                                                                                                                                          | Solution                                                                                                                                                                    |
   +=========================================================================================================================================================+=============================================================================================================================================================================+
   | Cause 1: **Access Status** for **Domain Name/IP Address** not updated                                                                                   | In the **Access Status** column for the website, click |image1| to update the status.                                                                                       |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cause 2: Website access traffic not enough for WAF to consider the website accessible                                                                   | #. Access the protected website many times within 1 minute.                                                                                                                 |
   |                                                                                                                                                         | #. In the **Access Status** column for the website, click |image2| to update the status.                                                                                    |
   | .. important::                                                                                                                                          |                                                                                                                                                                             |
   |                                                                                                                                                         |                                                                                                                                                                             |
   |    NOTICE:                                                                                                                                              |                                                                                                                                                                             |
   |    After you connect a website to WAF, the website is considered accessible only when WAF detects at least 20 requests to the website within 5 minutes. |                                                                                                                                                                             |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cause 3: Incorrect domain name or IP address settings                                                                                                   | Check domain name or IP address settings.                                                                                                                                   |
   |                                                                                                                                                         |                                                                                                                                                                             |
   |                                                                                                                                                         | If there are incorrect settings for the domain name or IP address, remove this domain name or IP address from WAF and add it to WAF again.                                  |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cause 4: No load balancer configured for the dedicated WAF instance or no EIP bound to the load balancer configured for the dedicated WAF instance      | #. Configure a load balancer for dedicated WAF instances by referring to :ref:`Configuring a Load Balancer <waf_01_0251>`.                                                  |
   |                                                                                                                                                         | #. :ref:`Bind an EIP to a Load Balancer <waf_01_0252>`.                                                                                                                     |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cause 5: Incorrect load balancer configured or incorrect EIP bound to the load balancer                                                                 | -  After you :ref:`configure a load balancer <waf_01_0251>`, ensure that **Health Check Result** for the dedicated WAF instances added to the load balancer is **Healthy**. |
   |                                                                                                                                                         | -  After you :ref:`bind an EIP to the load balancer <waf_01_0252>`, check the EIP status.                                                                                   |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001497159614.png
.. |image2| image:: /_static/images/en-us_image_0000001547599721.png
