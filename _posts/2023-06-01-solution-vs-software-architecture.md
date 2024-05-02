---
layout:     post
title:      Solution vs Software Architecture
subtitle:   This post dives into distinct architecture domains, like DevOps and data architecture, how they interconnect, and their importance in overall solution architecture.
author:     NDA
header-img: img/it/it_header06.png
header-mask: 0.5
catalog: true
tags:
    - Solution Architect
---


>In my tenure as a solution architect in financial services working for a global consulting firm, I have often questioned the best way to practice enterprise architecture.  A common challenge that many architecture consultants face is that most client firms insist on using their proprietary enterprise architecture content. I have observed that frequently such architecture content does not always distinguish between the solution and software architecture.
This article is not an academic paper. In this article, I  present my experiences and ideas to help my colleagues better understand the vague differences between two similar but distinct architecture disciplines. At the very least, this article may trigger a conversation via the comments section that may persuade me that I am wrong.


>“If I Had More Time, I Would Have Written a Shorter Letter” - Blaise Pascal.


# Solution Architecture

The term "Solution Architecture" is commonly used to describe the process of developing, documenting architecture content for a specific architecture stakeholder audience intended to enable a particular business or organizational outcome.

The solution architecture will address the needs and concerns of individual business and organizational stakeholders producing corresponding functional and non-functional requirements captured in the solution architecture document. The solution architecture document describes the target architecture within the context of relevant architecture domains such as business, data, application, technology, integration, security, etc. The solution architecture document elaborates and decomposes the target architecture into concrete architecture deliverables, also called building blocks for each architecture domain. In this article, I will use an example of a fictitious online bank loan application to segregate such concerns by each architecture domain:

![](https://dz2cdn1.dzone.com/storage/temp/6166458-solution-architecture.png)

* **Business Architecture**: describes the sequence of events and actions for each user persona to complete the online loan application 
* **Data Architecture**: defines the information scope needed to complete the loan application such as information format, source, and quality. Data architecture also addresses the concerns for private data security and integrity while ensuring performance, availability, and consistency
* **Application Architecture**: Decomposes the application into granular single responsibility UX, functional, data components that the loan account opening web or mobile apps consist of
* **Integration Architecture**: Identifies external data and functional resources, and defines the methods to interact with these resources
* **Security Architecture**: Deals with Customer Identity and Access Management (CIAM) concerns such as user registration, authentication, and password recovery
* **Technology Architecture**: Addresses the infrastructure needs for high availability and performance for:
    * compute (virtualization, containerization, serverless)
    * network (firewalls, subnets)
    * storage (object, block, file share)
* **DevOps Architecture**: Focuses on enhancing change management operations via CI/CD pipeline and application observability (logs monitoring, incident management)

The solution architecture document captures the above concerns and decisions and is presented to the project and architecture review boards to ensure that it satisfies organizational standards and the project time and cost constraints.

# Software Architecture

Once the solution architecture is defined, reviewed, and approved, the project can now transition to the build phase referred to as the SDLC phase. A software architect will now work to develop the software architecture as part of the Design Runway. The primary focus of software architecture is to define and document software structure and behavior based on known functional and non-functional requirements and enable software engineers to produce functional software. The objective here is quite different from the goal of solution architecture, which is to define the application, data, infra architecture building blocks, and dependencies. A software architect will apply software architecture styles and design patterns to outline the client and server-side software components that implement user experience (UX), functional, and data application building blocks defined in the solution architecture document. As I mentioned, the main objective of software architecture is to enable software engineering delivery. The software engineering diagrams I find most useful are the domain object model class, service component, sequence, and deployment diagrams.

![](https://dz2cdn1.dzone.com/storage/temp/6166459-software-architecture.png)

* **A Domain Object Model Class Diagram** is essential in defining the domain-driven design that ensures consistent data structure across UX, API, and backend data tiers.
* **A Services Component Diagram** breaks down the application into bounded context REST APIs that can be implemented as self-contained microservices
* **A Sequence Diagram** demonstrates how each user function is implemented by an orchestrated process made up of multiple service interactions 
* **A Deployment Diagram** is necessary to demonstrate the platform each software component is deployed on such as VMs, Kubernetes pods, or serverless lambda, and how high availability is configured across multi-availability zones.

I hope I have demonstrated how solution and software architecture are two distinct disciplines with different purposes and audiences. Can a solution architect be a software architect and vice versa? In my opinion, yes, as long as s/he knows when each discipline is appropriate.
