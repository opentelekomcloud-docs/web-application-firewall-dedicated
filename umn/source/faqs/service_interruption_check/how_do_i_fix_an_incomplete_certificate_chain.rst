:original_name: waf_01_0082.html

.. _waf_01_0082:

How Do I Fix an Incomplete Certificate Chain?
=============================================

If the certificate provided by the certificate authority is not found in the built-in trust store on your platform and the certificate chain does not have a certificate authority, the certificate is incomplete. If you use the incomplete certificate to access the website corresponding to the protected domain name, the access will fail.

Use either of the following methods to fix it:

-  Manually build up a complete certificate chain and upload the certificate. (This function is available soon.)
-  Purchase a new certificate and upload it.

The latest Google Chrome version supports automatic verification of the trust chain. The following describes how to manually create a complete certificate chain:

#. Check the certificate. Click the padlock in the address bar to view the certificate status. :ref:`Figure 1 <waf_01_0082__fig3896113414308>` shows an example.

   .. _waf_01_0082__fig3896113414308:

   .. figure:: /_static/images/en-us_image_0246108677.png
      :alt: **Figure 1** Viewing the certificate

      **Figure 1** Viewing the certificate

#. Check the certificate chain. Click **Certificate**. Select the **Certificate Path** tab and then click the certificate name to view the certificate status. :ref:`Figure 2 <waf_01_0082__fig1987812411375>` shows an example.

   .. _waf_01_0082__fig1987812411375:

   .. figure:: /_static/images/en-us_image_0246112199.png
      :alt: **Figure 2** Viewing the certificate chain

      **Figure 2** Viewing the certificate chain

#. Save the certificates to the local PC one by one.

   a. Select the certificate name and click the **Details** tab. :ref:`Figure 3 <waf_01_0082__fig56008156448>` shows an example.

      .. _waf_01_0082__fig56008156448:

      .. figure:: /_static/images/en-us_image_0246108818.png
         :alt: **Figure 3** Details

         **Figure 3** Details

   b. Click **Copy to File**, and then click **Next** as prompted.

   c. Select **Base-64 encoded X.509 (.CER)** and click **Next**. :ref:`Figure 4 <waf_01_0082__fig1699010397583>` shows an example.

      .. _waf_01_0082__fig1699010397583:

      .. figure:: /_static/images/en-us_image_0246109037.png
         :alt: **Figure 4** Certificate Export Wizard

         **Figure 4** Certificate Export Wizard

#. Rebuild the certificate. After all certificates are exported to the local PC, open the certificate file in Notepad and rebuild the certificate according to the sequence shown in :ref:`Figure 5 <waf_01_0082__fig1970017819312>`.

   .. _waf_01_0082__fig1970017819312:

   .. figure:: /_static/images/en-us_image_0283637109.png
      :alt: **Figure 5** Certificate rebuilding

      **Figure 5** Certificate rebuilding

#. Upload the certificate again.
