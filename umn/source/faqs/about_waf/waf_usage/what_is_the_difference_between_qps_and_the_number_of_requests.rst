:original_name: waf_01_0179.html

.. _waf_01_0179:

What Is the Difference Between QPS and the Number of Requests?
==============================================================

Queries Per Second (QPS) indicates the number of requests per second. For example, an HTTP GET request is also called a query. The number of requests is the total number of requests in a specific time range.

Queries Per Second (QPS) is the number of requests a server can handle per second.

.. note::

   QPS is used to measure the number of queries, or requests, per second.

For details about QPS on the **Dashboard** page, see :ref:`Table 1 <waf_01_0179__table48681616133812>`.

.. _waf_01_0179__table48681616133812:

.. table:: **Table 1** QPS calculation

   +----------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | Time Range                 | Average QPS Description                                                                                            | Peak QPS Description                                            |
   +============================+====================================================================================================================+=================================================================+
   | **Yesterday** or **Today** | The QPS curve is made with the average QPSs in every minute.                                                       | The QPS curve is made with each peak QPS in every minute.       |
   +----------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | **Past 3 days**            | The QPS curve is made with the average QPSs in every five minutes.                                                 | The QPS curve is made with each peak QPS in every five minutes. |
   +----------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | **Past 7 days**            | The QPS curve is made with the maximum value among the average QPSs in every five minutes at a 10-minute interval. | The QPS curve is made with each peak QPS in every 10 minutes.   |
   +----------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | **Past 30 days**           | The QPS curve is made with the maximum value among the average QPSs in every five minutes at a one-hour interval.  | The QPS curve is made with the peak QPSs in every hour.         |
   +----------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
