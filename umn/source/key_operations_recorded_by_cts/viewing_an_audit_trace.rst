:original_name: waf_01_0060.html

.. _waf_01_0060:

Viewing an Audit Trace
======================

After you enable CTS, the system starts recording operations on WAF. Operation records for the last seven days can be viewed on the CTS console.

Viewing WAF Logs on the CTS console
-----------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner of the page. In the dialog box displayed on the right, choose **Management & Deployment** > **Cloud Trace Service**.

#. Choose **Trace List** in the navigation pane.

#. Click **Filter** and specify filtering criteria as needed. The following four filters are available:

   -  **Trace Type**, **Trace Source**, **Resource Type**, and **Search By**.

      -  Set **Trace Type** to **Management**.
      -  Set **Trace Source** to **WAF**.
      -  When you select **Resource ID** for **Search By**, you also need to enter a resource ID.

   -  **Operator**: Select a specific operator (a user other than tenant).
   -  **Trace Status**: Available options include **All trace statuses**, **normal**, **warning**, and **incident**. You can only select one of them.
   -  **Time Range**: In the upper right corner of the page, you can query traces in the last 1 hour, last 1 day, last 1 week, or within a customized period.

#. Click **Query**.

#. Click |image3| on the left of a trace to expand its details, as shown in :ref:`Figure 1 <waf_01_0060__fig512618236452>`.

   .. _waf_01_0060__fig512618236452:

   .. figure:: /_static/images/en-us_image_0216882896.png
      :alt: **Figure 1** Expanding trace details

      **Figure 1** Expanding trace details

#. Click **View Trace** in the **Operation** column. On the displayed **View Trace** dialog box shown in :ref:`Figure 2 <waf_01_0060__fig111275233454>`, the trace structure details are displayed.

   .. _waf_01_0060__fig111275233454:

   .. figure:: /_static/images/en-us_image_0110861334.jpg
      :alt: **Figure 2** Viewing the trace

      **Figure 2** Viewing the trace

.. |image1| image:: /_static/images/en-us_image_0000001538688185.jpg
.. |image2| image:: /_static/images/en-us_image_0000001538689725.png
.. |image3| image:: /_static/images/en-us_image_0210924459.png
