<!-- TOC START -->
**Table of Contents** — 9 subtopics · 38 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Cloud Service Models](#cloud-service-models-13) | 13 |
| 2 | [Virtualization & Containers (VM vs Container)](#virtualization--containers-vm-vs-container-8) | 8 |
| 3 | [Cloud Storage & Fundamentals](#cloud-storage--fundamentals-6) | 6 |
| 4 | [Cluster, Grid & Distributed Computing](#cluster-grid--distributed-computing-4) | 4 |
| 5 | [Scalability (Horizontal & Vertical Scaling)](#scalability-horizontal--vertical-scaling-2) | 2 |
| 6 | [Edge Computing & Fog Computing](#edge-computing--fog-computing-2) | 2 |
| 7 | [Virtualization & Resource Allocation](#virtualization--resource-allocation-1) | 1 |
| 8 | [High Availability & System Redundancy](#high-availability--system-redundancy-1) | 1 |
| 9 | [Cloud Security & Compliance](#cloud-security--compliance-1) | 1 |

<!-- TOC END -->

---

## Cloud Service Models (13)

1. A startup company wants to launch a new web application. They do not want to manage any underlying hardware, operating systems, or even the runtime environment; they only want to focus on writing and deploying their code. Based on your understanding of Cloud Service Models, which model (IaaS, PaaS, or SaaS) is most appropriate for them? Provide two real-world examples of platforms that provide this specific type of service. [SO IT 25-07-2026]

   Answer: **PaaS (Platform as a Service)** is the right model.

   Why PaaS fits exactly
   - The startup wants to write and deploy code only, and PaaS provides a ready-made platform where the provider manages servers, storage, operating system and runtime environment.
   - IaaS would still leave them managing the operating system, patching and the runtime — which they explicitly do not want.
   - SaaS is finished software for end users, so there is nowhere to deploy their own application code.

   | Model | What they would manage | Suitable here? |
   |---|---|---|
   | IaaS | OS, runtime, application, data | No — too much management |
   | PaaS | Application code and data only | Yes |
   | SaaS | Nothing — just use the software | No — cannot deploy own code |

   Two real-world PaaS platforms
   - **Google App Engine** — upload the code and Google handles servers, scaling and patching automatically.
   - **AWS Elastic Beanstalk** — upload the application and AWS provisions capacity, load balancing, auto-scaling and health monitoring.
   - Others in the same category: Microsoft Azure App Service, Heroku, Red Hat OpenShift.

   - Trade-off to note: PaaS reduces customisation of the underlying infrastructure and creates some vendor lock-in, which is usually an acceptable price for a small startup.

2. What is cloud computing? Mention its service models. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

   Answer: Cloud computing is the delivery of computing services — servers, storage, databases, networking, software and analytics — over the internet, on a pay-as-you-go basis, instead of owning and running physical hardware.

   Essential characteristics
   - On-demand self-service, broad network access, resource pooling, rapid elasticity and measured service (pay per use).

   Three service models
   - **IaaS (Infrastructure as a Service)** — rents virtualised hardware: virtual machines, storage and networking. The customer manages the OS, runtime, applications and data. Examples: AWS EC2, Microsoft Azure VMs, Google Compute Engine.
   - **PaaS (Platform as a Service)** — provides a ready development and deployment platform. The provider manages the OS and runtime; the customer manages only the application and its data. Examples: Google App Engine, AWS Elastic Beanstalk, Heroku.
   - **SaaS (Software as a Service)** — delivers finished applications over a browser. The provider manages everything. Examples: Gmail, Google Docs, Salesforce, Microsoft 365.

   Four deployment models
   - Public cloud, private cloud, hybrid cloud and community cloud.

   - Simple way to remember the layers: IaaS gives you the land, PaaS gives you the built house, and SaaS lets you rent a furnished flat.

3. **What is SaaS and multi-tenant architecture? How are they related? What are the advantages and disadvantages of multi-tenancy? For a multi-vendor e-commerce application, you can choose a database architecture where you can put all the vendors in a single database or each vendor in a separate database. Which architecture will you follow and why?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 328 (ET: BIBM)]*

   Answer:

   (a) SaaS
   - Software as a Service delivers a complete application over the internet, accessed through a browser. The provider owns and maintains the code, infrastructure, security and updates; the customer simply subscribes and uses it.

   (b) Multi-tenant architecture
   - A single running instance of the software serves MANY customers, called tenants. Each tenant's data is logically separated so no tenant can see another's data, but the application code, servers and often the database are shared.
   - The opposite is single-tenant, where each customer gets a dedicated instance.

   (c) How they are related
   - Multi-tenancy is the architecture that makes SaaS economically viable. Without it a provider would need one full deployment per customer, and the cost per customer would never fall. Sharing one instance across thousands of tenants is what allows low subscription prices.

   Advantages of multi-tenancy
   - Much lower cost per tenant, since infrastructure is shared.
   - One codebase to maintain, so updates reach every tenant at once.
   - Efficient resource use — idle capacity of one tenant serves another.
   - Easy onboarding of a new tenant, usually just a configuration record.

   Disadvantages of multi-tenancy
   - Security risk — a bug in data isolation can leak one tenant's data to another.
   - Noisy neighbour problem — one heavy tenant can slow the others.
   - Limited customisation, since all tenants share the same code.
   - A single outage affects every tenant at once.
   - Complex compliance when tenants are in different jurisdictions.

   (d) Database choice for a multi-vendor e-commerce application

   | Approach | Pros | Cons |
   |---|---|---|
   | Single shared database with a `vendor_id` column | Cheapest, easiest to scale to many vendors, one schema to migrate | Weakest isolation; a missing `WHERE vendor_id` leaks data |
   | Separate database per vendor | Strongest isolation, easy per-vendor backup and restore, simple compliance | Expensive, hundreds of schemas to migrate, hard to run cross-vendor reports |

   - My choice: a **single shared database with a `vendor_id` column on every table**, plus row-level security enforced in the database itself.
   - Reasons: an e-commerce marketplace expects a large and growing number of vendors, most of them small. Per-vendor databases would not scale operationally — every schema change would need to run hundreds of times. Cross-vendor features such as global search, marketplace-wide reporting and shared product catalogues are natural in one database and painful across many.
   - The isolation risk is handled by enforcing `vendor_id` filtering at the data-access layer and with database row-level security policies, so a forgotten filter in application code cannot expose data.
   - Exception: a very large enterprise vendor with strict regulatory requirements can be moved to its own database — a hybrid approach that keeps the shared model for the majority.

4. **6.11 A startup company wants to launch a new web application. They do not want to manage any underlying hardware, operating systems, or even the runtime environment; they only want to focus on writing and deploying their code. Based on your understanding of Cloud Service Models, which model (IaaS, PaaS, or SaaS) is most appropriate for them? Provide two real-world examples of platforms that provide this specific type of service.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: **PaaS (Platform as a Service)** is the appropriate model.

   Justification
   - The requirement names exactly what PaaS removes — hardware, operating system and runtime environment are all managed by the provider.
   - The customer's only responsibility under PaaS is the application code and its data, which is precisely what the startup wants to focus on.
   - IaaS is ruled out because the customer would still have to install, patch and secure the operating system and runtime.
   - SaaS is ruled out because it delivers finished software; there is no way to deploy custom application code onto it.

   Responsibility split under PaaS

   | Layer | Managed by |
   |---|---|
   | Application and data | Customer (the startup) |
   | Runtime, middleware, OS | Provider |
   | Virtualisation, servers, storage, networking | Provider |

   Two real-world examples
   - **Google App Engine** — deploy code and Google handles provisioning, scaling and maintenance.
   - **AWS Elastic Beanstalk** — upload the application; AWS sets up capacity, load balancing and auto-scaling automatically.
   - Also in this category: Microsoft Azure App Service, Heroku, Red Hat OpenShift.

   - Extra benefit for a startup: PaaS scales automatically as traffic grows, so no capacity planning is needed in the early months.

5. **Describe SaaS, IaaS and PaaS.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

   Answer: These are the three cloud service models, each abstracting away a different amount of the technology stack.

   IaaS — Infrastructure as a Service
   - Provides virtualised computing resources over the internet: virtual machines, storage, networks and load balancers.
   - The provider runs the physical data centre; the customer installs and manages the OS, runtime, applications and data.
   - Most control, most responsibility. Examples: AWS EC2, Azure Virtual Machines, Google Compute Engine, DigitalOcean Droplets.

   PaaS — Platform as a Service
   - Provides a ready environment for building, testing and deploying applications.
   - The provider manages the OS, runtime, middleware and scaling; the customer manages only the application code and data.
   - Examples: Google App Engine, AWS Elastic Beanstalk, Azure App Service, Heroku.

   SaaS — Software as a Service
   - Delivers complete, ready-to-use software over a browser. Nothing is installed locally.
   - The provider manages everything — application, data storage, infrastructure, security and updates.
   - Least control, least responsibility. Examples: Gmail, Google Docs, Salesforce, Microsoft 365, Zoom, Dropbox.

   | Layer | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | Application | Customer | Customer | Provider |
   | Data | Customer | Customer | Provider |
   | Runtime, middleware | Customer | Provider | Provider |
   | Operating system | Customer | Provider | Provider |
   | Virtualisation, servers, storage, network | Provider | Provider | Provider |

6. **Explain IaaS, PaaS, and SaaS with respect to cloud computing.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*

   Answer: The three models differ in how much of the stack the cloud provider takes over.

   IaaS — the lowest layer
   - Rents raw virtualised infrastructure: compute, storage and networking.
   - Suits organisations that want full control over the OS and software but do not want to own hardware.
   - Advantages: no capital expense on servers, scales up and down on demand, full control of the environment.
   - Drawbacks: the customer must patch the OS, secure the system and manage backups.

   PaaS — the middle layer
   - Adds the operating system, runtime, database and development tools on top of the infrastructure.
   - Suits development teams that want to ship applications quickly without infrastructure work.
   - Advantages: faster development, built-in scaling, full lifecycle support from build to deploy.
   - Drawbacks: less control over the underlying environment, and vendor lock-in.

   SaaS — the top layer
   - Delivers a finished application to the end user through a browser or thin client.
   - Suits any organisation that simply needs software to work without an IT team behind it.
   - Advantages: no installation, automatic updates, subscription pricing, accessible from any device.
   - Drawbacks: little customisation, dependence on internet connectivity, and data control concerns.

   Banking example to show the difference
   - IaaS — the bank rents virtual servers and installs its own core banking software on them.
   - PaaS — the bank's developers build an internal loan-approval application and deploy it, without touching servers.
   - SaaS — the bank's staff use Microsoft 365 for email and documents, run entirely by Microsoft.

7. **What do you mean by multi-tenancy in the cloud? Why is it beneficial for cloud service providers?** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 749 (ET: N/A)]*

   Answer: Multi-tenancy means a single instance of an application and its supporting infrastructure serves multiple customers, called tenants, at the same time. Each tenant's data and configuration are kept logically separate, so no tenant can see another's data even though the underlying resources are shared.

   How isolation is achieved
   - A `tenant_id` column on every table, enforced by row-level security, or
   - A separate schema per tenant inside one database, or
   - A separate database per tenant, with the application still shared.

   Why it benefits the cloud service provider
   - **Cost efficiency** — one deployment serves thousands of customers, so infrastructure cost per customer falls dramatically.
   - **Single codebase** — one version to develop, test, patch and monitor, instead of one per customer.
   - **Instant updates** — a new feature or security fix reaches every tenant at once.
   - **Better resource utilisation** — tenants peak at different times, so idle capacity of one serves another.
   - **Fast onboarding** — adding a new tenant is a configuration record, not a new deployment.
   - **Easier scaling and monitoring** — one system to observe and tune.

   Costs the provider must accept
   - Strong data isolation must be designed in and tested constantly, since one bug can leak data across tenants.
   - The noisy neighbour problem needs rate limiting and resource quotas.
   - A single failure affects all tenants, so high availability becomes critical.

   - Multi-tenancy is what makes the low subscription prices of SaaS possible at all.

8. **(ক) Cloud Computing এর সার্ভিসগুলো লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*

   Answer: Cloud computing offers three main service models.

   - **IaaS (Infrastructure as a Service)** — virtual machines, storage, networking and load balancers rented on demand. Examples: AWS EC2, Azure VMs, Google Compute Engine.
   - **PaaS (Platform as a Service)** — a development and deployment platform including the OS, runtime and middleware. Examples: Google App Engine, AWS Elastic Beanstalk, Heroku.
   - **SaaS (Software as a Service)** — ready-made applications delivered over the browser. Examples: Gmail, Google Docs, Salesforce, Microsoft 365.

   Other "as a Service" models now in common use
   - **FaaS (Function as a Service)** / serverless — run individual functions without managing servers. Examples: AWS Lambda, Azure Functions.
   - **DaaS (Database as a Service)** — managed databases such as Amazon RDS.
   - **STaaS (Storage as a Service)** — Dropbox, Google Drive, Amazon S3.
   - **DRaaS (Disaster Recovery as a Service)** and **SECaaS (Security as a Service)**.

   Deployment models
   - Public cloud, private cloud, hybrid cloud and community cloud.

9. **Software as a Service is SaaS, Platform as a Service is PaaS and Infrastructure as a Service is IaaS. Those are three types of Cloud services. In the following table, there are some Cloud services. Write the category of those:** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819-820 (ET: BUET)]*
   Search engine for a web server
   Google Docs
   Microsoft Azure
   Drop box
   Amazon Web Services (AWS)

   Answer:

   | Cloud service | Category | Reason |
   |---|---|---|
   | Search engine for a web server | **SaaS** | A finished application used through a browser; the user manages nothing |
   | Google Docs | **SaaS** | Ready-made document software delivered over the web, no installation |
   | Microsoft Azure | **IaaS** (also offers PaaS and SaaS) | Primarily rents virtual machines, storage and networking |
   | Dropbox | **SaaS** | A complete file storage and sharing application; often called STaaS, a SaaS sub-type |
   | Amazon Web Services (AWS) | **IaaS** (also offers PaaS and SaaS) | Core offering EC2 and S3 rents raw compute and storage |

   - Note that Azure and AWS are full platforms spanning all three models — Azure VMs and AWS EC2 are IaaS, Azure App Service and Elastic Beanstalk are PaaS, and Microsoft 365 is SaaS. In an exam answer they are classified by their primary offering, which is IaaS.

10. **(c) What are the three types of services provided by the cloud?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888 (ET: N/A)]*

    Answer: The cloud provides three service types.

    - **IaaS — Infrastructure as a Service.** Rents virtualised hardware: servers, storage and networks. The customer manages the OS, runtime, applications and data. Examples: AWS EC2, Azure VMs.
    - **PaaS — Platform as a Service.** Provides a ready platform with OS, runtime and development tools. The customer manages only the application and its data. Examples: Google App Engine, Heroku.
    - **SaaS — Software as a Service.** Delivers complete applications over the internet. The provider manages everything. Examples: Gmail, Salesforce, Microsoft 365.

    | Model | Customer manages | Provider manages |
    |---|---|---|
    | IaaS | OS, runtime, app, data | Hardware, virtualisation, network |
    | PaaS | App, data | Everything below the app |
    | SaaS | Nothing but usage and settings | Everything |

11. **Write the three basic function of cloud services?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*

    Answer: The three basic functions delivered by cloud services are:

    - **Computing (processing)** — providing CPU power and memory to run applications, through virtual machines, containers or serverless functions. Delivered mainly by IaaS and PaaS.
    - **Storage** — keeping data safely and retrieving it on demand, through object storage, block storage, file storage and managed databases. Examples: Amazon S3, Google Drive, Azure Blob Storage.
    - **Networking** — connecting the resources and delivering them to users, including virtual networks, load balancers, CDNs, DNS and firewalls.

    Read another way, the three basic functions map exactly onto the three service models
    - IaaS supplies raw infrastructure, PaaS supplies a development platform, and SaaS supplies finished software.

    - Everything else the cloud offers — analytics, AI services, backup, monitoring — is built on top of these three foundations.

12. **ক্লাউড কম্পিউটিং এর সুবিধা ও অসুবিধা লিখুন।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

    Answer:

    Advantages
    - **Cost saving** — no capital spending on servers and data centres; pay only for what is used.
    - **Scalability and elasticity** — resources grow during a traffic peak and shrink afterwards, within minutes.
    - **Accessibility** — data and applications are reachable from anywhere with an internet connection, on any device.
    - **Automatic updates and maintenance** — the provider patches and upgrades the platform.
    - **Reliability and disaster recovery** — data is replicated across multiple data centres, so failures are survivable.
    - **Fast deployment** — a new server takes minutes instead of weeks of procurement.
    - **Collaboration** — several users can work on the same document or system simultaneously.

    Disadvantages
    - **Internet dependency** — no connectivity means no access, which is a real risk where the network is unreliable.
    - **Security and privacy concerns** — sensitive data sits on someone else's infrastructure.
    - **Limited control** — the customer cannot touch the underlying hardware or, in SaaS, even the software version.
    - **Vendor lock-in** — moving from one provider to another is costly and technically hard.
    - **Downtime risk** — an outage at the provider affects every customer at once.
    - **Long-term cost** — for a steady, predictable workload, owning servers can eventually be cheaper than renting.
    - **Compliance issues** — data may be stored in another country, which some regulations forbid.

13. **What is cloud computing? Mention five advantages threat of cloud computing. Describe IaaS, PaaS and SaaS.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1196 (ET: N/A)]*

    Answer:

    Cloud computing
    - The delivery of computing services — servers, storage, databases, networking and software — over the internet on a pay-per-use basis, instead of owning physical infrastructure.

    Five advantages
    - Cost saving — no upfront hardware purchase, pay only for what is consumed.
    - Scalability — capacity increases or decreases on demand within minutes.
    - Accessibility — reachable from anywhere on any internet-connected device.
    - Automatic updates — the provider handles patching and maintenance.
    - Disaster recovery — built-in replication and backup across multiple data centres.

    Five threats (security risks)
    - Data breach — sensitive data stored off-premises may be exposed.
    - Account hijacking — stolen credentials give an attacker full access.
    - Insider threat — a provider's employee could misuse access.
    - Insecure APIs — a weak management interface becomes an entry point.
    - Data loss and vendor lock-in — provider failure or migration difficulty can strand the data.
    - Also relevant: DDoS attacks and shared-technology vulnerabilities in a multi-tenant environment.

    IaaS, PaaS and SaaS
    - **IaaS** — rents virtualised hardware. The customer manages OS, runtime, applications and data. Examples: AWS EC2, Azure VMs.
    - **PaaS** — provides a ready development platform. The customer manages only the application and data. Examples: Google App Engine, Heroku.
    - **SaaS** — delivers complete software over a browser. The provider manages everything. Examples: Gmail, Salesforce, Microsoft 365.

## Virtualization & Containers (VM vs Container) (8)

1. VM vs Container in Submarine Cable Network: [BSCCPL AME 21-08-2026 (BUET)] A national submarine cable landing station provides international connectivity to several organizations. The organization wants to deploy DNS, Web, Database, Monitoring, and Network Management services on a shared physical server. The network administrator is considering two approaches:
Approach A: Deploy each service in a separate Virtual Machine.
Approach B: Deploy each service in a separate Container.
A submarine cable connects Bangladesh to an international data center. At the cable landing station, a server hosts 4 VMs, while another server runs 4 containers. Which one and why? [BSCCPL AME 21-08-2026 (BUET)]

2. **What is Virtualization? Write down the benefits of Virtualization. Write down the top 5 virtual platform software.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 529 (ET: MIST)]*

3. **What is Server Virtualization? Explain with example of its.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 551 (ET: BIBM)]*

4. **How virtualization help physical server.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 566 (ET: N/A)]*

5. **Define a virtual machine with a neat diagram, explain the working of VM. What are the benefits of a VM?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 442 (ET: BIBM)]*

6. **What is docker? An application running on windows server shifted in linux server. What problem will occur? Can Docker solve it?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

7. **What is type 2 hypervisors in virtual machine?** *[Probashi Kallyan Bank Programmer 2019 compact it 1157 (ET: AUST)]*

8. **Explain Type 1 and Type 2 hypervisors in virtual machine operating system with figure.** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1220 (ET: N/A)]*

## Cloud Storage & Fundamentals (6)

1. What is cloud computing? Why is it used? State the difference between cloud storage and traditional storage. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **What is Cloud Computing? What are its characteristics? Briefly describe the types of cloud computing.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

3. **Explain cloud computing and evaluate its advantages and disadvantages.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

4. **(খ) Cloud computing কী? উহার বৈশিষ্ট্য ও সুবিধা বর্ণনা করুন ।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 616 (ET: N/A)]*

5. **What is Cloud Computing? Write its adventages and Disadventages?** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*

6. **Describe the cloud base database briefly.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

## Cluster, Grid & Distributed Computing (4)

1. **(ক) উদাহরণসহ distributed এবং centralized computing -এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

2. **Difference between cluster computing and grid computing.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 750 (ET: N/A)]*

3. **Imagine data in a system is green, red, yellow and blue in the system using distributed server in parallel. Design the system using reduce map.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*

4. **(খ) Distributed processing কী? উহার বৈশিষ্ট্য ও সুবিধাগুলো লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1094 (ET: N/A)]*

## Scalability (Horizontal & Vertical Scaling) (2)

1. **Server rack digram to draw horizontal and vertical scalling.** *[RPGCL Assistant Manager (ICT) 2022 compact it 655 (ET: BUET)]*

2. **Difference between elasticity and scalability of resources in the cloud.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 749 (ET: N/A)]*

## Edge Computing & Fog Computing (2)

1. **What is the need of edge server?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*

2. **(গ) Edge Computing এর ধারণা সংক্ষেপে উপস্থাপন করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

## Virtualization & Resource Allocation (1)

1. A physical server has 32 CPU cores, 96\text{ GB} RAM, and 4\text{ TB} storage. Each virtual machine (VM) requires 4 CPU cores, 16\text{ GB} RAM, and 500\text{ GB} storage. Calculate the maximum number of VMs that can be hosted on the server without overcommitting resources. Identify which hardware resource limits the number of VMs. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

## High Availability & System Redundancy (1)

1. High-Availability Design: [BSCCPL AME 21-08-2026 (BUET)] A submarine cable operator wants to ensure that a DNS service remains available even if one physical server fails. where VM/container technology helps and where network redundancy is required.

## Cloud Security & Compliance (1)

1. **How do assessment and audit reports help detect vulnerabilities and ensure compliance to cloud security posture?** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1431 (ET: BUET)]*
