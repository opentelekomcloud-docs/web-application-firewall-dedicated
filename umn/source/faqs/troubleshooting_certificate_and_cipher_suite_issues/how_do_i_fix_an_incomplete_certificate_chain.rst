:original_name: waf_01_0082.html

.. _waf_01_0082:

How Do I Fix an Incomplete Certificate Chain?
=============================================

If the certificate provided by the certificate authority is not found in the built-in trust store on your platform and the certificate chain does not have a certificate authority, the certificate is incomplete. If you use the incomplete certificate to access the website corresponding to the protected domain name, the access will fail.

Use either of the following methods to fix it:

-  Make a complete certificate chain manually and upload the certificate.
-  Upload the correct certificate.

The latest Google Chrome version supports automatic verification of the trust chain. The following describes how to manually create a complete certificate chain:

#. **View and export the certificate.**

   a. Click the padlock in the address bar to view the certificate status.
   b. Locate the row that shows **Secure Connection**, click |image1|, and click **Valid Certificate** in address bar.
   c. Click the **Details** tab. In the lower right corner of the page, click **Copy to File...** to export the certificate to the local PC.

#. Check the certificate chain. Open the certificate you export. Select the **Certificate Path** tab and then click the certificate name to view the certificate status.

#. Save the certificates to the local PC one by one.

   a. Select the certificate name and click the **Details** tab.

   b. Click **Copy to File**, and then click **Next** as prompted.

   c. Select **Base-64 encoded X.509 (.CER)** and click **Next**. :ref:`Figure 1 <waf_01_0082__fig1699010397583>` shows an example.

      .. _waf_01_0082__fig1699010397583:

      .. figure:: /_static/images/en-us_image_0000002395334853.png
         :alt: **Figure 1** Certificate Export Wizard

         **Figure 1** Certificate Export Wizard

#. Rebuild the certificate. After all certificates are exported to the local PC, open the certificate file in Notepad and rebuild the certificate according to the sequence shown in :ref:`Figure 2 <waf_01_0082__fig1970017819312>`.

   .. _waf_01_0082__fig1970017819312:

   .. figure:: /_static/images/en-us_image_0000002395175005.png
      :alt: **Figure 2** Certificate rebuilding

      **Figure 2** Certificate rebuilding

#. Upload the certificate again.

.. |image1| image:: /_static/images/en-us_image_0000002361495052.png
