---
hide:
  - toc
---

# Disable IPV6

Currently, IPV6 has entered thousands of households. However, in some cases, IPV6 addresses need to be disabled. Smartdns supports the following ways to disable IPV6 addresses.

1. Method 1: Completely Disable IPV6

    ```shell
    force-AAAA-SOA yes
    ```

1. Method 2: Disable IPV6 of Specific Domain Name

    ```shell
    address /example.com/#6
    ```

1. Method 3: If you need to disable IPV6 queries for a specific query port (such as the second DNS), you can configure it as follows:

    ```shell
    bind :53 -force-aaaa-soa
    ```

1. Exception configuration:

    If you disable AAAA is enabled, you can add exceptions with following options:

    ```shell
    address /example.com/-
    address /example.com/-6
    ```

## Disable Other Query Requests

1. Smartdns supports disabling other query requests, and the corresponding parameter is `force-qtype-SOA`.

    ```shell
    force-qtype-SOA 28
    ```

    After force-qtype-SOA parameter is the type of DNS. The specific types can be queried from the IANA Explanation.

    Clear specified types

    ```
    force-qtype-SOA -,28
    ```

    Clear all types

    ```
    force-qtype-SOA -
    ```

## Additional Notes

Smartdns has the ability to automatically detect IPV6 environment. If the network environment does not support IPV6, the IPV6-related optimization functions will be automatically disabled.