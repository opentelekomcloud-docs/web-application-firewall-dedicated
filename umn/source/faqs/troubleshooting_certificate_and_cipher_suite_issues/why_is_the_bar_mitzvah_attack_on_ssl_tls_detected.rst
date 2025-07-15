:original_name: waf_01_3312.html

.. _waf_01_3312:

Why Is the Bar Mitzvah Attack on SSL/TLS Detected?
==================================================

The Bar Mitzvah attack is a cryptographic attack targeting SSL/TLS protocols. The attack exploits a vulnerability in the RC4 cryptographic algorithm. This vulnerability can disclose ciphertext in SSL/TLS encrypted traffic in some cases, such as passwords, credit card data, or other privacy data, to hackers.

Solution
--------

To solve this problem, you can set the minimum TLS version to TLS v1.2 and cipher suite to cipher suite 2.
