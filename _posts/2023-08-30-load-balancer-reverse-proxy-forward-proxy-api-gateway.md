---
layout:     post
title:      Load Balancer, Reverse Proxy, Forward Proxy, API Gateway - System design
subtitle:   
author:     NDA
header-img: img/posts/bg09.jpg
header-mask: 0.5
catalog:    true
tags:
    - System Design
---

Load Balancers, Reverse Proxies, Forward Proxies, and API Gateways are all network tools that manage traffic between clients and servers, but they serve different purposes and have unique features.

# Load Balancers

A **load balancer** is a specialized network device or software application designed to optimize the distribution of incoming network traffic across multiple servers or resources. Its primary role is to enhance the performance, availability, and reliability of applications and services by preventing any single server from becoming a bottleneck. Load balancers achieve this by employing various algorithms to route incoming requests to the most appropriate server intelligently.

Load balancers come in two main types:

* **Hardware** load balancers are dedicated physical devices optimized for high-speed data processing. They are often used in enterprise settings where performance and reliability are critical.

* **Software** load balancers, on the other hand, are more flexible and can be deployed on virtual machines or containers. They offer the advantage of being easily scalable and configurable, making them suitable for cloud-based and dynamic environments.

>It's also important to note that the role of a load balancer is not limited to just distributing traffic between clients and servers. Load balancers can also be used within a data center to balance traffic between different components of an application, such as microservices. They can even be deployed to distribute workloads across multiple databases, cache servers, or other backend services. This makes them versatile tools in various network architectures beyond the traditional client-server model.

To protect against failures, it's common to set up multiple load balancers in active-passive or active-active mode or build a hierarchy of balancers.

If setting up a complete load balancer between client and server isn't possible, load balancing can be managed on the client side. The client application receives a list of available web or application servers and initially connects to the first one to request data. Should that server repeatedly fail after a predetermined number of retries, the application discards it and moves on to the next server on the list. This approach offers a cost-effective way to implement load balancing.

## Types of Load Balancers
Based on specific needs, load balancing can be performed at the network/transport and application layer of the OSI layers:

* **Layer 4** - Operate at the Transport layer of the OSI model, dealing primarily with TCP and UDP packets. This load balancers route traffic based on source and destination IP addresses and ports. They are relatively simple, fast, and effective for routing user requests to available servers without inspecting the content of the packets. Used when needed:
High-speed data routing
Simple load distribution based on IP and port
* **Layer 7** - Operate at the Application layer and can inspect the data packets' content. This allows them to make more intelligent routing decisions based on HTTP headers, cookies, or application-specific data. Used when needed:
Content-based routing
SSL termination
Application-level decisions like directing users to a specific version of a web page
* **Layer 2/3** - Though less common, some load balancers operate at the Data Link (Layer 2) and Network (Layer 3) levels. These load balancers are generally used in specialized scenarios requiring packet-level routing. Used when needed:
MAC address-based routing (Layer 2)
IP-based routing without port considerations (Layer 3)

## Global and Local Load Balancers

Load balancing can be categorized into local and global types, each serving different scopes and use cases. Local load balancing operates within a single data center or cloud region, focusing on distributing traffic among servers in that specific location. On the other hand, global load balancing works across multiple data centers or cloud regions, often on a worldwide scale. It routes users to the nearest or best-performing data center.

### Global Server Load Balancers (GSLB)

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-ntl3t2h.png)


**GSLB**, or Global Server Load Balancing, is designed to distribute user traffic across multiple geographically dispersed data centers. Its primary purpose is to optimize user experience by reducing latency and enhancing fault tolerance. GSLB is primarily based on the Domain Name System (DNS). When a DNS query comes in for a particular domain, the GSLB-enabled DNS server doesn't just return a pre-configured IP address. Instead, it evaluates various metrics such as the geographic proximity of the user to the data centers, the health and load of the servers in those data centers, and even performance metrics like latency and packet loss. Based on these factors, the DNS server returns the IP address of the most suitable data center. This ensures that users are always directed to the optimal server, improving performance and availability.

The most common balancing use cases are:

* **DNS round-robin**: Distributes traffic between all data centers in multiple locations.
* **Failover**: Send all traffic to a primary data center, but redirect traffic to a secondary data center if the primary becomes inaccessible.
* **Geolocation-based DNS**: Detect users' locations and route traffic to the nearest data center to lower latency.

GSLB provides:

* **Disaster recovery**: Automatically reroute user traffic to an operational data center if another experiences an outage or failure.
* **Better user experience**: Route clients to the nearest data center.
* **Meet regulatory and security requirements**: Route user traffic to data centers that comply with specific legal and security standards, such as data sovereignty or GDPR.
* **Caching and Content Delivery**: Allows to get a cache of data and static content (pictures, videos) from the servers closest to the user.

**Popular Solutions**: F5 BIG-IP DNS, Citrix ADC, AWS Route 53, Cloudflare Load Balancer

### Local Load Balancers

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-0k173t1t.png)

A **Local Load Balancer** operates within a single data center or cloud region, primarily focusing on distributing incoming traffic among local servers. Its main goal is to optimize resource utilization, maximize throughput, and minimize response time. It works to intelligently route incoming requests to the most appropriate server within the local network. Doing so enhances the performance and reliability of applications and services within that specific location.

Local Load Balancer provides:

* **Traffic distribution**: Ability to direct incoming requests to specific backend servers based on specific rules.
* **Load Balancing**: Distributing incoming traffic across multiple servers to optimize resource utilization.
* **Failower**: Automatically directing traffic away from servers that are down or underperforming to maintain service availability.
* **Traffic Pattern Prediction**: Ability to forecast traffic patterns using analytics or historical traffic data.
* **Seamless Scaling**: Easily adding more servers to the server farm to handle increased traffic.

* **Popular Solutions**: HAProxy, NGINX Load Balancer, AWS Elastic Load Balancer (ELB), F5 BIG-IP Local Traffic Manager (LTM)

## Load-balancing algorithms
The choice of a load-balancing algorithm depends on the specific needs and objectives of the application or service being balanced. Different algorithms offer various advantages and trade-offs, making them more or less suitable for particular scenarios.

**Static Algorithms**

<div style="float: left; margin: 2em 2em 2em 2em;width:40%">
<img src="https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-rov3ttf.jpeg" alt="">
</div>

<p class="line-space" > <br> </p>

<p>Distributes incoming requests sequentially and evenly across all available servers cyclically.</p>

<div style="clear:both;"></div>

<div style="float: left; margin: 2em 2em 2em 2em;width:40%">
<img src="https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-7dw3the.jpeg" alt="">
</div>

<p class="line-space" > <br> </p>

<p>A hybrid approach that combines Round Robin distribution with session persistence, ensuring that once a user session is established, it remains on the assigned server.</p>

<div style="clear:both;"></div>
<div style="float: left; margin: 2em 2em 2em 2em;width:40%">
<img src="https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-sqy3trh.jpeg" alt="">
</div>

<p class="line-space" > <br> </p>

<p>Similar to Round Robin, each server is assigned a weighted score, affecting the distribution of requests. Servers with higher weights receive a larger share of the incoming requests.</p>

<div style="clear:both;"></div>
<div style="float: left; margin: 2em 2em 2em 2em;width:40%">
<img src="https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-t1103tbb.jpeg" alt="">
</div>

<p class="line-space" > <br> </p>

<p>This algorithm hashes the client's IP address to determine the server for routing the request, ensuring session persistence by always directing a specific client's requests to the same server.</p>

<div style="clear:both;"></div>

**Dynamic Algorithms**

<div style="clear:both;"></div>
<div style="float: left; margin: 2em 2em 2em 2em;width:40%">
<img src="https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-j8123ty0.jpeg" alt="">
</div>

<p class="line-space" > <br> </p>

<p>Requests are redirected to the server with the fastest average response time, balancing server load and user experience.</p>

<div style="clear:both;"></div>
<div style="float: left; margin: 2em 2em 2em 2em;width:40%">
<img src="https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-wd143tpz.jpeg" alt="">
</div>

<p class="line-space" > <br> </p>

<p>Requests are redirected to the server with the fewest active connections, requiring additional computation by the load balancer to identify less-busy servers.</p>

<div style="clear:both;"></div>

# Reverse Proxy

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-n3183tmz.png)

A **Reverse Proxy**, like a Load Balancer, is a server that sits between clients and a web server, directing incoming requests to appropriate backend servers. The key difference between a reverse proxy and a load balancer is their primary focus. While both can distribute traffic across multiple servers, a load balancer is designed explicitly for this purpose and usually offers more advanced distribution algorithms. A reverse proxy, on the other hand, provides a broader range of functionalities, such as:

* **Backend Anonymity**: Backend servers remain hidden from the external network, protecting against potential vulnerabilities.

* **DDoS Mitigation**: Many reverse proxies have built-in features to shield backend servers from distributed denial-of-service attacks, such as IP deny listing and client connection rate limiting.

* **SSL Offloading**: Handles the decryption of incoming requests and encryption of server responses, relieving backend servers from these computationally intensive tasks.

* **Data Compression**: Reduces the size of server responses for faster data transfer.

* **Response Caching**: Serves previously cached responses to identical requests, improving speed and reducing server load.

* **Direct Serving of Static Content**: Manages the delivery of static files like HTML, CSS, JavaScript, images, and videos directly to the client.

* **URL/Content Rewriting**: Modifies the URL or content before forwarding requests to the backend servers.

Reverse proxies can be helpful even with just one web server or application server, opening up the benefits described in the previous section.

**Popular Solutions**: Nginx, Apache HTTP Server (mod_proxy), HAProxy, Squid, Azure Application Gateway

# Forward Proxy

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-qk193tt4.jpeg)

A **Forward Proxy** is a server that sits between client devices and the Internet, acting as an intermediary for outgoing requests from the client. A forward proxy accepts connections from computers on a private network and forwards those requests to the public internet. It is the single exit point for subnet users accessing resources outside their private network. The key difference between a forward proxy and a reverse proxy lies in their primary roles and whom they serve. A forward proxy primarily serves the client's needs, helping it access blocked or restricted content and providing anonymity. A reverse proxy, on the other hand, is installed on the server side and manages incoming requests to the server. A forward proxy is client-focused and provides functions like:

* **Clients Anonymity**: A forward proxy conceals the client's original IP address, adding an extra layer of security during internet access.

* **Access Management**: Organizations can employ forward proxies to limit access to specific resources, safeguarding sensitive information.

* **Caching**: By caching commonly accessed resources, forward proxies can enhance client internet response times.

* **Traffic Control**: Forward proxies can manage and control network traffic flow, optimizing bandwidth usage.

* **Logging**: Forward proxies can record all outgoing requests and responses, aiding in monitoring and auditing.

**Popular Solutions**: Squid, Tinyproxy, CCProxy, WinGate

# API Gateway

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-lp1b3trm.jpeg)

An **API Gateway** is a centralized entry point that manages and routes API requests from client applications to appropriate backend services. It acts as a layer of abstraction between the client and multiple backend services, streamlining their interaction. It is a crucial component in modern architecture, especially in microservices-based systems. API gateways offer various functionalities like:

* **Routing**: Directs client-originating API requests to the suitable backend service or microservice, guided by established rules and settings.
* **Authentication and Authorization**: Manages user credentials to ensure only approved clients can access services. This includes verification of API keys, tokens, or other forms of identification.
* **Rate Limiting and Throttling**: Safeguards backend services by enforcing client request rate limits or throttling based on pre-configured policies.
* **Load Balancing**: Distributes incoming API requests across multiple service instances, enhancing the system's ability to manage a higher volume of requests and improving overall performance.
* **Caching**: Minimizes latency and backend workload by storing and reusing frequently requested responses, bypassing the need for backend queries.
* **Request and Response Transformation**: Alters incoming and outgoing data, such as data format conversions or header modifications, to maintain compatibility between clients and backend services.
* **Monitoring**: Gathers metrics and other relevant data on request and response behaviors, offering insights into microservice performance and aiding in problem identification and resolution.
* **Request and Response Validation**: Validates the structure and format of requests and responses to and from microservices, helping to prevent errors and ensure proper functionality.
* **Circuit Breaking**: Implements a circuit breaker pattern to prevent a single service failure from compromising the entire system. It monitors service health and can switch to a backup service if needed.
* **Service Discovery**: Identifies available microservices and their locations, allowing clients to interact with them without knowing their specific addresses.
* **Enhanced Security**: Enforces robust authentication and access control measures, bolstering the system's overall security against unauthorized access.

**Popular Solutions**: Kong, Amazon API Gateway, Apigee, Azure API Gateway, MuleSoft Anypoint Platform

# Conclusion
In the complex landscape of network architecture and web services, understanding the roles and functionalities of Load Balancers, Forward Proxies, Reverse Proxies, and API Gateways is crucial for effective system design and management. While each of these components serves a unique purpose, they all aim to optimize resource utilization, enhance security, and improve user experience in some form.

**Load Balancers** primarily focus on distributing incoming traffic across multiple servers to ensure no single server is overwhelmed. They are essential for scalability and high availability but are generally agnostic to the type of content being served.

**Reverse Proxies** sit in front of web servers and direct client requests to the appropriate backend server. They are server-facing and are often used for caching, SSL termination, and load distribution within an internal network.

**Forward Proxies** act as intermediaries between clients and servers, often filtering requests, providing anonymity for users, or bypassing geo-restrictions. They are client-facing and are generally used to control outbound traffic.

**API Gateways**, on the other hand, are specialized types of reverse proxies tailored for API traffic. They offer advanced functionalities like request routing, API composition, rate limiting, and security features such as authentication and authorization.

Each component has advantages and limitations, and your project's specific needs and constraints should dictate the choice between them. In many modern architectures, you'll often find a combination of these elements working to create a robust, scalable, and secure environment. Understanding their distinct roles and capabilities is the first step in making an informed decision about which to implement in your system.