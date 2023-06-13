:original_name: waf_01_0457.html

.. _waf_01_0457:

How Does WAF Detect SQL Injection and XSS Attacks?
==================================================

A Structured Query Language (SQL) injection is a common web attack. The attacker injects malicious SQL commands into database query strings to deceive the server into executing commands. By exploiting these commands, the attacker can obtain sensitive information, add users, export files, or even gain the highest permissions to the database or system.

XSS attacks exploit vulnerabilities left during web page development to inject malicious instruction code into web pages so that attackers can trick visitors into loading and executing malicious web page programs attackers fabricated. These malicious web page programs are usually JavaScript, but they can also include Java, VBScript, ActiveX, Flash, or even common HTML. After an attack succeeds, the attacker may obtain various content, including but not limited to higher permissions (for example, permissions for certain operations), private content, sessions, and cookies.

How Does WAF Detect SQL Injection Attacks?
------------------------------------------

WAF detects and matches SQL keywords, special characters, operators, and comment symbols.

-  SQL keywords: union, Select, from, as, asc, desc, order by, sort, and, or, load, delete, update, execute, count, top, between, declare, distinct, distinctrow, sleep, waitfor, delay, having, sysdate, when, dba_user, case, delay, and the like
-  Special characters: ',; ()
-  Mathematical operators: **±**, **\***, **/**, **%**, and **\|**
-  Operators: **=**, **>**, **<**, **>=**, **<=**, **!=**, **+=**, and **-=**
-  Comment symbols: **-** or **/**/**

How Does WAF Detect XSS Attacks?
--------------------------------

WAF checks HTML script tags, event processors, script protocols, and styles to prevent malicious users from injecting malicious XSS statements through client requests.

-  XSS keywords (such as **javascript**, **script**, **object**, **style**, **iframe**, **body**, **input**, **form**, **onerror**, and **alert**)
-  Special characters (<, >, ', and ")
-  External links (href="http://xxx/",src="http://xxx/attack.js")

.. note::

   Rich text can be uploaded using multipart upload instead of body. In multipart upload, rich text is stored in forms and can be decoded even if it is encoded using Base64. Analyze your services and do not use quotation marks and angle brackets as far as possible.
