# Edge Application
Edge Application is a product that lets you build web applications on Azion Edge Network, reducing latency and throughput between origin servers and users. You can define how your content will be cached, execute functions and business rules, and optimize content delivery for your users.

Learn how to create an edge application in the getting started guide.

How it works
Edge Caching
Delivery
3.1. Delivery protocols
3.2. Ports
Minimum TLS Version
Ciphers
Edge Application Modules
Related documentation
1. How it works
Edge Application works with a reverse proxy architecture. When you build an application in Real-Time Manager (RTM) and point the traffic from your domain to Azion, your users will access your application through our highly distributed global network of edge nodes.

See the documentation on Domains for more information on how to associate a domain to an edge application.

Then, Azion selects which edge node closest to the user can handle the request, reducing latency and speeding up content transfer and downloads.

In this architecture, your content or web application has to be available from an origin, which can be one or more web servers in your infrastructure, a cloud service, or one of Azion Origin Services.

See the documentation on Single Origin and Load Balancer to find out more about how to set up one or multiple origins.

To configure Edge Application, follow these steps:

Access RTM.
Go to Products menu > Edge Application.
Select an existing application from the list or create a new one.
Configure your edge application.
Click the Save button to save your settings.
2. Edge Caching
Through Edge Caching, Azion’s highly distributed global network allows you to deliver your content much more efficiently. Content that is successfully cached – cache hit – on Azion’s edge nodes can be delivered directly to your users from the nearest Edge Node, without having to access the origin. In addition to increasing performance and scalability for your content, you can reduce costs on your origin infrastructure.

A cache miss occurs when content is requested and it isn’t in cache. The Edge Caching module minimizes the effect of cache miss by maintaining a keep-alive connection with the origin whenever possible, avoiding the overhead of the TCP/IP handshake. Regardless of the volume of simultaneous requests made to Azion’s Edge Nodes, each Edge Node will search the content at the origin only once per cache miss, which substantially reduces the impact on your infrastructure.

3. Delivery
3.1. Delivery Protocols
You can customize the delivery of your application by choosing the following options:

HTTP: delivers your application using only the HTTP protocol.
HTTP & HTTPS: delivers your application using the HTTP and HTTPS protocols.
If you choose to deliver your application through HTTP & HTTPS, you must define a minimum TLS version and set up Digital Certificates for your domain.

3.2. Ports
Azion allows you to choose which HTTP and HTTPS ports your application will use. You must choose at least one port from the available ports for each protocol selected.

The simultaneous multiport solution allows you to choose from all available ports, including non-default ones, for simultaneous delivery.

List of available ports
HTTP Port	HTTPS Port
80 (default)	443 (default)
8080	8443
8008	9440
 	9441
 	9442
 	9443
4. Minimum TLS version
The Transport Layer Security (TLS) protocol allows you to encrypt web traffic. The following TLS versions can be used with edge applications:

TLS 1.0 (deprecated)
TLS 1.1 (deprecated)
TLS 1.2
TLS 1.3
You can choose the minimum version of TLS that will be supported by your edge application. By choosing recent versions of the protocol, older devices or browsers might not be able to access the edge application.

Azion blocks TLS Renegotiation and TLS Resumption by default. If you want to customize this setup, contact our Sales team.

5. Ciphers
Ciphers are cryptography algorithms utilized to encrypt plaintext into ciphertext, which requires a key to be decrypted. Azion gives you the possibility to change the cipher suite your edge application will use in order to protect your application against SSL/TLS attacks.

The cipher suite will determine which cryptographic algorithms will be used in the SSL/TLS connections of your edge application. Both, client and server, will negotiate the cipher suite to securely encrypt and decrypt the data exchanged during the session.

To set the cipher suite of your Edge Application:

Access RTM.
Open the Products Menu, indicated by the three horizontal lines.
Click Edge Application.
Select an existing application or click the Add application button to create a new one.
In the Main Settings tab, in the dropdown list Supported Ciphers list, select the cipher suite desired.
The table below shows the ciphers available in each cipher suite.

| Cipher | TLSv1.2_2018 | TLSv1.2_2019 | TLSv1.2_2021 | TLSv1.3_2022 |
|--------|--------------|--------------|--------------|--------------|
| TLS_AES_128_GCM_SHA256 | ✔︎ | ✔︎ | ✔︎ | ✕ |
| TLS_AES_256_GCM_SHA384 | ✔︎ | ✔︎ | ✔︎ | ✕ |
| TLS_CHACHA20_POLY1305_SHA256 | ✔︎ | ✔︎ | ✔︎ | ✕ |
| ECDHE-ECDSA-AES128-GCM-SHA256 | ✔︎ | ✔︎ | ✔︎ | ✔︎ |
| ECDHE-ECDSA-AES256-GCM-SHA384 | ✔︎ | ✔︎ | ✔︎ | ✔︎ |
| ECDHE-ECDSA-CHACHA20-POLY1305 | ✔︎ | ✔︎ | ✔︎ | ✔︎ |
| ECDHE-RSA-AES128-GCM-SHA256 | ✔︎ | ✔︎ | ✔︎ | ✔︎ |
| ECDHE-RSA-AES256-GCM-SHA384 | ✔︎ | ✔︎ | ✔︎ | ✔︎ |
| ECDHE-RSA-CHACHA20-POLY1305 | ✔︎ | ✔︎ | ✔︎ | ✔︎ |
| ECDHE-ECDSA-AES256-SHA384 | ✔︎ | ✔︎ | ✕ | ✕ |
| ECDHE-ECDSA-AES128-SHA256 | ✔︎ | ✔︎ | ✕ | ✕ |
| ECDHE-RSA-AES128-SHA256 | ✔︎ | ✔︎ | ✕ | ✕ |
| ECDHE-RSA-AES256-SHA384 | ✔︎ | ✔︎ | ✕ | ✕ |
| AES128-SHA256 | ✔︎ | ✕ | ✕ | ✕ |
| AES256-GCM-SHA384 | ✔︎ | ✕ | ✕ | ✕ |
| AES128-GCM-SHA256 | ✔︎ | ✕ | ✕ | ✕ |
| DHE-RSA-AES128-GCM-SHA256 | ✕ | ✕ | ✔︎ | ✔︎ |
| DHE-RSA-AES256-GCM-SHA384 | ✕ | ✕ | ✔︎ | ✔︎ |
| DHE-RSA-CHACHA20-POLY1305 | ✕ | ✕ | ✔︎ | ✔︎ |
| AES256-SHA256 | ✕ | ✕ | ✕ | ✕ |
| AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| AES128-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES128-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES128-SHA | ✕ | ✕ | ✕ | ✕ |
| AES128-GCM | ✕ | ✕ | ✕ | ✕ |
| AES256-CBC-SHA | ✕ | ✕ | ✕ | ✕ |
| AES256-CBC | ✕ | ✕ | ✕ | ✕ |
| AES128-CBC-SHA | ✕ | ✕ | ✕ | ✕ |
| AES128-CBC | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-CHACHA20-POLY1305-OLD | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-AES256-SHA256 | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-AES128-SHA256 | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-AES128-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES256-SHA384 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES128-SHA256 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES256-SHA384 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES128-SHA256 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES128-SHA | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-CAMELLIA256-SHA | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-CAMELLIA128-SHA | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-AES256-SHA256 | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-AES128-SHA256 | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| DHE-RSA-AES128-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-CAMELLIA256-SHA384 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-CAMELLIA128-SHA256 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES256-SHA384 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES128-SHA256 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-ECDSA-AES128-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-CAMELLIA256-SHA384 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-CAMELLIA128-SHA256 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES256-SHA384 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES128-SHA256 | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES256-SHA | ✕ | ✕ | ✕ | ✕ |
| ECDHE-RSA-AES128-SHA | ✕ | ✕ | ✕ | ✕ |

6. Edge Application Modules
In addition to caching and delivery, Azion Edge Application provides several modules that allow you to add functionality and optimize your web application. Some of these modules include:

Edge Functions: You can create custom JavaScript functions that execute on the edge nodes, enabling you to perform complex operations close to your users and reducing latency.
Bot Manager: This module detects and mitigates malicious bot traffic, protecting your application from automated threats.
WAF (Web Application Firewall): It protects your application from common web application attacks, such as SQL injection and cross-site scripting (XSS).
Image Optimization: This module automatically optimizes and delivers images in a highly efficient format, reducing their size and improving performance.
API Gateway: It enables you to manage and distribute APIs efficiently, controlling access, applying security measures, and monitoring usage.
To learn more about each module and how to configure them, refer to the Azion documentation.

7. Related documentation
To further explore Azion Edge Application and its features, you can refer to the following documentation:

Azion Edge Application
Getting Started Guide
Domains
Single Origin and Load Balancer
Edge Caching
Edge Functions
Bot Manager
WAF (Web Application Firewall)
Image Optimization
API Gateway
