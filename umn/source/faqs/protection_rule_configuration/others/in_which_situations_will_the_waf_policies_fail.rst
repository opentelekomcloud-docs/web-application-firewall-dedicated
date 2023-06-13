:original_name: waf_01_0102.html

.. _waf_01_0102:

In Which Situations Will the WAF Policies Fail?
===============================================

Normally, all requests destined for your site will pass through WAF. However, if your site is using CDN and WAF, the WAF policy targeted at the requests for caching static content will not take effect because CDN directly returns these requests to the client.
