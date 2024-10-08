:original_name: waf_01_0059.html

.. _waf_01_0059:

WAF Operations Recorded by CTS
==============================

CTS provides records of operations on WAF. With CTS, you can query, audit, and backtrack these operations. For details, see the *Cloud Trace Service User Guide*.

.. table:: **Table 1** WAF Operations Recorded by CTS

   +-----------------------------------------------------+---------------+---------------------+
   | Operation                                           | Resource Type | Trace Name          |
   +=====================================================+===============+=====================+
   | Creating a WAF instance                             | instance      | createInstance      |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting a WAF instance                             | instance      | deleteInstance      |
   +-----------------------------------------------------+---------------+---------------------+
   | Modifying a WAF instance                            | instance      | alterInstanceName   |
   +-----------------------------------------------------+---------------+---------------------+
   | Modifying the protection status of a WAF instance   | instance      | modifyProtectStatus |
   +-----------------------------------------------------+---------------+---------------------+
   | Modifying the connection status of a WAF instance   | instance      | modifyAccessStatus  |
   +-----------------------------------------------------+---------------+---------------------+
   | Creating a WAF policy                               | policy        | createPolicy        |
   +-----------------------------------------------------+---------------+---------------------+
   | Applying a WAF policy                               | policy        | applyToHost         |
   +-----------------------------------------------------+---------------+---------------------+
   | Modifying a policy                                  | policy        | modifyPolicy        |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting a WAF policy                               | policy        | deletePolicy        |
   +-----------------------------------------------------+---------------+---------------------+
   | Uploading a certificate                             | certificate   | createCertificate   |
   +-----------------------------------------------------+---------------+---------------------+
   | Changing the name of a certificate                  | certificate   | modifyCertificate   |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting a certificate from WAF                     | certificate   | deleteCertificate   |
   +-----------------------------------------------------+---------------+---------------------+
   | Adding a CC attack protection rule                  | policy        | createCc            |
   +-----------------------------------------------------+---------------+---------------------+
   | Modifying a CC attack protection rule               | policy        | modifyCc            |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting a CC attack protection rule                | policy        | deleteCc            |
   +-----------------------------------------------------+---------------+---------------------+
   | Adding a precise protection rule                    | policy        | createCustom        |
   +-----------------------------------------------------+---------------+---------------------+
   | Modifying a precise protection rule                 | policy        | modifyCustom        |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting a precise protection rule                  | policy        | deleteCustom        |
   +-----------------------------------------------------+---------------+---------------------+
   | Adding an IP address blacklist or whitelist rule    | policy        | createWhiteblackip  |
   +-----------------------------------------------------+---------------+---------------------+
   | Modifying an IP address blacklist or whitelist rule | policy        | modifyWhiteblackip  |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting an IP address blacklist or whitelist rule  | policy        | deleteWhiteblackip  |
   +-----------------------------------------------------+---------------+---------------------+
   | Creating/updating a web tamper protection rule      | policy        | createAntitamper    |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting a web tamper protection rule               | policy        | deleteAntitamper    |
   +-----------------------------------------------------+---------------+---------------------+
   | Creating a global protection whitelist rule         | policy        | createIgnore        |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting a global protection whitelist rule         | policy        | deleteIgnore        |
   +-----------------------------------------------------+---------------+---------------------+
   | Adding a data masking rule                          | policy        | createPrivacy       |
   +-----------------------------------------------------+---------------+---------------------+
   | Modifying a data masking rule                       | policy        | modifyPrivacy       |
   +-----------------------------------------------------+---------------+---------------------+
   | Deleting a data masking rule                        | policy        | deletePrivacy       |
   +-----------------------------------------------------+---------------+---------------------+
