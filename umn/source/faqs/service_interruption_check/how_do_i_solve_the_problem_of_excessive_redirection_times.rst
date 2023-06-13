:original_name: waf_01_0117.html

.. _waf_01_0117:

How Do I Solve the Problem of Excessive Redirection Times?
==========================================================

After a domain name is connected to WAF, if the system displays a message indicating that there are excessive redirection times when a user requests to access the target domain name, the possible cause is that you have configured forcible redirection from HTTP to HTTPS on the backend server and forwarding from HTTPS (client protocol) to HTTP (server protocol) is configured on WAF, WAF is forced to redirect user requests, causing an infinite loop. You can configure two pieces of server information about HTTP (client protocol) to HTTP (server protocol) and HTTPS (client protocol) to HTTPS (server protocol).
