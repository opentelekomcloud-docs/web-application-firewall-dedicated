:original_name: waf_01_3312.html

.. _waf_01_3312:

Why Is the Bar Mitzvah Attack on SSL/TLS Detected?
==================================================

The bar mitzvah attack is an attack on SSL/TLS protocols that exploits a vulnerability in the RC4 cryptographic algorithm. This vulnerability can disclose ciphertext in SSL/TLS encrypted traffic in some cases, such as passwords, credit card data, or other privacy data, to hackers.

Solution
--------

To solve this problem, you can set the minimum TLS version to TLS v1.2 and cipher suite to cipher suite 2.
