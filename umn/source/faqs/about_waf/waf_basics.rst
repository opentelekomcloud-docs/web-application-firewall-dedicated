:original_name: waf_01_0150.html

.. _waf_01_0150:

WAF Basics
==========

If you are a beginner for WAF, here are some useful FAQs.

Is WAF a Hardware Firewall or a Software Firewall?
--------------------------------------------------

WAF is a software firewall.

Does WAF Affect My Existing Workloads and Server Running?
---------------------------------------------------------

Enabling WAF does not interrupt your existing workloads or affect the running status of your origin servers. No additional operation (such as shutdown or restart) on the origin servers is required.

Can a WAF Instance Be Deployed in the VPC?
------------------------------------------

Yes. You can deploy dedicated engine WAF instances in a VPC.

Does a Dedicated WAF Instance Support Cross-VPC Protection?
-----------------------------------------------------------

Dedicated WAF instances cannot protect origin servers in the VPCs that are different from where those WAF instances locate. To protect such origin servers, apply for dedicated WAF instances in the same VPC as that for the origin servers.

Which OSs Does WAF Support?
---------------------------

WAF is deployed on the cloud, which is irrelevant to an OS. Therefore, WAF supports any OS. A domain name server on any OS can be connected to WAF for protection.

Which Layers Does WAF Provide Protection At?
--------------------------------------------

WAF provides protection at seven layers, namely, the physical layer, data link layer, network layer, transport layer, session layer, presentation layer, and application layer.

How Does WAF Block Requests?
----------------------------

WAF checks both the request header and body. For example, WAF detects the request body, such as form, XML, and JSON data, and blocks requests that do not comply with protection rules.

Does WAF Support File Caching?
------------------------------

WAF caches only static web pages that are configured with web tamper protection and sends the cached web pages that are not tampered with to web visitors.

Does WAF Cache Website Data?
----------------------------

WAF protects user data on the application layer. It supports cache configuration on static web pages. When a user accesses a web page, the system returns a cached page to the user and randomly checks whether the page has been tampered with.

Can I Use WAF to Check Health Status of Servers?
------------------------------------------------

No. If you want to check health status of servers, the combination of ELB and WAF is recommended for your workloads. After you configure a load balancer in ELB, you can enable health checks for servers and use the EIP of the load balancer as the server IP address to establish connections between servers and WAF.

Does WAF Support Two-Way SSL Authentication?
--------------------------------------------

No. You can configure a one-way SSL certificate on WAF.

.. note::

   If you set **Client Protocol** to **HTTPS** when adding a website to WAF, you will be required to upload a certificate and use it for your website.

You are advised to use an ELB load balancer and dedicated WAF instances and then configure two-way authentication on the load balancer. The procedure is as follows:

#. :ref:`Apply for a dedicated WAF instance. <waf_01_1072>`
#. Connect your website to WAF and configure ELB. For details, see :ref:`Website Connection Process (Dedicated Mode) <waf_01_5249>`.
#. Configure two-way authentication on the ELB load balancer.

Does WAF Support Application Layer Protocol- and Content-Based Access Control?
------------------------------------------------------------------------------

WAF supports access control over content at the application layer. HTTP and HTTPS are both application layer protocols.

Can WAF Check the Body I Add to a POST Request?
-----------------------------------------------

The built-in detection of WAF checks POST data, and web shells are the files submitted in POST requests. WAF checks all data, such as forms and JSON files in POST requests based on the default protection policies.

You can configure a precise protection rule to check the body added to POST requests.

Can WAF Limit the Access Speed of a Domain Name?
------------------------------------------------

No. However, you can customize a CC attack protection rule to restrict access to a specific URL on your website based on an IP address, cookie, or Referer, mitigating CC attacks.

Can WAF Block URL Requests That Contain Special Characters?
-----------------------------------------------------------

No. WAF can only detect and restrict source IP addresses.

Can WAF Block Spam and Malicious User Registrations?
----------------------------------------------------

WAF cannot block business-related attacks, such as spam and malicious user registrations. To prevent these attacks, configure the registration verification mechanism on your website.

WAF is designed to keep web applications stable and secure. It examines all HTTP and HTTPS requests to detect for and block suspicious network attacks, such as Structure Query Language (SQL) injections, cross-site scripting (XSS) attacks, web shell upload, command or code injections, file inclusion, unauthorized sensitive file access, third-party vulnerability exploits, Challenge Collapsar (CC) attacks, malicious crawlers, and cross-site request forgery (CSRF).

Can WAF Block Requests for Calling Other APIs from Web Pages?
-------------------------------------------------------------

If the request data for calling other APIs on the web page is included in the domain names protected by WAF, the request data passes through WAF. WAF checks the request data and blocks it if it is an attack.

If the request data for calling other APIs on the web page is not included in the domain names protected by WAF, the request data does not pass through WAF. WAF cannot block the request data.

Can WAF Limit Access Through Domain Names?
------------------------------------------

No. WAF supports the blacklist and whitelist rules to block, log only, or permit access requests from specified IP addresses or IP address segments.

You can configure blacklist and whitelist rules to block, log only, or permit access requests from the IP addresses or IP address segments corresponding to the domain names.

Does WAF Have the IPS Module?
-----------------------------

Unlike the traditional firewalls, WAF does not have an Intrusion Prevention System (IPS). WAF supports intrusion detection of only HTTP/HTTPS requests.

Can My WAF Instances Be Automatically Scalable?
-----------------------------------------------

No.

Is There Any Impact on Origin Servers If I Enable HTTP/2 in WAF?
----------------------------------------------------------------

Yes. HTTP/2 is not supported between WAF and the origin server. This means if you enable HTTP/2 in WAF, WAF can process HTTP/2 requests from clients, but WAF can only forward the requests to origin server using HTTP 1.0/1.1. In this situation, the origin server request traffic may rise as multiplexing in HTTP/2 may become invalid for origin servers.

Does WAF Affect Email Ports or Email Receiving and Sending?
-----------------------------------------------------------

WAF protects web application pages. After your website is connected to WAF, there is no impact on your email port or email sending or receiving.

What Are Concurrent Requests?
-----------------------------

The number of concurrent requests refers to the number of requests that the system can process simultaneously. When it comes to a website, concurrent requests refer to the requests from the visitors at the same time.

Can WAF Block Requests When a Certificate Is Mounted on ELB?
------------------------------------------------------------

If the certificate is mounted on ELB, all requests sent through WAF are encrypted. For HTTPS services, you must upload the certificate to WAF so that WAF can detect the decrypted request and determine whether to block the request.

Do I Need to Make Some Changes in WAF If the Security Group for Origin Server (Address) Is Changed?
---------------------------------------------------------------------------------------------------

No modifications are required in WAF, but you are required to whitelist WAF back-to-source IP addresses on the origin servers.

How Is the Load Balanced When Multiple Origin Servers Are Configured in WAF?
----------------------------------------------------------------------------

If you have configured multiple origin server IP addresses, WAF uses the weighted round robin algorithm to distribute access requests by default. You can also customize a load balancing algorithm as required.

Does gzip on the Origin Server Affect WAF?
------------------------------------------

If gzip is enabled on the origin server, WAF may incorrectly block normal access requests from the origin server. If the blocked request is a normal access request, you can handle the event as a false alarm by referring to :ref:`Handling False Alarms <waf_01_0024>`. After an event is handled as a false alarm, WAF stops blocking corresponding type of event. No such type of event will be displayed on the **Events** page and you will no longer receive alarm notifications accordingly.

Can WAF Protect Multiple Domain Names That Point to the Same Origin Server?
---------------------------------------------------------------------------

Yes. If there are multiple domain names pointing to the same origin server, you can connect these domain names to WAF for protection.

WAF protects websites over domain names or IP addresses. If multiple domain names use the same EIP to provide services, all these domain names must be connected to WAF.

What Is a Protection IP Address?
--------------------------------

A protection IP address in WAF is the IP address of a website you use WAF to protect.

Do I Need to Add the Domain Name to WAF Again If the Domain Name IP Address Has Been Changed?
---------------------------------------------------------------------------------------------

If the IP address of the website does not change, you do not need to reconfigure it in WAF. If the website resolves a new IP address, you need to add it in WAF again.

Does WAF Support Vulnerability Detection?
-----------------------------------------

WAF enables customizable anti-crawler rules to detect and block threats such as third-party security tool vulnerability attacks. If you enable the scanner item when configuring anti-crawler rules, WAF detects scanners and crawlers, such as OpenVAS and Nmap.

Does WAF Support Protocols Used in MS Exchange?
-----------------------------------------------

WAF supports HTTP and HTTPS for logging in to Exchange on the web, but does not support mail-related protocols such as Simple Mail Transfer Protocol (SMTP), Post Office Protocol version 3 (POP3), or Internet Message Access Protocol (IMAP) used by MS Exchange.

Can WAF Defend Against XOR Injection Attacks?
---------------------------------------------

Yes. WAF can defend against XOR injection attacks.

What Is the bind_ip Parameter in WAF Logs?
------------------------------------------

After your website is connected to WAF, WAF functions as a reverse proxy between the client and the origin server. WAF examines traffic to your website, filters out malicious traffic, and forwards health traffic to your origin servers. **bind_ip** indicates the WAF back-to-source IP addresses used by WAF to forward healthy traffic.

Can WAF Protect All Domain Names Mapped to My Website IP Address If I Have Connected the IP Address to WAF?
-----------------------------------------------------------------------------------------------------------

No.

In dedicated mode, the origin server IP address can be connected to WAF, and the IP address can be a private or internal IP address. WAF protects only the traffic accessed through the IP address but cannot protect the traffic to the domain name mapped to the IP address. To protect a domain name, connect the domain name to WAF.

Can WAF Protect Websites in the C/S Architecture?
-------------------------------------------------

In the C/S architecture, WAF can protect only websites that use the layer-7 HTTP/HTTPS protocol.

Where Can I Query the Service QPS of the Current WAF Service?
-------------------------------------------------------------

You can query the inbound bandwidth or QPS quota usage of the origin server IP address on the origin server.

Can WAF Block Data Packets in multipart/form-data Format?
---------------------------------------------------------

Yes.

The multipart/form-data indicates that the browser uses a form to upload files. For example, if an attachment is added to an email, the attachment is usually uploaded to the server in multipart/form-data format.

Which CVE Vulnerabilities Can WAF Defend Against?
-------------------------------------------------

WAF can defend against the following CVE vulnerabilities: CVE-2017-7525, CVE-2019-17571, CVE-2018-1270, CVE-2016-1000027, CVE-2022-22965, CVE-2022-22968, and CVE-2018-20318.

How Do I Configure WAF If a Reverse Proxy Server Is Deployed for My Website?
----------------------------------------------------------------------------

In this case, the reverse proxy server will not be affected after the website is connected to WAF.

Can I Change the Domain Name That Has Been Added to WAF?
--------------------------------------------------------

After a domain name is added to WAF, you cannot change its name. If you want to change the protected domain name, you are advised to delete the original one and add the domain name you want to protect.

Can I Configure Multiple Load Balancers for a Dedicated WAF Instance?
---------------------------------------------------------------------

Yes. You can add a dedicated WAF instance to backend server groups of more than one load balancers.
