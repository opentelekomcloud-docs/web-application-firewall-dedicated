:original_name: waf_01_0184.html

.. _waf_01_0184:

Does WAF Support Two-Way SSL Authentication?
============================================

No. You can configure a one-way SSL certificate on WAF.

.. note::

   If you set **Client Protocol** to **HTTPS** when adding a website to WAF, you will be required to upload a certificate and use it for your website.

You are advised to use an ELB load balancer and dedicated WAF instances and then configure two-way authentication on the load balancer. The procedure is as follows:

#. :ref:`Applying for a Dedicated WAF Instance <waf_01_1072>`.
#. Connect your website to WAF and configure ELB. For details, see :ref:`Connection Process (Dedicated Mode) <waf_01_0326>`.
#. Configure two-way authentication on the ELB.
