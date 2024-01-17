---
hide:
  - toc
---

# 禁用IPV6

目前IPV6已经进入千家万户，但有时需要禁用IPV6地址，smartdns支持如下方式禁用IPV6地址。

1. 方法一：完全禁用IPV6

    ```shell
    force-AAAA-SOA yes
    ```

1. 方法二：禁用特定域名的IPV6

    ```shell
    address /example.com/#6
    ```

1. 方法三：如需禁用特定查询端口的IPV6查询（比如第二DNS），可以配置如下

    ```shell
    bind :53 -force-aaaa-soa 
    ```

1. 例外配置：

    在开启禁用AAAA记录时，如果需要特定的例外域名，可以通过下面方式添加例外

    ```shell
    address /example.com/-
    address /example.com/-6
    ```

## 其他查询请求的禁用

1. smartdns支持对其他查询请求的禁用，对应参数为force-qtype-SOA

    ```shell
    force-qtype-SOA 28
    ```

    force-qtype-SOA参数后为DNS的类型。具体的类型，可以查询[IANA说明](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml#dns-parameters-4)

    清除指定的类型

    ```
    force-qtype-SOA -,28
    ```

    清除所有类型

    ```
    force-qtype-SOA -
    ```

## 附加说明

smartdns具备自动检测IPV6环境的能力，如果网络环境不支持IPV6，则会自动禁用IPV6相关的优化功能。
