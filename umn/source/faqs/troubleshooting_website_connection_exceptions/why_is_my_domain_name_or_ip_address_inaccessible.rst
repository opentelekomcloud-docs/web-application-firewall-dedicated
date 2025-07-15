:original_name: waf_01_0278.html

.. _waf_01_0278:

Why Is My Domain Name or IP Address Inaccessible?
=================================================

Symptoms
--------

If **Access Progress/Status** for a website you have added to WAF is **Inaccessible**, the connection between WAF and the website domain name or IP address fails to be established.

Troubleshooting and Solutions for Dedicated WAF
-----------------------------------------------

Refer to :ref:`Figure 1 <waf_01_0278__fig1680743491611>` and :ref:`Table 1 <waf_01_0278__table439923118137>` to fix connection failures.

.. _waf_01_0278__fig1680743491611:

.. figure:: /_static/images/en-us_image_0000001667743969.png
   :alt: **Figure 1** Troubleshooting for dedicated mode

   **Figure 1** Troubleshooting for dedicated mode

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
   |                                                                                                                                                         | #. :ref:`Binding an EIP to a Load Balancer <waf_01_0252>`.                                                                                                                  |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cause 5: Incorrect load balancer configured or incorrect EIP bound to the load balancer                                                                 | -  After you :ref:`configure a load balancer <waf_01_0251>`, ensure that **Health Check Result** for the dedicated WAF instances added to the load balancer is **Healthy**. |
   |                                                                                                                                                         | -  After you :ref:`bind an EIP to the load balancer <waf_01_0252>`, check the EIP status.                                                                                   |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Troubleshooting and Solutions for ELB Access Mode
-------------------------------------------------

For **ELB Access**, refer to :ref:`Figure 2 <waf_01_0278__fig153411857111619>` and :ref:`Table 2 <waf_01_0278__table12804175031614>` to fix connection failures.

.. _waf_01_0278__fig153411857111619:

.. figure:: /_static/images/en-us_image_0000001396559941.png
   :alt: **Figure 2** Troubleshooting for ELB Access Mode

   **Figure 2** Troubleshooting for ELB Access Mode

.. _waf_01_0278__table12804175031614:

.. table:: **Table 2** Troubleshooting for website connection failure in WAF - ELB access mode

   +---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Possible Cause                                                                                                                                          | Solution                                                                                                |
   +=========================================================================================================================================================+=========================================================================================================+
   | Cause 1: **Access Status** for **Domain Name/IP Address** not updated                                                                                   | In the **Access Status** column for the website, click |image3| to update the status.                   |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Cause 2: Website access traffic not enough for WAF to consider the website accessible                                                                   | #. Access the protected website for many times within 1 minute.                                         |
   |                                                                                                                                                         | #. In the **Access Status** column for the website, click |image4| to update the status.                |
   | .. important::                                                                                                                                          |                                                                                                         |
   |                                                                                                                                                         |                                                                                                         |
   |    NOTICE:                                                                                                                                              |                                                                                                         |
   |    After you connect a website to WAF, the website is considered accessible only when WAF detects at least 20 requests to the website within 5 minutes. |                                                                                                         |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Cause 3: Incorrect domain name or IP address settings                                                                                                   | Check whether the domain name or IP address settings are correct.                                       |
   |                                                                                                                                                         |                                                                                                         |
   |                                                                                                                                                         | If there are incorrect settings, remove the domain name or IP address from WAF and add it to WAF again. |
   +---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001497159614.png
.. |image2| image:: /_static/images/en-us_image_0000001547599721.png
.. |image3| image:: /_static/images/en-us_image_0000002039631197.png
.. |image4| image:: /_static/images/en-us_image_0000002003392090.png
