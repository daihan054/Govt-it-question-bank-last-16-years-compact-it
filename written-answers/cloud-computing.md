<!-- TOC START -->
**Table of Contents** — 9 subtopics · 34 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Cloud Service Models](#cloud-service-models-12) | 12 |
| 2 | [Cloud Storage & Fundamentals](#cloud-storage--fundamentals-6) | 6 |
| 3 | [Virtualization & Containers (VM vs Container)](#virtualization--containers-vm-vs-container-6) | 6 |
| 4 | [Cluster, Grid & Distributed Computing](#cluster-grid--distributed-computing-3) | 3 |
| 5 | [Scalability (Horizontal & Vertical Scaling)](#scalability-horizontal--vertical-scaling-2) | 2 |
| 6 | [Edge Computing & Fog Computing](#edge-computing--fog-computing-2) | 2 |
| 7 | [Virtualization & Resource Allocation](#virtualization--resource-allocation-1) | 1 |
| 8 | [High Availability & System Redundancy](#high-availability--system-redundancy-1) | 1 |
| 9 | [Cloud Security & Compliance](#cloud-security--compliance-1) | 1 |

<!-- TOC END -->

---

## Cloud Service Models (12)

1. A startup company wants to launch a new web application. They do not want to manage any underlying hardware, operating systems, or even the runtime environment; they only want to focus on writing and deploying their code. Based on your understanding of Cloud Service Models, which model (IaaS, PaaS, or SaaS) is most appropriate for them? Provide two real-world examples of platforms that provide this specific type of service. [SO IT 25-07-2026]


   Answer: PaaS, Platform as a Service, is the most appropriate model.

   Reason:
   - The startup does not want to manage hardware, operating systems or the runtime environment. PaaS provides exactly that: the provider supplies the servers, the operating system, the runtime, the middleware and the database, and the customer supplies only the application code and its data.
   - IaaS would still leave them responsible for installing and patching the operating system and the runtime, which is precisely what they want to avoid.
   - SaaS would give them a finished application to use, not a place to deploy their own code, so it does not fit at all.
   - PaaS also gives them automatic scaling, built in deployment pipelines and managed backups, so a very small team can run a production service.

   Two real-world examples:
   - Heroku, where the developer pushes code with `git push heroku main` and the platform builds and runs it.
   - Google App Engine, which runs the application and scales it automatically according to traffic.
   - Others that would also be accepted: AWS Elastic Beanstalk, Microsoft Azure App Service and Red Hat OpenShift.
2. What is cloud computing? Mention its service models. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*


   Answer:

   - Cloud computing is the delivery of computing services, that is servers, storage, databases, networking, software and analytics, over the Internet on a pay as you go basis, instead of owning and running physical hardware.
   - The five essential characteristics defined by NIST are on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Service models:

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What is provided | Virtual machines, storage, network, that is raw infrastructure | A ready runtime platform with OS, middleware, database and development tools | Complete ready to use application software |
   | The user manages | OS, middleware, runtime, applications and data | Applications and data only | Nothing, only the data and the settings |
   | The provider manages | Hardware, virtualisation, network, storage | Everything below the application | Absolutely everything |
   | Control and flexibility | Highest | Medium | Lowest |
   | Target user | System administrator, network engineer | Application developer | End user |
   | Examples | AWS EC2, Google Compute Engine, Microsoft Azure VM, DigitalOcean droplets | Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service, Red Hat OpenShift | Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom |
   | Analogy, using a car | Renting a car and driving it yourself | Hiring a car with a driver | Taking a taxi ride |

   - Deployment models, for completeness: public cloud, private cloud, hybrid cloud and community cloud.
3. **What is SaaS and multi-tenant architecture? How are they related? What are the advantages and disadvantages of multi-tenancy? For a multi-vendor e-commerce application, you can choose a database architecture where you can put all the vendors in a single database or each vendor in a separate database. Which architecture will you follow and why?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 328 (ET: BIBM)]*


   Answer:

   SaaS:
   - Software as a Service is a cloud model in which a complete application is hosted by the provider and delivered to customers over the Internet, normally by subscription. The customer installs nothing and manages nothing but its own data and settings. Examples: Gmail, Salesforce, Office 365 and Zoom.

   Multi-tenant architecture:
   - A single running instance of the application, and usually a single shared database, serves many customers, called tenants. Each tenant's data is logically isolated so that no tenant can see another's, even though the underlying resources are shared.
   - The opposite is single tenancy, where each customer gets its own separate instance and database.

   How they are related:
   - Multi-tenancy is the architecture that makes SaaS economically possible. Running one shared instance for ten thousand customers costs a fraction of running ten thousand separate instances, and it is that economy that allows SaaS to be sold at a low monthly price. In practice almost every large SaaS product is multi-tenant.

   Advantages of multi-tenancy:
   - Much lower cost per customer, since hardware, licences and operational effort are shared.
   - One codebase and one deployment, so an update or a security patch reaches every customer at once.
   - Higher resource utilisation, because tenants peak at different times.
   - Easier onboarding: a new customer is a new row of configuration, not a new server.
   - Central monitoring, backup and scaling for the whole population.

   Disadvantages of multi-tenancy:
   - Noisy neighbour effect: one heavy tenant can degrade performance for everybody.
   - Security risk is concentrated: a single flaw in the tenant isolation logic can expose every customer's data.
   - Limited customisation, since the schema and the code must serve all tenants.
   - A single bug or a bad deployment brings down all tenants together.
   - Compliance difficulty: a customer that must keep its data in a separate jurisdiction or under separate encryption keys is hard to accommodate.
   - Complex development: every query must filter by tenant, and a single missing filter is a serious data leak.

   Which database architecture for a multi-vendor e-commerce application:
   - I would choose a single shared database with a `vendor_id` column on every table, that is the shared schema multi-tenant model, for the general vendor population.

   Reasons:
   - Cost and scalability: an e-commerce platform may have thousands of small vendors. Thousands of separate databases would mean thousands of connection pools, backups and migration jobs, which is operationally unmanageable and expensive.
   - Cross-vendor features are natural: product search across all vendors, a shared cart containing items from several vendors, platform wide analytics and recommendation all require querying across vendors, which is trivial in one database and painful across many.
   - Schema changes are applied once, not thousands of times, so releases are fast and consistent.
   - Onboarding a new vendor is instant, which matters for a marketplace.
   - Better hardware utilisation, since most vendors are small and idle most of the time.

   How the risks are controlled:
   - Every table carries `vendor_id`, every query filters on it, and this is enforced in a single data access layer rather than left to individual developers.
   - Row level security in the database gives a second line of defence independent of application code.
   - Partitioning or sharding by `vendor_id` keeps large tables manageable.
   - A hybrid approach is the practical answer for the largest vendors: a very large vendor with special compliance or performance requirements is moved to its own database or its own shard, while the long tail of small vendors stays in the shared one. This is what real marketplaces do.
4. **6.11 A startup company wants to launch a new web application. They do not want to manage any underlying hardware, operating systems, or even the runtime environment; they only want to focus on writing and deploying their code. Based on your understanding of Cloud Service Models, which model (IaaS, PaaS, or SaaS) is most appropriate for them? Provide two real-world examples of platforms that provide this specific type of service.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer: PaaS, Platform as a Service, is the appropriate model.

   Reason:
   - The requirement is explicitly to avoid managing hardware, operating systems and the runtime environment, and to focus only on writing and deploying code. That is the exact definition of PaaS: the provider manages everything up to and including the runtime, and the customer manages only the application and its data.
   - IaaS is rejected because the customer would still have to install, patch and secure the operating system and the runtime.
   - SaaS is rejected because it delivers a finished application, not a place to run one's own code.

   Two real-world examples:
   - Heroku
   - Google App Engine
   - Equally acceptable: AWS Elastic Beanstalk, Microsoft Azure App Service, Red Hat OpenShift.

   Additional benefits for a startup:
   - Automatic scaling as traffic grows, built in deployment and rollback, managed database add-ons, and no need to employ a system administrator, so a very small team can run a production service.
5. **Describe SaaS, IaaS and PaaS.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*


   Answer: These are the three service models of cloud computing, distinguished by how much the provider manages and how much is left to the customer.

   SaaS, Software as a Service:
   - A complete, ready to use application delivered over the Internet, normally by subscription. The customer manages nothing except its own data and settings; there is no installation, no patching and no server to maintain.
   - Examples: Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom.

   PaaS, Platform as a Service:
   - A ready runtime platform including the operating system, web server, database and development tools, on which the customer deploys its own application code. The provider manages everything below the application.
   - Examples: Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service.

   IaaS, Infrastructure as a Service:
   - Raw virtualised infrastructure, that is virtual machines, storage and networking, rented on demand. The customer installs and manages the operating system, the middleware and the applications, and so keeps the greatest control.
   - Examples: AWS EC2, Google Compute Engine, Azure Virtual Machines, DigitalOcean.

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What is provided | Virtual machines, storage, network, that is raw infrastructure | A ready runtime platform with OS, middleware, database and development tools | Complete ready to use application software |
   | The user manages | OS, middleware, runtime, applications and data | Applications and data only | Nothing, only the data and the settings |
   | The provider manages | Hardware, virtualisation, network, storage | Everything below the application | Absolutely everything |
   | Control and flexibility | Highest | Medium | Lowest |
   | Target user | System administrator, network engineer | Application developer | End user |
   | Examples | AWS EC2, Google Compute Engine, Microsoft Azure VM, DigitalOcean droplets | Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service, Red Hat OpenShift | Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom |
   | Analogy, using a car | Renting a car and driving it yourself | Hiring a car with a driver | Taking a taxi ride |
6. **Explain IaaS, PaaS, and SaaS with respect to cloud computing.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*


   Answer: IaaS, PaaS and SaaS are the three service models of cloud computing, and they differ in where the boundary of responsibility falls between the provider and the customer.

   IaaS, Infrastructure as a Service:
   - The provider supplies virtualised hardware: compute, storage and network. The customer chooses and installs the operating system and everything above it.
   - It gives the greatest control and flexibility, and is used when an organisation wants to move its existing servers to the cloud without changing how they are built.
   - Examples: AWS EC2, Azure Virtual Machines, Google Compute Engine.

   PaaS, Platform as a Service:
   - The provider supplies the whole runtime stack: operating system, web server, runtime, database and development tools. The customer supplies only the application code and its data.
   - It removes all infrastructure work from the developer, and adds automatic scaling and deployment pipelines, but gives less control over the environment.
   - Examples: Heroku, Google App Engine, AWS Elastic Beanstalk.

   SaaS, Software as a Service:
   - The provider supplies a complete finished application over the Internet. The customer simply uses it and manages nothing but its own data and configuration.
   - It is the easiest to adopt and the least flexible, and it is normally multi-tenant, one shared instance serving many customers.
   - Examples: Gmail, Office 365, Salesforce.

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What is provided | Virtual machines, storage, network, that is raw infrastructure | A ready runtime platform with OS, middleware, database and development tools | Complete ready to use application software |
   | The user manages | OS, middleware, runtime, applications and data | Applications and data only | Nothing, only the data and the settings |
   | The provider manages | Hardware, virtualisation, network, storage | Everything below the application | Absolutely everything |
   | Control and flexibility | Highest | Medium | Lowest |
   | Target user | System administrator, network engineer | Application developer | End user |
   | Examples | AWS EC2, Google Compute Engine, Microsoft Azure VM, DigitalOcean droplets | Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service, Red Hat OpenShift | Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom |
   | Analogy, using a car | Renting a car and driving it yourself | Hiring a car with a driver | Taking a taxi ride |
7. **What do you mean by multi-tenancy in the cloud? Why is it beneficial for cloud service providers?** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 749 (ET: N/A)]*


   Answer:

   Multi-tenancy in the cloud:
   - Multi-tenancy means that a single instance of an application, or a single set of physical resources, serves many separate customers, called tenants, at the same time. Each tenant's data and configuration are logically isolated so that no tenant can see or affect another's, even though the underlying software and hardware are shared.
   - It exists at several levels: shared hardware with separate VMs, shared application with separate databases, and a fully shared application and database with a tenant identifier on every record.
   - The opposite is single tenancy, where each customer receives its own dedicated instance.

   Why it is beneficial for cloud service providers:
   - Economy of scale: one deployment serves thousands of customers, so hardware, licences, power and operational staff are shared and the cost per customer falls dramatically. This is what allows a service to be sold for a few dollars a month.
   - High resource utilisation: tenants peak at different times and most are idle most of the time, so pooled resources are used far more efficiently than dedicated ones.
   - Single codebase and single deployment: a feature or a security patch is written once and reaches every customer immediately, instead of being rolled out to thousands of separate installations.
   - Fast onboarding: adding a customer is a configuration change, not a server build, so the business can grow without a proportional increase in operations work.
   - Central monitoring, backup, scaling and support, which reduces operational complexity enormously.
   - Easier capacity planning, because aggregate demand across many tenants is far smoother and more predictable than any individual tenant's demand.
   - Higher margins, since the marginal cost of one more customer is very small.

   - The corresponding obligations on the provider are strong tenant isolation, protection against the noisy neighbour effect through quotas and throttling, and clear data segregation guarantees in the service level agreement.
8. **(ক) Cloud Computing এর সার্ভিসগুলো লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*


   Answer: Cloud Computing-er tinti prodhan service model:

   - SaaS, Software as a Service: sompurno toiri software Internet-er madhome byabohar kora jay. Byabaharkari kichu install ba maintain kore na, shudhu nijer data ar setting-i dekhe. Udahoron: Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom.
   - PaaS, Platform as a Service: operating system, runtime, database ar development tool shoho ekti toiri platform deoa hoy, jekhane developer shudhu nijer code deploy kore. Udahoron: Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service.
   - IaaS, Infrastructure as a Service: virtual machine, storage ar network — mane kancha infrastructure vara deoa hoy. Grahok nije OS theke shuru kore shob kichu boshay ar niyontron kore. Udahoron: AWS EC2, Google Compute Engine, Azure VM, DigitalOcean.

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What is provided | Virtual machines, storage, network, that is raw infrastructure | A ready runtime platform with OS, middleware, database and development tools | Complete ready to use application software |
   | The user manages | OS, middleware, runtime, applications and data | Applications and data only | Nothing, only the data and the settings |
   | The provider manages | Hardware, virtualisation, network, storage | Everything below the application | Absolutely everything |
   | Control and flexibility | Highest | Medium | Lowest |
   | Target user | System administrator, network engineer | Application developer | End user |
   | Examples | AWS EC2, Google Compute Engine, Microsoft Azure VM, DigitalOcean droplets | Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service, Red Hat OpenShift | Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom |
   | Analogy, using a car | Renting a car and driving it yourself | Hiring a car with a driver | Taking a taxi ride |

   Onnanno service jegulo ekhon alada bhabe bola hoy:
   - FaaS ba Function as a Service, jake Serverless-o bola hoy — shudhu ekti function likhe deoa hoy, server-er kotha bhabte-i hoy na. Udahoron: AWS Lambda.
   - DaaS, Database ba Desktop as a Service; STaaS, Storage as a Service; ar NaaS, Network as a Service.

   Deployment model:
   - Public cloud, Private cloud, Hybrid cloud ar Community cloud.
9. **Software as a Service is SaaS, Platform as a Service is PaaS and Infrastructure as a Service is IaaS. Those are three types of Cloud services. In the following table, there are some Cloud services. Write the category of those:** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819-820 (ET: BUET)]*
   Search engine for a web server
   Google Docs
   Microsoft Azure
   Drop box
   Amazon Web Services (AWS)


   Answer:

   | Cloud service | Category | Reason |
   |---|---|---|
   | Search engine for a web server | SaaS | The user simply uses a finished search application over the Internet and manages nothing beneath it |
   | Google Docs | SaaS | A complete ready to use application accessed through the browser |
   | Microsoft Azure | IaaS, and also PaaS | Azure Virtual Machines provide raw infrastructure, which is IaaS; Azure App Service provides a managed runtime, which is PaaS |
   | Dropbox | SaaS | A finished file storage and sharing application; the user manages only the files |
   | Amazon Web Services (AWS) | IaaS, and also PaaS | EC2, S3 and VPC are IaaS; Elastic Beanstalk and Lambda are PaaS |

   - Rule for deciding: if the customer only uses a finished application, it is SaaS. If the customer deploys its own code onto a managed runtime, it is PaaS. If the customer manages the operating system itself, it is IaaS.
   - Azure and AWS are whole platforms offering services in all three categories, so the honest answer names IaaS as the primary category while noting that they also provide PaaS and SaaS offerings.
10. **(c) What are the three types of services provided by the cloud?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888 (ET: N/A)]*


   Answer: The three types of services provided by the cloud are IaaS, PaaS and SaaS.

   - IaaS, Infrastructure as a Service: virtual machines, storage and networking rented on demand; the customer manages the operating system and everything above it. Examples: AWS EC2, Azure VM, Google Compute Engine.
   - PaaS, Platform as a Service: a ready runtime with operating system, middleware, database and development tools; the customer deploys only its own code. Examples: Heroku, Google App Engine, AWS Elastic Beanstalk.
   - SaaS, Software as a Service: a complete finished application delivered over the Internet; the customer manages nothing but its own data. Examples: Gmail, Office 365, Salesforce, Dropbox.

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What is provided | Virtual machines, storage, network, that is raw infrastructure | A ready runtime platform with OS, middleware, database and development tools | Complete ready to use application software |
   | The user manages | OS, middleware, runtime, applications and data | Applications and data only | Nothing, only the data and the settings |
   | The provider manages | Hardware, virtualisation, network, storage | Everything below the application | Absolutely everything |
   | Control and flexibility | Highest | Medium | Lowest |
   | Target user | System administrator, network engineer | Application developer | End user |
   | Examples | AWS EC2, Google Compute Engine, Microsoft Azure VM, DigitalOcean droplets | Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service, Red Hat OpenShift | Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom |
   | Analogy, using a car | Renting a car and driving it yourself | Hiring a car with a driver | Taking a taxi ride |
11. **Write the three basic function of cloud services?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*


   Answer: The three basic functions, that is the three service categories, of cloud services are:

   - Infrastructure as a Service, IaaS: providing computing infrastructure, that is virtual servers, storage and networking, on demand. The customer manages the operating system and the applications. Examples: AWS EC2, Azure Virtual Machines.
   - Platform as a Service, PaaS: providing a complete development and deployment platform, with the operating system, runtime, database and tools already in place, so the customer supplies only application code. Examples: Heroku, Google App Engine.
   - Software as a Service, SaaS: providing a finished application over the Internet, ready to use, with nothing to install or maintain. Examples: Gmail, Office 365, Salesforce.

   - In terms of underlying functions rather than models, the three things every cloud service delivers are computing power, storage, and networking, all pooled, virtualised and metered.
12. **ক্লাউড কম্পিউটিং এর সুবিধা ও অসুবিধা লিখুন।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*


   Answer:

   Cloud computing-er shubidha:
   - Prathomik khoroch khub kom: nijer server, data centre, cooling ba power-e boro binoyog lage na; khoroch masik operating expense hoye jay.
   - Scalability ar elasticity: chahida onujayi kichukhon-er modhye resource barano ba komano jay, tai hothat traffic barleo site chalu thake ar chahida kome gele baroti taka dite hoy na.
   - Je kono jaiga theke access: Internet thakle je kono device theke kaj kora jay, tai remote kaj sohoj hoy.
   - Nirbhorjogyota ar disaster recovery: provider ekadhik availability zone ar region-e data replicate kore rakhe ebong 99.9 percent porjonto SLA dey.
   - Automatic update ar maintenance: patch, hardware bodol ar upgrade — shob provider-er dayitto.
   - Druto deployment: je server age kinte koyek soptaho lagto, ekhon koyek minute-e chalu hoy.
   - Sohojogita: onek byabaharkari ekoi document ba dataset-e ekshathe kaj korte pare.
   - Machine learning, big data analytics ar CDN-er moto unnoto seba pawa jay, ja choto protishthan nije kokhono banate parto na.

   Cloud computing-er oshubidha:
   - Internet-er upor sompurno nirbhorota: connection gele kono kaj hoy na. Jekhane bandwidth dami ba oniyomito, sekhane eta boro somossa.
   - Nirapotta ar gopaniyota: data onner hardware-e thake, tai gopaniyota provider-er niyontron ar grahok-er thik configuration-er upor nirbhor kore.
   - Data sovereignty ar ain: onek desh, jemon Bangladesh-e banking data, nirdisto data desher bhitore rakhte bare.
   - Sīmito niyontron ar customization, bishesh kore SaaS-e, jekhane software-er achoron bodlano jay na.
   - Vendor lock-in: proprietary service ar data transfer charge-er karone pore onno provider-e jaoa kothin ar bhoyongkor dami.
   - Dirghomeyade khoroch: sthir ar oporiborton-shil workload-er jonno koyek bochor por nijer hardware-i shosta hote pare.
   - Downtime-er jhuki: provider-er ekti outage ekshathe shob grahok-ke prabhabito kore, ar grahok-er kichu-i korar thake na.
   - Lukono charge, bishesh kore outbound data transfer-e, ar notun dokkhota-sompanno lok-er proyojon.

## Cloud Storage & Fundamentals (6)

1. What is cloud computing? Why is it used? State the difference between cloud storage and traditional storage. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **What is Cloud Computing? What are its characteristics? Briefly describe the types of cloud computing.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

3. **Explain cloud computing and evaluate its advantages and disadvantages.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

4. **(খ) Cloud computing কী? উহার বৈশিষ্ট্য ও সুবিধা বর্ণনা করুন ।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 616 (ET: N/A)]*

5. **What is Cloud Computing? Write its adventages and Disadventages?** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*

6. **Describe the cloud base database briefly.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

## Virtualization & Containers (VM vs Container) (6)

1. VM vs Container in Submarine Cable Network: [BSCCPL AME 21-08-2026 (BUET)] A national submarine cable landing station provides international connectivity to several organizations. The organization wants to deploy DNS, Web, Database, Monitoring, and Network Management services on a shared physical server. The network administrator is considering two approaches:
Approach A: Deploy each service in a separate Virtual Machine.
Approach B: Deploy each service in a separate Container.
A submarine cable connects Bangladesh to an international data center. At the cable landing station, a server hosts 4 VMs, while another server runs 4 containers. Which one and why? [BSCCPL AME 21-08-2026 (BUET)]

2. **What is Virtualization? Write down the benefits of Virtualization. Write down the top 5 virtual platform software.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 529 (ET: MIST)]*

3. **What is Server Virtualization? Explain with example of its.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 551 (ET: BIBM)]*

4. **How virtualization help physical server.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 566 (ET: N/A)]*

5. **Define a virtual machine with a neat diagram, explain the working of VM. What are the benefits of a VM?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 442 (ET: BIBM)]*

6. **What is docker? An application running on windows server shifted in linux server. What problem will occur? Can Docker solve it?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

## Cluster, Grid & Distributed Computing (3)

1. **(ক) উদাহরণসহ distributed এবং centralized computing -এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

2. **Difference between cluster computing and grid computing.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 750 (ET: N/A)]*

3. **Imagine data in a system is green, red, yellow and blue in the system using distributed server in parallel. Design the system using reduce map.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*

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
