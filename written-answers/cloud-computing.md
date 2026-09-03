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

   Answer: For a national submarine cable landing station, **Approach A — separate Virtual Machines — is the better choice**, because isolation and security matter more here than density.

   Core technical difference
   - A VM virtualises the HARDWARE. Each VM runs its own full guest operating system on top of a hypervisor.
   - A container virtualises the OPERATING SYSTEM. All containers share the host kernel and only package the application with its libraries.

   | Point | Virtual Machine | Container |
   |---|---|---|
   | Virtualises | Hardware | Operating system |
   | Guest OS | Own full OS per VM | Shares the host kernel |
   | Size | GBs | MBs |
   | Boot time | Minutes | Seconds |
   | Isolation | Strong — full separation | Weaker — shared kernel |
   | Overhead | High | Very low |
   | Managed by | Hypervisor (VMware ESXi, KVM, Hyper-V) | Container engine (Docker, containerd) |

   Why VMs win for this specific case
   - **Security isolation** — the station serves SEVERAL DIFFERENT ORGANIZATIONS. Each VM is fully isolated, so a compromise of the Web VM cannot reach the Database VM. With containers, a kernel-level exploit can escape to every other container on the host.
   - **Critical national infrastructure** — DNS and Network Management for international connectivity must not fail together. Full OS isolation limits the blast radius.
   - **Different OS requirements** — the database or the network management system may need a specific OS version or kernel module that containers cannot provide, since they must share the host kernel.
   - **Regulatory and audit needs** — per-organization VMs give clean boundaries for compliance and per-tenant auditing.
   - **Stable, long-running services** — DNS, database and monitoring are not deployed dozens of times a day, so the container advantage of fast start-up is not valuable here.

   When containers would be the better choice instead
   - If the five services all belonged to ONE organization, needed frequent redeployment, and had to be packed densely on limited hardware, containers would win on efficiency — 4 containers use far less RAM and CPU than 4 VMs and start in seconds.

   - A practical middle path used in real data centres: run containers INSIDE VMs. Each organization gets its own VM boundary, and inside that VM its services run as containers for easy deployment.

2. **What is Virtualization? Write down the benefits of Virtualization. Write down the top 5 virtual platform software.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 529 (ET: MIST)]*

   Answer: Virtualization is the technology that creates a software-based (virtual) version of a physical resource — a server, storage device, network or operating system — so that one physical machine can run several isolated virtual machines at the same time. A software layer called the hypervisor sits between the hardware and the virtual machines and shares the CPU, memory and disk among them.

   Benefits of virtualization
   - **Server consolidation** — one physical server replaces many under-used ones, cutting hardware cost, rack space and power consumption.
   - **Better resource utilisation** — a typical physical server runs at 10-15% utilisation; virtualization can push it to 70-80%.
   - **Isolation** — each VM is separate, so a crash or compromise in one does not affect the others.
   - **Fast provisioning** — a new server takes minutes from a template instead of weeks of procurement.
   - **Easy backup and disaster recovery** — a whole VM is a file, so it can be snapshotted, cloned and restored quickly.
   - **Live migration** — a running VM can be moved to another host with no downtime, which allows maintenance without service interruption.
   - **Testing and development** — multiple OS versions can be tested on one machine, and snapshots allow instant rollback.
   - **Foundation of cloud computing** — IaaS is virtualization offered as a service.

   Top 5 virtualization platforms
   - **VMware vSphere / ESXi** — the enterprise market leader, a Type 1 bare-metal hypervisor.
   - **Microsoft Hyper-V** — Type 1 hypervisor built into Windows Server.
   - **KVM (Kernel-based Virtual Machine)** — open source, built into the Linux kernel; the basis of most public clouds.
   - **Oracle VirtualBox** — free Type 2 hypervisor, popular for desktops and testing.
   - **Citrix Hypervisor (XenServer)** — Type 1, based on the Xen project.

3. **What is Server Virtualization? Explain with example of its.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 551 (ET: BIBM)]*

   Answer: Server virtualization is the process of dividing one physical server into several isolated virtual servers, each running its own operating system and applications as if it were a separate machine. A hypervisor sits between the hardware and the virtual servers and allocates CPU, memory, disk and network to each.

   ```mermaid
   flowchart TD
       A[Physical Server Hardware<br/>CPU, RAM, Disk, NIC] --> B[Hypervisor]
       B --> C[VM 1: Web Server<br/>Linux]
       B --> D[VM 2: Database Server<br/>Windows]
       B --> E[VM 3: Mail Server<br/>Linux]
   ```

   Example — a bank branch server room
   - Before virtualization: three physical servers, one each for the web application, the database and email. Each runs at about 12% CPU utilisation, so most of the hardware is idle, yet all three consume power, cooling and rack space.
   - After virtualization: one powerful server with a hypervisor runs all three as VMs. Utilisation rises to around 70%, two servers are eliminated, and each service is still isolated in its own OS.

   Types of server virtualization
   - Full virtualization — the guest OS is unaware it is virtualised (VMware ESXi, KVM).
   - Para-virtualization — the guest OS is modified to cooperate with the hypervisor (Xen).
   - OS-level virtualization — containers sharing one kernel (Docker, LXC).

   Benefits shown by the example
   - Lower hardware, power and cooling cost; faster provisioning of new servers; easy snapshot and restore; live migration for zero-downtime maintenance.

4. **How virtualization help physical server.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 566 (ET: N/A)]*

   Answer: Virtualization helps a physical server mainly by turning wasted capacity into useful work.

   - **Raises utilisation** — a dedicated physical server usually runs at 10-15% of its capacity. Hosting several VMs on it pushes utilisation to 70-80%, so the same hardware does far more work.
   - **Server consolidation** — ten lightly loaded physical servers can become ten VMs on one or two physical machines, cutting purchase cost, rack space, power and cooling.
   - **Isolation without extra hardware** — each workload gets its own OS and its own failure boundary, which previously required a separate box.
   - **Faster provisioning** — a new server is cloned from a template in minutes, with no procurement cycle.
   - **Simpler backup and recovery** — an entire VM is just a set of files, so snapshots and restores are quick and complete.
   - **Live migration** — running VMs move to another host, so the physical server can be shut down for maintenance without any service outage.
   - **Hardware independence** — a VM is not tied to specific hardware, so replacing or upgrading the physical server does not require reinstalling the systems.
   - **Testing and rollback** — snapshots allow a change to be undone instantly, which is impossible on bare metal.

   - The cost of these benefits is a small performance overhead from the hypervisor, and the fact that a failure of the physical host now affects every VM on it — which is why clustering and live migration are used alongside virtualization.

5. **Define a virtual machine with a neat diagram, explain the working of VM. What are the benefits of a VM?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 442 (ET: BIBM)]*

   Answer: A virtual machine (VM) is a software emulation of a complete physical computer. It has its own virtual CPU, memory, disk and network interface, and runs its own operating system, called the guest OS, completely isolated from other VMs on the same hardware.

   Diagram
   ```mermaid
   flowchart TD
       H[Physical Hardware<br/>CPU / RAM / Storage / Network] --> HY[Hypervisor - VMM]
       HY --> V1[VM 1]
       HY --> V2[VM 2]
       HY --> V3[VM 3]
       V1 --> G1[Guest OS + Applications]
       V2 --> G2[Guest OS + Applications]
       V3 --> G3[Guest OS + Applications]
   ```

   How a VM works
   - The hypervisor, also called the Virtual Machine Monitor, sits directly on the hardware or on a host OS.
   - It divides the physical CPU cores, RAM and disk into virtual slices and assigns them to each VM.
   - Each VM believes it owns real hardware; the hypervisor intercepts privileged instructions and translates them to the real hardware.
   - The hypervisor schedules the VMs onto physical CPUs, exactly as an OS schedules processes.
   - Isolation is enforced by the hypervisor, so one VM cannot read another's memory.

   Benefits of a VM
   - Runs multiple operating systems on one machine at the same time.
   - Strong isolation — a crash or infection in one VM does not affect the others.
   - Hardware independence — the VM can be moved to a different physical machine unchanged.
   - Snapshot and rollback — save the exact state and return to it instantly.
   - Efficient use of hardware and lower total cost.
   - Safe environment for testing untrusted software or new OS versions.
   - Live migration for maintenance with no downtime.

   - Drawback: each VM carries a full guest OS, so it uses more disk and RAM and boots more slowly than a container.

6. **What is docker? An application running on windows server shifted in linux server. What problem will occur? Can Docker solve it?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

   Answer:

   What Docker is
   - Docker is a containerization platform that packages an application together with all its dependencies — libraries, configuration files and runtime — into a single unit called a container image.
   - Unlike a VM, a container does not carry a guest OS. It shares the host kernel and is managed by the Docker Engine, so it is only megabytes in size and starts in seconds.

   Problems when moving a Windows application to a Linux server
   - **Binary incompatibility** — a Windows `.exe` or `.dll` will not run on Linux at all, because the executable format and system calls are different (PE vs ELF).
   - **Missing runtime and libraries** — .NET Framework, Windows-specific DLLs, COM components and the Windows registry do not exist on Linux.
   - **File path and case sensitivity** — Windows uses `C:\folder\file` and is case-insensitive; Linux uses `/folder/file` and is case-sensitive.
   - **Line endings** — CRLF on Windows versus LF on Linux breaks scripts and config parsing.
   - **Permissions model** — Windows ACLs differ completely from Linux `rwx` permissions and ownership.
   - **Services and dependencies** — IIS, Windows Services, Active Directory integration and Windows-only APIs have no direct Linux equivalent.

   Can Docker solve it?
   - **Partly, not fully.** Docker guarantees that an application runs identically wherever the container runs, which removes the "it works on my machine" class of problems — mismatched library versions, missing dependencies and configuration drift.
   - **But Docker cannot change the kernel.** A Windows container needs a Windows host kernel; a Linux container needs a Linux kernel. A Windows container simply will not run on a Linux server.
   - So the application must first be made Linux-compatible — for example by porting it from .NET Framework to .NET Core / .NET 5+, which runs cross-platform. Once it is Linux-capable, Docker packages it and makes deployment to any Linux server reliable and repeatable.

   - Summary: Docker solves the DEPENDENCY and ENVIRONMENT problem, not the PLATFORM problem. The rewrite to a cross-platform runtime is still required.

7. **What is type 2 hypervisors in virtual machine?** *[Probashi Kallyan Bank Programmer 2019 compact it 1157 (ET: AUST)]*

   Answer: A Type 2 hypervisor, also called a hosted hypervisor, is installed as an ordinary application ON TOP of an existing host operating system, rather than directly on the hardware.

   How it works
   - The stack is: Hardware → Host OS → Type 2 Hypervisor → Guest OS.
   - The hypervisor requests CPU, memory and disk from the host OS, which in turn talks to the hardware. Every hardware access therefore passes through one extra layer.

   Characteristics
   - Easy to install — it is just another program, like installing any desktop software.
   - Lower performance, because the host OS sits between the VM and the hardware.
   - Less secure, since a compromise of the host OS exposes every VM.
   - Ideal for desktops, laptops, development, testing and learning — not for production servers.

   Examples
   - Oracle VirtualBox, VMware Workstation, VMware Fusion, Parallels Desktop, QEMU (in user mode).

   | Point | Type 1 (bare metal) | Type 2 (hosted) |
   |---|---|---|
   | Installed on | Directly on hardware | On top of a host OS |
   | Performance | Near native | Lower, extra layer |
   | Security | Higher | Lower |
   | Used in | Data centres, production servers | Desktops, testing |
   | Examples | VMware ESXi, Hyper-V, Xen, KVM | VirtualBox, VMware Workstation |

8. **Explain Type 1 and Type 2 hypervisors in virtual machine operating system with figure.** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1220 (ET: N/A)]*

   Answer: A hypervisor, or Virtual Machine Monitor, is the software that creates and runs virtual machines. There are two types, distinguished by where the hypervisor sits.

   Type 1 — bare-metal hypervisor
   ```mermaid
   flowchart TD
       A[Physical Hardware] --> B[Type 1 Hypervisor]
       B --> C[Guest OS 1 + Apps]
       B --> D[Guest OS 2 + Apps]
       B --> E[Guest OS 3 + Apps]
   ```
   - Installed directly on the hardware, with no host OS underneath.
   - The hypervisor itself acts as a minimal operating system and controls the hardware directly.
   - Near-native performance, strong isolation and high security, because the attack surface is small.
   - Used in enterprise data centres and by every major cloud provider.
   - Examples: VMware ESXi, Microsoft Hyper-V, Citrix XenServer, KVM.

   Type 2 — hosted hypervisor
   ```mermaid
   flowchart TD
       A[Physical Hardware] --> B[Host Operating System]
       B --> C[Type 2 Hypervisor]
       C --> D[Guest OS 1 + Apps]
       C --> E[Guest OS 2 + Apps]
   ```
   - Installed as an application on an existing host OS such as Windows or macOS.
   - Every hardware request passes through the host OS, adding overhead.
   - Easy to install and use, but slower and less secure than Type 1.
   - Used on desktops for development, testing and running a second OS.
   - Examples: Oracle VirtualBox, VMware Workstation, Parallels Desktop.

   | Point | Type 1 | Type 2 |
   |---|---|---|
   | Position | Directly on hardware | On top of a host OS |
   | Also called | Bare metal, native | Hosted |
   | Performance | Near native | Noticeably slower |
   | Security and isolation | Strong | Weaker — depends on the host OS |
   | Installation | Complex, needs dedicated hardware | Simple, like any application |
   | Typical use | Production servers, cloud | Personal computers, labs |

## Cloud Storage & Fundamentals (6)

1. What is cloud computing? Why is it used? State the difference between cloud storage and traditional storage. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: Cloud computing is the delivery of computing services — servers, storage, databases, networking and software — over the internet on a pay-as-you-go basis, instead of owning and maintaining physical hardware.

   Why it is used
   - Removes the large upfront cost of buying servers and building a data centre.
   - Capacity can be increased or reduced within minutes as demand changes.
   - Accessible from anywhere on any internet-connected device.
   - The provider handles maintenance, patching and hardware replacement.
   - Built-in replication across data centres gives disaster recovery for free.
   - A new environment is ready in minutes instead of weeks.

   Cloud storage vs traditional storage

   | Point | Cloud storage | Traditional (local) storage |
   |---|---|---|
   | Location | Remote data centres of the provider | On-premises hard disk, SAN or NAS |
   | Access | Over the internet, from anywhere | Only from the local machine or LAN |
   | Cost model | Operating cost, pay per GB per month | Capital cost, buy the hardware upfront |
   | Scalability | Virtually unlimited, expand instantly | Limited by the hardware bought |
   | Maintenance | Handled by the provider | Handled by the organization's IT team |
   | Backup and redundancy | Automatic, replicated across sites | Must be arranged and paid for separately |
   | Internet dependency | Required | Not required |
   | Data control | Data sits with a third party | Full physical control |
   | Examples | Google Drive, Amazon S3, Dropbox, OneDrive | Internal hard disk, USB drive, office file server |

   - Cloud storage suits growing, distributed or unpredictable workloads; local storage still suits data that must never leave the premises for legal reasons.

2. **What is Cloud Computing? What are its characteristics? Briefly describe the types of cloud computing.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

   Answer: Cloud computing delivers computing resources — compute, storage, networking, databases and software — as an on-demand service over the internet, billed by usage.

   Five essential characteristics (the NIST definition)
   - **On-demand self-service** — a user provisions resources without contacting a person.
   - **Broad network access** — available over the network from any standard device.
   - **Resource pooling** — the provider's resources serve many customers, assigned and reassigned dynamically.
   - **Rapid elasticity** — capacity scales out and back in quickly, appearing unlimited to the customer.
   - **Measured service** — usage is metered, so billing matches consumption exactly.

   Types by SERVICE MODEL
   - **IaaS** — rents virtual machines, storage and networks. Examples: AWS EC2, Azure VMs.
   - **PaaS** — provides a ready platform for developing and deploying applications. Examples: Google App Engine, Heroku.
   - **SaaS** — delivers finished software over the browser. Examples: Gmail, Salesforce.

   Types by DEPLOYMENT MODEL
   - **Public cloud** — owned by a provider and shared by many customers. Cheapest and most elastic. Examples: AWS, Azure, GCP.
   - **Private cloud** — dedicated to one organization, on-premises or hosted. Most control and security, highest cost.
   - **Hybrid cloud** — combines public and private, keeping sensitive data private while bursting to public capacity when demand rises.
   - **Community cloud** — shared by several organizations with common requirements, such as a group of banks or government agencies.

3. **Explain cloud computing and evaluate its advantages and disadvantages.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

   Answer: Cloud computing means using computing resources — servers, storage, databases, networking and software — over the internet, provided on demand and paid for by usage, rather than owning the physical infrastructure.

   Advantages
   - **Cost efficiency** — capital expenditure on hardware becomes an operating expense; pay only for what is used.
   - **Scalability and elasticity** — resources expand during a peak and shrink afterwards, within minutes.
   - **Global accessibility** — reachable from anywhere, on any device with a connection.
   - **Automatic maintenance** — patching, upgrades and hardware replacement are the provider's responsibility.
   - **Reliability and disaster recovery** — data is replicated across regions, and major providers offer 99.9%+ availability SLAs.
   - **Speed to market** — a full environment is ready in minutes rather than after weeks of procurement.
   - **Collaboration** — teams work on shared data simultaneously from different locations.

   Disadvantages
   - **Internet dependency** — no connectivity means no access, a serious constraint where the network is unreliable.
   - **Security and privacy risk** — sensitive data resides on third-party infrastructure, exposed to breaches and insider threats.
   - **Limited control** — the customer cannot touch the hardware and, in SaaS, cannot even choose the software version.
   - **Vendor lock-in** — proprietary services make migrating to another provider expensive and technically hard.
   - **Downtime risk** — a provider outage affects every customer at once.
   - **Compliance and data sovereignty** — data may be stored abroad, which some regulations prohibit.
   - **Long-term cost** — for a steady, predictable workload, owning hardware can eventually be cheaper.

   - Overall evaluation: the cloud is clearly advantageous for variable, growing or geographically distributed workloads. For stable, highly regulated workloads with predictable capacity, a private or hybrid model is usually the better fit.

4. **(খ) Cloud computing কী? উহার বৈশিষ্ট্য ও সুবিধা বর্ণনা করুন ।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 616 (ET: N/A)]*

   Answer: Cloud computing is the on-demand delivery of computing services — servers, storage, databases, networking, software and analytics — over the internet, charged according to usage.

   Characteristics
   - **On-demand self-service** — resources are provisioned automatically without human interaction with the provider.
   - **Broad network access** — available over the network through standard mechanisms, from laptops, phones and tablets.
   - **Resource pooling** — the provider's compute, storage and network serve multiple customers, dynamically assigned. The customer generally does not know the physical location.
   - **Rapid elasticity** — capacity can be added or released quickly, and appears unlimited.
   - **Measured service** — usage is monitored and reported, so charging is transparent and proportional.
   - **Virtualization based** — every cloud rests on virtualization technology.
   - **Multi-tenancy** — one instance serves many customers with logical data separation.

   Advantages
   - No large upfront investment in hardware or a data centre.
   - Scales up during peaks and down afterwards, so no capacity is wasted.
   - Accessible from anywhere, which supports remote and distributed teams.
   - Maintenance, patching and upgrades are handled by the provider.
   - Automatic backup and geographic replication give strong disaster recovery.
   - New environments are ready in minutes, which speeds up projects.
   - Environmentally better, since shared data centres use resources far more efficiently than many small server rooms.

5. **What is Cloud Computing? Write its adventages and Disadventages?** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*

   Answer: Cloud computing is the delivery of IT resources — computing power, storage, databases and software — over the internet, on demand and billed by usage, instead of owning physical servers.

   Advantages
   - Low upfront cost, since no hardware has to be purchased.
   - Elastic scaling — capacity follows demand within minutes.
   - Accessible from anywhere with an internet connection.
   - Automatic updates and maintenance by the provider.
   - Strong disaster recovery through multi-region replication.
   - Rapid deployment of new services and environments.
   - Easy collaboration on shared data across locations.

   Disadvantages
   - Requires a reliable internet connection at all times.
   - Data security and privacy depend on the provider.
   - Limited control over the infrastructure and software versions.
   - Vendor lock-in makes switching providers costly.
   - A provider outage takes down all its customers together.
   - Ongoing subscription cost can exceed the cost of owning hardware over many years.
   - Legal and compliance risk when data is stored in another country.

   - Practical guidance: use the cloud for variable or fast-growing workloads, and keep highly sensitive or strictly regulated data in a private or hybrid arrangement.

6. **Describe the cloud base database briefly.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

   Answer: A cloud database is a database that runs on cloud infrastructure and is accessed over the internet. The provider handles the hardware, the operating system and usually the database software itself, so the customer works only with the data and the schema.

   Two ways it is offered
   - **DBaaS (Database as a Service)** — fully managed. The provider handles installation, patching, backup, replication and scaling. Examples: Amazon RDS, Azure SQL Database, Google Cloud SQL, MongoDB Atlas.
   - **Self-managed on a cloud VM** — the customer installs MySQL or PostgreSQL on an IaaS virtual machine and manages everything except the hardware.

   Types by data model
   - **Relational (SQL)** — structured tables with ACID guarantees. Amazon RDS, Azure SQL, Cloud SQL.
   - **NoSQL** — document, key-value, column or graph stores for unstructured and very large data. DynamoDB, MongoDB Atlas, Firebase, Cassandra.
   - **Data warehouse** — optimised for analytics on huge datasets. Amazon Redshift, Google BigQuery, Snowflake.

   Advantages
   - No hardware to buy or maintain; storage and compute scale on demand.
   - Automated backup, point-in-time recovery and multi-region replication.
   - High availability through automatic failover to a standby replica.
   - Pay only for the storage and compute actually used.
   - Accessible from anywhere, which suits distributed applications.

   Disadvantages
   - Network latency compared with a database on the same LAN.
   - Sensitive data resides with a third party, raising security and compliance questions.
   - Vendor lock-in, especially with proprietary engines such as DynamoDB or BigQuery.
   - Ongoing cost grows with data volume and query traffic.

## Cluster, Grid & Distributed Computing (4)

1. **(ক) উদাহরণসহ distributed এবং centralized computing -এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer:

   Centralized computing
   - All processing, storage and control happen on a single central computer. Users connect to it through terminals or thin clients that do little or no processing themselves.
   - Example: a traditional bank mainframe. Every branch terminal sends transactions to one central mainframe, which performs all the processing and holds all the data.
   - Advantages: simple to manage and secure, data is consistent because there is only one copy, and backup is straightforward.
   - Disadvantages: a single point of failure, limited scalability, and performance degrades as users increase.

   Distributed computing
   - Processing and data are spread across many independent computers connected by a network. They coordinate with each other and appear to the user as one system.
   - Example: Google Search. A single query is answered by thousands of servers across many data centres working together. Another example is a bank with a local server in each branch that synchronises with the others.
   - Advantages: no single point of failure, scales by adding more machines, better performance through parallel work, and resources can sit close to the users.
   - Disadvantages: complex to design and debug, network dependency, and difficulty keeping data consistent across nodes.

   | Point | Centralized | Distributed |
   |---|---|---|
   | Processing location | One central machine | Many machines |
   | Failure impact | Whole system stops | Other nodes continue |
   | Scalability | Vertical only, limited | Horizontal, nearly unlimited |
   | Complexity | Low | High |
   | Cost | One powerful expensive machine | Many ordinary machines |
   | Data consistency | Easy — one copy | Hard — needs synchronisation |

2. **Difference between cluster computing and grid computing.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 750 (ET: N/A)]*

   Answer: Both connect multiple computers to work as one, but they differ in how similar the machines are and how far apart they sit.

   | Point | Cluster computing | Grid computing |
   |---|---|---|
   | Hardware | Homogeneous — same type of machines | Heterogeneous — different machines and OSes |
   | Location | Same site, connected by a fast LAN | Geographically dispersed, connected over WAN or internet |
   | Ownership | Owned and managed by ONE organization | Owned by MANY organizations |
   | Coupling | Tightly coupled | Loosely coupled |
   | Scheduling | Centralized scheduler | Distributed scheduling across domains |
   | Network speed | Very high, low latency | Slower, higher latency |
   | Task type | One large task split across nodes | Many independent tasks distributed to volunteers |
   | Example | A university HPC cluster; a web server farm behind a load balancer | SETI@home, Folding@home, World Community Grid |

   - Cluster computing suits tightly coupled problems such as weather simulation, where nodes must exchange data constantly.
   - Grid computing suits embarrassingly parallel problems, where each task is independent and can be sent anywhere, tolerating slow links.
   - Cloud computing borrowed from both: it uses clusters inside a data centre and grid-like distribution across regions, adding virtualization and pay-per-use billing.

3. **Imagine data in a system is green, red, yellow and blue in the system using distributed server in parallel. Design the system using reduce map.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*

   Answer: MapReduce processes large data in parallel across many servers in two phases — Map produces key-value pairs, and Reduce aggregates the values for each key. Counting the occurrences of the colours green, red, yellow and blue fits this model exactly.

   ```mermaid
   flowchart LR
       I[Input data split into blocks] --> M1[Mapper 1]
       I --> M2[Mapper 2]
       I --> M3[Mapper 3]
       M1 --> S[Shuffle and Sort<br/>group by colour]
       M2 --> S
       M3 --> S
       S --> R1[Reducer: green]
       S --> R2[Reducer: red]
       S --> R3[Reducer: yellow, blue]
       R1 --> O[Final counts]
       R2 --> O
       R3 --> O
   ```

   Step 1 — Split
   - The dataset is divided into blocks and each block is sent to a different server.

   Step 2 — Map phase (runs in parallel on every server)
   ```
   map(key, record):
       colour = record.colour
       emit(colour, 1)
   ```
   - Mapper 1 output: `(green,1) (red,1) (green,1)`
   - Mapper 2 output: `(blue,1) (yellow,1) (red,1)`
   - Mapper 3 output: `(green,1) (blue,1)`

   Step 3 — Shuffle and Sort
   - All pairs with the same key are grouped and sent to the same reducer.
   - `green → [1,1,1]`, `red → [1,1]`, `yellow → [1]`, `blue → [1,1]`

   Step 4 — Reduce phase
   ```
   reduce(colour, list_of_counts):
       total = sum(list_of_counts)
       emit(colour, total)
   ```

   Final output

   | Colour | Count |
   |---|---|
   | green | 3 |
   | red | 2 |
   | yellow | 1 |
   | blue | 2 |

   - Why this scales: the Map phase is fully parallel with no communication between mappers, so doubling the servers roughly halves the time.
   - An optional Combiner running on each mapper (a local reduce) would cut network traffic during the shuffle by pre-summing counts.
   - Implementations: Apache Hadoop MapReduce and Apache Spark.

4. **(খ) Distributed processing কী? উহার বৈশিষ্ট্য ও সুবিধাগুলো লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1094 (ET: N/A)]*

   Answer: Distributed processing means dividing a computing task among several computers connected by a network, so that they work on it simultaneously and appear to the user as a single system.

   Characteristics
   - **Resource sharing** — CPU, storage, printers and data are shared across the network.
   - **Concurrency** — many nodes execute parts of the work at the same time.
   - **Transparency** — the user sees one system and does not know which node did the work or where the data lives.
   - **Scalability** — capacity grows by adding more nodes.
   - **Fault tolerance** — the failure of one node does not stop the whole system.
   - **Openness and heterogeneity** — nodes may run different hardware and operating systems, communicating through standard protocols.
   - **No global clock** — nodes coordinate by message passing, which is why distributed algorithms are hard.

   Advantages
   - Higher performance through genuine parallel execution.
   - Reliability — redundancy means the system survives individual failures.
   - Economy — many ordinary machines cost less than one very powerful one.
   - Incremental growth — add nodes as demand rises, without replacing anything.
   - Geographic distribution — processing sits close to the users, reducing latency.
   - Better resource utilisation, since idle capacity on one node serves another.

   Disadvantages worth noting
   - Complex to design, program and debug.
   - Depends entirely on the network; a partition can split the system.
   - Keeping data consistent across nodes is difficult — the CAP theorem forces a trade-off between consistency and availability.
   - Security is harder, because data travels over the network and there are more points to protect.

## Scalability (Horizontal & Vertical Scaling) (2)

1. **Server rack digram to draw horizontal and vertical scalling.** *[RPGCL Assistant Manager (ICT) 2022 compact it 655 (ET: BUET)]*

   Answer: Vertical scaling makes ONE server bigger; horizontal scaling adds MORE servers.

   Vertical scaling (scale up) — same rack slot, stronger machine
   ```
   BEFORE                          AFTER
   +----------------------+        +----------------------+
   |  Server 1            |        |  Server 1            |
   |  4 CPU cores         |  --->  |  16 CPU cores        |
   |  8 GB RAM            |        |  64 GB RAM           |
   |  500 GB SSD          |        |  2 TB SSD            |
   +----------------------+        +----------------------+
        (one machine)                  (same one machine,
                                        upgraded hardware)
   ```

   Horizontal scaling (scale out) — more machines behind a load balancer
   ```
   BEFORE                    AFTER
                                    +----------------+
                                    | Load Balancer  |
                                    +--+----+----+---+
                                       |    |    |
   +--------------+           +--------+ +--+---+ +--------+
   |  Server 1    |   --->    |Server 1| |Server2| |Server 3|
   |  4 CPU, 8 GB |           |4CPU 8GB| |4CPU8GB| |4CPU 8GB|
   +--------------+           +--------+ +-------+ +--------+
    (one machine)                    (three identical machines
                                      sharing the traffic)
   ```

   | Point | Vertical scaling (scale up) | Horizontal scaling (scale out) |
   |---|---|---|
   | Method | Add CPU, RAM, disk to one server | Add more servers |
   | Limit | Bounded by the largest machine available | Practically unlimited |
   | Downtime | Usually needed to upgrade hardware | None — new nodes join live |
   | Cost | Rises steeply for high-end hardware | Uses many commodity machines |
   | Complexity | Simple, no code change | Needs a load balancer and stateless design |
   | Fault tolerance | Poor — still a single point of failure | Good — other nodes survive a failure |
   | Suitable for | Databases, legacy applications | Web servers, microservices, cloud apps |

   - Cloud platforms favour horizontal scaling because it is elastic — instances are added automatically during a traffic peak and removed afterwards.

2. **Difference between elasticity and scalability of resources in the cloud.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 749 (ET: N/A)]*

   Answer: Both describe growth of capacity, but scalability is about long-term CAPABILITY while elasticity is about short-term AUTOMATIC adjustment.

   Scalability
   - The ability of a system to handle a growing workload by adding resources.
   - Usually planned and often manual, responding to predicted long-term growth.
   - Two forms: vertical (a bigger machine) and horizontal (more machines).
   - Example: a bank expects 50% more customers next year, so it plans to add servers over the coming months.

   Elasticity
   - The ability to automatically add and REMOVE resources in real time as demand rises and falls.
   - Fully automatic, driven by monitoring rules such as "if CPU exceeds 70% for 5 minutes, add an instance".
   - Includes shrinking back, which pure scalability does not.
   - Example: an e-commerce site automatically runs 20 servers during an Eid sale and drops back to 4 servers the next week.

   | Point | Scalability | Elasticity |
   |---|---|---|
   | Definition | Capability to grow with demand | Automatic real-time expansion and contraction |
   | Direction | Mainly one way — grow | Both ways — grow and shrink |
   | Timing | Planned, long term | Immediate, short term |
   | Trigger | Human decision or capacity planning | Automated monitoring rules |
   | Cost effect | Capacity is retained and paid for | Pay only for what is running at that moment |
   | Applies to | Both on-premises and cloud | Essentially a cloud property |

   - Relationship: elasticity requires scalability. A system must be scalable before it can be made elastic, but a scalable system is not automatically elastic.
   - AWS Auto Scaling Groups, Azure Virtual Machine Scale Sets and Kubernetes Horizontal Pod Autoscaler are elasticity mechanisms.

## Edge Computing & Fog Computing (2)

1. **What is the need of edge server?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*

2. **(গ) Edge Computing এর ধারণা সংক্ষেপে উপস্থাপন করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

## Virtualization & Resource Allocation (1)

1. A physical server has 32 CPU cores, 96\text{ GB} RAM, and 4\text{ TB} storage. Each virtual machine (VM) requires 4 CPU cores, 16\text{ GB} RAM, and 500\text{ GB} storage. Calculate the maximum number of VMs that can be hosted on the server without overcommitting resources. Identify which hardware resource limits the number of VMs. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

## High Availability & System Redundancy (1)

1. High-Availability Design: [BSCCPL AME 21-08-2026 (BUET)] A submarine cable operator wants to ensure that a DNS service remains available even if one physical server fails. where VM/container technology helps and where network redundancy is required.

## Cloud Security & Compliance (1)

1. **How do assessment and audit reports help detect vulnerabilities and ensure compliance to cloud security posture?** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1431 (ET: BUET)]*
