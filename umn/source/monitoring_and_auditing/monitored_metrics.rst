:original_name: waf_01_1372.html

.. _waf_01_1372:

Monitored Metrics
=================

Introduction
------------

This topic describes metrics reported by dedicated WAF to Cloud Eye as well as their namespaces and dimensions. You can use APIs provided by Cloud Eye to query the metrics of the monitored object and alarms generated for dedicated WAF. You can also query them on the Cloud Eye console.

namespaces
----------

SYS.WAF

.. note::

   A namespace is an abstract collection of resources and objects. Multiple namespaces can be created in a single cluster with the data isolated from each other. This enables namespaces to share the same cluster services without affecting each other.

Metrics for Dedicated WAF Instances
-----------------------------------

.. table:: **Table 1** Metrics for dedicated waf instances

   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | Metric ID                     | Metric Name                 | Description                                                                  | Value Range       | Monitored Object        | Monitoring Interval (Raw Data) |
   +===============================+=============================+==============================================================================+===================+=========================+================================+
   | cpu_util                      | CPU Usage                   | CPU usage of the monitored object                                            | 0% to 100%        | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: percentage (%)                                                         | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: 100% minus idle CPU usage percentage                      |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | mem_util                      | Memory Usage                | Memory usage of the monitored object                                         | 0% to 100%        | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: percentage (%)                                                         | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: 100% minus idle memory percentage                         |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | disk_util                     | Disk Usage                  | Disk usage of the monitored object                                           | 0% to 100%        | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: percentage (%)                                                         | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: 100% minus idle disk space percentage                     |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | disk_avail_size               | Available Disk Space        | Available disk space of the monitored object                                 | >= 0 bytes        | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: byte, KB, MB, GB, TB or PB                                             | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection mode: size of free disk space                                     |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | disk_read_bytes_rate          | Disk Read Rate              | Number of bytes the monitored object reads from the disk per second          | >= 0 byte/s       | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: byte/s, KB/s, MB/s, or GB/s                                            | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection mode: number of bytes read from the disk per second               |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | disk_write_bytes_rate         | Disk Write Rate             | Number of bytes the monitored object writes into the disk per second         | >= 0 byte/s       | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: byte/s, KB/s, MB/s, or GB/s                                            | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection mode: number of bytes written into the disk per second            |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | disk_read_requests_rate       | Disk Read Requests          | Number of requests the monitored object reads from the disk per second       | >= 0 request/s    | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: Requests/s                                                             | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection mode: number of read requests processed by the disk per second    |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | disk_write_requests_rate      | Disk Write Requests         | Number of requests the monitored object writes into the disk per second      | >= 0 request/s    | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: Requests/s                                                             | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: Number of write requests processed by the disk per second |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | network_incoming_bytes_rate   | Incoming Traffic            | Incoming traffic per second on the monitored object                          | >= 0 byte/s       | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit:                                                                        | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | byte/s, KB/s, MB/s, or GB/s                                                  |                   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: Incoming traffic over the NIC per second                  |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | network_outgoing_bytes_rate   | Outgoing Traffic            | Outgoing traffic per second on the monitored object                          | >= 0 byte/s       | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit:                                                                        | Value type: Float |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | byte/s, KB/s, MB/s, or GB/s                                                  |                   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: Outgoing traffic over the NIC per second                  |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | network_incoming_packets_rate | Incoming Packet Rate        | Incoming packets per second on the monitored object                          | >= 0 packet/s     | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit:                                                                        | Value type: Int   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | packet/s                                                                     |                   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: Incoming packets over the NIC per second                  |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | network_outgoing_packets_rate | Outgoing Packet Rate        | Outgoing packets per second on the monitored object                          | >= 0 packet/s     | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit:                                                                        | Value type: Int   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | packet/s                                                                     |                   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: Outgoing packets over the NIC per second                  |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | concurrent_connections        | Concurrent Connections      | Number of concurrent connections being processed                             | >=0 count         | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: count                                                                  | Value type: Int   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: Number of concurrent connections in the system            |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | active_connections            | Active Connections          | Number of active connections                                                 | >=0 count         | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: count                                                                  | Value type: Int   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: Number of active connections in the system                |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+
   | latest_policy_sync_time       | Latest Rule Synchronization | Time elapsed for the WAF to synchronize the latest custom rules              | >=0 ms            | Dedicated WAF instances | 1 minute                       |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Unit: ms                                                                     | Value type: Int   |                         |                                |
   |                               |                             |                                                                              |                   |                         |                                |
   |                               |                             | Collection method: Time elapsed for synchronizing to the last policies       |                   |                         |                                |
   +-------------------------------+-----------------------------+------------------------------------------------------------------------------+-------------------+-------------------------+--------------------------------+

Dimensions
----------

=============== ====================================
Key             Value
=============== ====================================
instance_id     ID of the dedicated WAF instance
waf_instance_id ID of the website protected with WAF
=============== ====================================

Example of Raw Data Format of Monitored Metrics
-----------------------------------------------

::

   [
       {
           "metric": {
                // Namespace
               "namespace": "SYS.WAF",
               "dimensions": [
                   {
                       // Dimension name, for example, protected website
                       "name": "waf_instance_id",
                       // ID of the monitored object in this dimension, for example, ID of the protected website
                       "value": "082db2f542e0438aa520035b3e99cd99"
                   }
               ],
              //Metric ID
               "metric_name": "waf_http_2xx"
           },
           // Time to live, which is predefined for the metric
           "ttl": 172800,
            // Metric value
           "value": 0.0,
          // Metric unit
           "unit": "Count",
            // Metric value type
           "type": "float",
           // Collection time for the metric
           "collect_time": 1637677359778
       }
   ]
