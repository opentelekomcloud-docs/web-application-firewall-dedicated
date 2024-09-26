:original_name: waf_01_0335.html

.. _waf_01_0335:

Why Does WAF Block Normal Requests as Invalid Requests?
=======================================================

Symptom
-------

After a website is connected to WAF, a normal access request is blocked by WAF. On the **Events** page, the corresponding **Event Type** reads **Invalid request**, and the **Handle False Alarm** button is grayed out, as shown in :ref:`Figure 1 <waf_01_0335__fig18471757872>`.

.. _waf_01_0335__fig18471757872:

.. figure:: /_static/images/en-us_image_0000001162278415.png
   :alt: **Figure 1** Normal requests blocked by WAF as invalid requests

   **Figure 1** Normal requests blocked by WAF as invalid requests

Possible Cause
--------------

If any of the following cases, WAF blocks the access request as an invalid request:

-  When **form-data** is used for POST or PUT requests, the number of parameters in a form exceeds 8,192.
-  The URL contains more than 2,048 parameters.
-  The number of headers exceeds 512.

Solution
--------

If you confirm that the blocked request is a normal request, allow it by :ref:`Configuring Custom Precise Protection Rules <waf_01_0010>`.
