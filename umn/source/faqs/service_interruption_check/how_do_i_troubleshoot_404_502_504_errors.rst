:original_name: waf_01_0066.html

.. _waf_01_0066:

How Do I Troubleshoot 404/502/504 Errors?
=========================================

If an error, such as 404 Not Found, 502 Bad Gateway, or 504 Gateway Timeout, occurs after a domain name is connected to WAF, use the following methods to locate the cause and remove the error:

404 Not Found
-------------

**Scenario 1**: When a visitor accesses your website, the page shown in :ref:`Figure 1 <waf_01_0066__fig197965218316>` is displayed.

.. _waf_01_0066__fig197965218316:

.. figure:: /_static/images/en-us_image_0169130550.png
   :alt: **Figure 1** 404 page

   **Figure 1** 404 page

**Cause**: The port added to a URL is incorrect.

-  A non-standard port is configured when a domain name is connected to WAF. No port is added or the origin server port instead of the non-standard port is used to access the website. For example, use **https://www.example.com** or **https://www.example.com:80** to access the website.

   **Solution**: Add the non-standard port to the URL and access the origin server again, for example, **https://www.example.com:8080**.

-  No non-standard port is configured when a domain name is added to WAF. A non-standard port or the origin server port is used to access the website. For example, use **https://www.example.com:8080** to access the website.

   .. note::

      If no non-standard port is configured, WAF protects services on port 80/443 by default. To protect services on other ports, re-configure domain settings.

   **Solution**: The domain name needs to be accessed directly. For example, **https://www.example.com**.

**Scenario 2**: When a visitor accesses your website, another 404 error page is displayed instead of the page shown in :ref:`Figure 1 <waf_01_0066__fig197965218316>`.

**Cause**: The website does not exist or has been deleted.

**Solution**: Check your website.

502 Bad Gateway
---------------

**Scenario**: Website access is normal after the WAF configuration is complete. However, after a certain period of time, a 502 Bad Gateway error is reported frequently.

.. note::

   If your web server is not deployed on the cloud, consult your server provider about whether the server has default block settings. If there are default block settings, ask the service provider to remove them.

Possible causes are as follows:

-  **Cause 1**: Your website is using another security protection software. The software considers back-to-source IP addresses of WAF as malicious and blocks the requests forwarded by WAF. As a result, the site becomes inaccessible.

   **Solution**: Add the WAF IP address ranges to the whitelist of the firewall (hardware or software), security protection software, and rate limiting module.

-  **Cause 2**: Multiple backend servers are configured. However, one backend server is unreachable.

   Perform the following steps to check whether the origin server configuration is correct:

   #. Log in to the management console, click **Service List** in the upper part of the page, and choose **Security** > **Web Application Firewall (Dedicated)**.

   #. In the navigation pane, choose **Website Settings**.

   #. In the **Protected Website** column, click the domain name to go to the **Basic Information** page.

   #. In the **Server Information** area, click |image1|. On the displayed page, check whether the client protocol, server protocol, origin server address, and port used by the origin server are correct.

   #. Run the **curl** command on the host to check whether each origin server can be properly accessed.

      .. code-block::

         curl http://xx.xx.xx.xx:yy -kvv

      *xx.xx.xx.xx* indicates the IP address of the origin server. *yy* indicates the port of the origin server. *xx.xx.xx.xx* and *yy* must belong to the same origin server.

      .. note::

         -  The host where the **curl** command can be run must meet the following requirements:

            -  The network communication is normal.
            -  The **curl** command has been installed. `curl <https://curl.haxx.se/>`__ must be manually installed on the host running the Windows operating system. **curl** is installed along with other operating systems.

         -  You can also enter **http://origin server address:origin server port** in the address bar of the browser to check whether the origin server can be properly accessed.

      If **connection refused** is displayed, the origin server is unreachable and website cannot be accessed. Perform the following operations:

      -  Check whether the server is running properly. If it is not, restart the server.
      -  Add the WAF IP address ranges to the whitelist of the firewall (hardware or software), security protection software, and rate limiting module.

-  **Cause 3**: Origin server performance

   **Solution**: Contact your website owner to rectify the fault.

504 Gateway Timeout
-------------------

**Scenario**: After the configuration of connecting a domain name to WAF is complete, your website works properly. However, with the increasing traffic volume, the number of 504 errors also increases. If you directly access the IP address of the origin server, the 504 error code is returned sometimes.

The possible causes are as follows:

-  **Cause 1**: Backend server performance issues (such as too many connections or high CPU usage)

   **Solution**:

   #. Optimize the server configuration, including TCP network parameters and ulimit parameters.

   #. To handle large-scale service increase, use method 1 or method 2 to perform the processing.

      **Method 1**: Add a backend server group to the ELB load balancer.

      **Method 2**: Create an ELB. Use the EIP of ELB as the IP address of the server to connect to WAF.

      a. Log in to the management console, click **Service List** in the upper part of the page, and choose **Security** > **Web Application Firewall (Dedicated)**.
      b. In the navigation pane, choose **Website Settings**.
      c. In the **Protected Website** column, click the domain name to go to the **Basic Information** page.
      d. In the **Server Information** area, click |image2|. On the displayed page, click **Add**.

   #. If the **Client Protocol** is **HTTPS**, you can use HTTPS on the WAF side. However, it is recommended that **HTTP** (**Server Protocol**) to forward the requests to your web server, lowering the computational demands on backend servers.

-  **Cause 2**: The WAF back-to-source IP addresses are not whitelisted or your origin server port is not enabled.

   **Solution**: Whitelist the WAF back-to-source IP addresses in the corresponding ECS security groups.

-  **Cause 3**: The origin server has a firewall and the firewall blocks the WAF IP addresses.

   **Solution**: Whitelist the WAF back-to-source IP addresses in the corresponding ECS security groups or uninstall the firewall software except WAF.

-  **Cause 4**: Connection timeout and read timeout

   **Solution**

   -  Database queries are slow.

      -  Tune services to shorten the query duration and improve user experience.
      -  Modify the request interaction mode so that the persistent connection can have some data transmitted within 60 seconds, such as ACK packets, heartbeat packets, keep-alive packets, and other packets that can keep the session alive.

   -  It takes a long time to upload large files.

      -  Tune services to shorten the file upload time.
      -  An FTP server is recommended for file upload.
      -  Upload the file through an IP address or a domain name that is not protected by WAF.
      -  The default timeout period for a dedicated WAF instance to respond origin servers is 180s.

   -  The origin server is faulty.

      Check whether the origin server works properly.

-  **Cause 5**: The bandwidth of the origin server exceeds the upper limit.

   **Solution**: Increase the bandwidth of the origin server.

.. |image1| image:: /_static/images/en-us_image_0167644254.jpg
.. |image2| image:: /_static/images/en-us_image_0167644254.jpg
