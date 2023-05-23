---
title: Customer background and scenario
layout: page
permalink: /background/
nav_order: 2
---

## Customer background
**Contoso Healthcare** is a global network of healthcare providers with a presence throughout the industry. Contoso Healthcare wishes to drive a new **Health Checks initiative**, which specifically entails building a suite of health check applications for its 7,500 combined direct and partner network employees worldwide to use. Currently, Contoso has an old **.NET system** they developed running on servers in their data center. This .NET system use a **SQL databases** for the backend. With recent modernization efforts, they want to optimize this system to the cloud while also migrating to more cloud-native platforms.

Contoso already uses a variety of Microsoft Azure services, taking advantage of both infrastructure as a service (IaaS) and platform as a service (PaaS)offerings. Their software engineers and infrastructure team have a good working familiarity with Azure services and wish to use this opportunity to develop an innovative product that can serve as a guide for future modernization of their existing application and infrastructure.

The engineering team at Contoso Healthcare wants a modern, innovative application platform, but this is not the only key group that will be involved. Management has made clear that the **Developers** currently employed by Contoso don’t have the availability to take on all aspects of this project and that **Business analysts** will be responsible for creating the business logic and user experience for most of the Health Check applications. These business analysts are not software developers; Contoso needs a low-code/no-code approach to application development, which will enable the team to work without relying on engineering. These applications should be able to access API endpoints that the engineering team plans to build.


## Solution design considerations
Contoso architects have sketched out a high-level overview of their ideal API, but there is some disagreement within the team around the techniques they should use for endpoint design and access. 

One architect believes that an **HTTP-based REST API**, using classic endpoints like GET and POST, would be best because Contoso engineers have a fair amount of experience working with .NET MVC and Web API applications. 
A second architect would prefer a **GraphQL** approach, arguing that it is a more modern and flexible take on API design. 
Their third architect is indifferent between the two approaches but strongly prefers using the **Command and Query Responsibility Separation** (CQRS) pattern for any API design. 

The three architects have all agreed that, because they are not as familiar as they would like to be with Azure services, they will put a great deal of weight on Microsoft's advice. They're all confident that their software engineers could handle either REST or GraphQL, but want to learn about best practices, as well as understand what works best in Azure.


## Further requirements
Contoso Healthcare has spent the last few months researching products, such as Amazon Honeycode, which would allow their Business Analysts to use an Excel-like approach to build web and mobile applications. They are interested in the product but are not convinced that it's a perfect fit. Because Contoso already uses Azure for some of their needs, they are interested in reviewing **Microsoft-native** options to see if there is something that might work even better for the team than Honeycode might. 

The engineering team also wish to have all data stored in a single database, as this will simplify security and open opportunities for their data scientists to analyze the data most efficiently. In addition, they would like to centralize the management of any access points to the data. Different engineering teams will work on separate API endpoints, and they are interested in anything which can improve the coordination between teams and make their architecture group's lives easier. Contoso strongly prefers centralized solutions, and has a concern about the overlapping capabilities in Azure services. They do not want to spend time combining a lot of applications to get to Contoso’ desired solution, so the fewer the number of working parts, the better it is in her mind.

Contoso’ business analysts would like to develop additional applications to facilitate the communication between customers in the Contoso healthcare network and their healthcare providers. They aim to develop systems that `let customers input vital metrics from mobile, tablet, or desktop devices`. For mobile and tablet devices, they would like to make the Health Check applications mobile apps rather than having customers navigate to a website for data entry. This mobile application interface should be as close to native Android or iOS as possible, but Contoso does not have much experience developing mobile applications, and the engineering department would need a significant ramp-up time to move on an initiative like this, making code-heavy mobile development a non-starter at this time for Contoso Healthcare.

Although the business analysts will do much of the front-end application work, they should, as much as possible, to have the teams working in a single, collaborative environment where the engineering department can review application security, ensure that everything is configured properly, and manage costs most efficiently. They are very concerned with security breaches based on misconfiguration.

Contoso also wants to ensure that any solution should have the capability to analyze large-scale data later, as Contoso Healthcare data scientists and the clinical research staff are hoping to `perform longitudinal studies of end-user symptoms` over an extended period to test the efficacy of various treatment regimes. Their data scientists have medical records information, but that information is limited to a subset of end users who were admitted for treatment, and the opportunity to analyze data on symptoms treated outside of a healthcare facility is of great interest to them.

Through a recent audit, some violations around data security were discovered when it comes to things like HIPAA, GDPR, and CCPA. So, as they migrate, they need to ensure that the new solution meets all the requirements for data privacy. Additionally, the security team is concerned about the possibility of denial of service (DoS) or distributed denial of service attacks (DDoS), as these applications will be accessible to mobile and desktop devices without tunneling through a VPN. Before they can sign off on a potential solution, they need to know that it can successfully handle DoS or DDoS attacks. One idea they have is to limit the number of calls for a single user to no more than ten over a five-minute interval. They also want to use their own certificates and keys whenever possible.

{: .highlight }
What are the solution requirements of the Contoso health checks initiative? Brainstorm with your team and discuss the following questions.

- How to bring engineer and business analytics teams togetehr and how to define the responsibilities?
- What are the functional and non-functional requirements of the health care application? 
- How does the proposed solution meet the requirements for data privacy?
- Can the proposed solution successfully handle DoS or DDoS attacks?
- Is it possible for them to limit the number of calls for a single user to no more than ten over a five-minute interval and use their own certificates and keys whenever possible?

<!-- [CONTINUE](https://felihong.github.io/taw-power-apps-power-platform/backend_architecture/){: .btn .btn-purple .mr-2} -->
