:original_name: waf_01_0329.html

.. _waf_01_0329:

Can WAF Protect Websites Accessed Through HSTS or NTLM Authentication?
======================================================================

Yes. WAF can protect HTTP and HTTPS applications.

-  If a website uses the HTTP Strict Transport Security (HSTS) policy, the client (such as a browser) is forced to use HTTPS to communicate with the website. This reduces the risk of session hijacking. Websites configured with HSTS policy use the HTTPS protocol. So, WAF can protect these websites.

-  Windows New Technology LAN Manager (NTLM) is an authentication method over HTTP. NTLM uses a three-way handshake to authenticate a connection. NTLM authenticates a client (such as a browser) the same way the Windows remote login authentication does.

   WAF can protect applications that use NTLM to authenticate connection between a server and client, such as a browser.
