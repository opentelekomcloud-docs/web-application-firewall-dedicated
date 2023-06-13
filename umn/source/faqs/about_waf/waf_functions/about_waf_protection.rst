:original_name: waf_01_0181.html

.. _waf_01_0181:

About WAF Protection
====================

What Is a Protection IP Address?
--------------------------------

A protection IP address in WAF is the IP address of a website you use WAF to protect.

Does WAF Support Vulnerability Detection?
-----------------------------------------

The basic web protection function of WAF can detect and block threats such as third-party security tool vulnerability attacks. If you enable the scanner item when configuring basic web protection rules, WAF detects scanners and crawlers, such as OpenVAS and Nmap.

Does WAF Support Protocols Used in MS Exchange?
-----------------------------------------------

WAF supports HTTP and HTTPS for logging in to Exchange on the web, but does not support mail-related protocols such as Simple Mail Transfer Protocol (SMTP), Post Office Protocol version 3 (POP3), or Internet Message Access Protocol (IMAP) used by MS Exchange.

Can WAF Defend Against XOR Injection Attacks?
---------------------------------------------

Yes. WAF can defend against XOR injection attacks.

What Is the bind_ip Parameter in WAF Logs?
------------------------------------------

After your website is connected to WAF, WAF functions as a reverse proxy between the client and the origin server. WAF examines traffic to your website, filters out malicious traffic, and forwards health traffic to your origin servers. **bind_ip** indicates the WAF IP addresses used by WAF to forward healthy traffic.

Can WAF Protect All Domain Names Mapped to My Website IP Address If I Have Connected the IP Address to WAF?
-----------------------------------------------------------------------------------------------------------

No.

In dedicated mode, the origin server IP address can be connected to WAF, and the IP address can be a private or internal IP address. WAF protects only the traffic accessed through the IP address but cannot protect the traffic to the domain name mapped to the IP address. To protect a domain name, connect the domain name to WAF.
