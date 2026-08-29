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


   Answer:

   What cloud computing is:

   - Cloud computing is the delivery of computing services — servers, storage, databases, networking, software and analytics — over the Internet on a pay as you go basis, instead of buying and running physical hardware.
   - The five essential characteristics defined by NIST are on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Why it is used:
   - To avoid the large capital cost and the long lead time of buying and installing physical servers.
   - To scale capacity up and down quickly with demand, paying only for what is used.
   - To reach data and applications from anywhere, on any device.
   - To obtain reliability, backup and disaster recovery that a single organisation could not afford to build.
   - To hand over patching, hardware maintenance and upgrades to the provider, so the internal team can work on the business instead.
   - To use advanced services such as analytics and machine learning without building the infrastructure for them.

   Cloud storage vs traditional storage:

   | Point | Cloud storage | Traditional, that is local or on-premises storage |
   |---|---|---|
   | Location | On the provider's servers, reached over the Internet | On the organisation's own disks, servers, NAS or SAN |
   | Cost model | Operating expense, pay per GB per month | Capital expense, paid up front for the hardware |
   | Capacity | Practically unlimited, expanded instantly | Fixed by the hardware bought; expansion needs procurement |
   | Access | From anywhere with an Internet connection | Normally only from within the local network |
   | Maintenance | Handled entirely by the provider | The organisation's own responsibility |
   | Backup and redundancy | Built in, replicated across zones and regions | Must be designed, bought and operated separately |
   | Speed | Limited by the Internet link | Very fast, limited only by the local bus or LAN |
   | Availability without network | None | Full |
   | Security and control | Shared responsibility; data is on someone else's hardware | Complete physical and logical control |
   | Examples | Amazon S3, Google Drive, Dropbox, Azure Blob Storage | Internal hard disk, USB drive, NAS, SAN, tape library |
2. **What is Cloud Computing? What are its characteristics? Briefly describe the types of cloud computing.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer:

   What cloud computing is:

   - Cloud computing is the delivery of computing services — servers, storage, databases, networking, software and analytics — over the Internet on a pay as you go basis, instead of buying and running physical hardware.
   - The five essential characteristics defined by NIST are on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Essential characteristics, as defined by NIST:
   - On demand self service: the user provisions computing resources automatically through a portal or an API, without any human interaction with the provider.
   - Broad network access: the service is available over the network and reachable from any standard client, whether a phone, a tablet or a workstation.
   - Resource pooling: the provider's resources are pooled to serve many customers using a multi-tenant model, with resources assigned and reassigned dynamically according to demand.
   - Rapid elasticity: capacity can be scaled out and in quickly, and to the customer the available resources appear unlimited.
   - Measured service: usage is metered and billed, so the customer pays only for what is consumed, which also gives transparency to both sides.

   Additional practical characteristics: virtualisation, high availability, automation, self healing and geographic distribution.

   Deployment types:
   - Public cloud: infrastructure owned by a provider and shared by many customers over the Internet. Cheapest, most scalable, least control. Examples: AWS, Azure, Google Cloud.
   - Private cloud: infrastructure dedicated to one organisation, either on its own premises or hosted. Highest control, security and compliance, but highest cost.
   - Hybrid cloud: a combination of public and private, with data and applications moving between them. Sensitive data is kept private while variable workloads burst into the public cloud. This is what most banks use.
   - Community cloud: shared by several organisations with a common concern, such as a group of government agencies or hospitals, sharing the cost and the compliance framework.

   Service types: IaaS, PaaS and SaaS, and now also FaaS or serverless.
3. **Explain cloud computing and evaluate its advantages and disadvantages.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer:

   - Cloud computing is the delivery of computing services — servers, storage, databases, networking, software and analytics — over the Internet on a pay as you go basis, instead of buying and running physical hardware.
   - The five essential characteristics defined by NIST are on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Advantages:
   - Low initial cost: no capital expenditure on servers, data centre space, cooling or power; the cost becomes a monthly operating expense.
   - Scalability and elasticity: resources can be added or removed within minutes to match demand, so a sudden peak is survivable and quiet periods cost nothing extra.
   - Accessibility: reachable from anywhere with an Internet connection and from any device, which supports remote and distributed work.
   - Reliability and disaster recovery: providers replicate data across availability zones and regions and offer service level agreements of 99.9 percent or better.
   - Automatic updates and maintenance: patching, hardware replacement and upgrades are the provider's responsibility.
   - Speed of deployment: a server that once took weeks to procure is running in minutes.
   - Collaboration: many users can work on the same document or dataset at the same time.
   - Access to advanced services such as machine learning, big data analytics and content delivery networks that a small organisation could never build itself.

   Disadvantages:
   - Dependence on the Internet: if the connection fails, nothing works, which is a real constraint where bandwidth is expensive or unreliable.
   - Security and privacy concerns: the data resides on someone else's hardware, so confidentiality depends on the provider's controls and on correct configuration by the customer.
   - Data sovereignty and legal compliance: many countries, including Bangladesh for banking data, require certain data to remain within the national boundary.
   - Limited control and customisation, particularly in SaaS, where the customer cannot change how the software behaves.
   - Vendor lock-in: proprietary services and data transfer charges make later migration costly and difficult.
   - Long term cost: for a steady workload running continuously, owning the hardware can be cheaper over several years.
   - Downtime risk: an outage at the provider affects every customer at once and the customer can only wait.
   - Hidden charges, especially for outbound data transfer, and the need for staff with new skills.

   - Evaluation: for a startup or for any workload with variable demand, the advantages are decisive, because the cost and the delay of owning hardware would be prohibitive. For a large organisation with a steady workload and strict data residency rules, such as a central bank, a private or hybrid cloud is the more sensible choice, keeping regulated data in-house while using the public cloud for elastic and non-sensitive work.
4. **(খ) Cloud computing কী? উহার বৈশিষ্ট্য ও সুবিধা বর্ণনা করুন ।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 616 (ET: N/A)]*


   Answer:

   Cloud computing ki:
   - Cloud computing holo Internet-er madhome computing seba — server, storage, database, networking, software ar analytics — chahida onujayi bhara neoa, nijer physical hardware kene chalanor poribote.
   - Jotota byabohar kora hoy totota-i taka deoa hoy, tai eta pay as you go model.

   Boishishtho (characteristics):
   - On demand self service: byabaharkari nijei portal ba API diye resource nite pare, provider-er kono lok-er dorkar hoy na.
   - Broad network access: je kono standard device theke network-er madhome pawa jay.
   - Resource pooling: provider-er resource multi-tenant model-e onek grahok-er modhye bhag kore deoa hoy ebong chahida onujayi punorbonton hoy.
   - Rapid elasticity: kichukhon-er modhye khomota barano ba komano jay, ar grahok-er kache resource oshim mone hoy.
   - Measured service: byabohar mapa hoy ar sei onujayi bill hoy, tai duipokkher jonoi ta sposhto.
   - Ei sathe virtualization, uchcho nirbhorjogyota, automation ar bhougolik bistar.

   Shubidha:
   - Prathomik binoyog prayo lage na; khoroch masik operating expense hoye jay.
   - Chahida onujayi kichukhon-er modhye resource barano-komano jay.
   - Je kono jaiga theke, je kono device theke access kora jay.
   - Provider ekadhik region-e data replicate kore, tai backup ar disaster recovery built-in.
   - Patch, upgrade ar hardware maintenance provider-er dayitto.
   - Druto deployment — koyek minute-e server chalu.
   - Onek byabaharkari ekoi file-e ekshathe kaj korte pare.
   - Machine learning ar big data analytics-er moto unnoto seba sohoje pawa jay.

   Oshubidha, jeta uttor-e ullekh korle bhalo:
   - Internet-er upor sompurno nirbhorota, nirapotta ar data sovereignty niye udbeg, sīmito niyontron, vendor lock-in, ar dirghomeyade khoroch beshi hote para.
5. **What is Cloud Computing? Write its adventages and Disadventages?** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*


   Answer:

   - Cloud computing is the delivery of computing services — servers, storage, databases, networking, software and analytics — over the Internet on a pay as you go basis, instead of buying and running physical hardware.
   - The five essential characteristics defined by NIST are on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Advantages:
   - Low initial cost: no capital expenditure on servers, data centre space, cooling or power; the cost becomes a monthly operating expense.
   - Scalability and elasticity: resources can be added or removed within minutes to match demand, so a sudden peak is survivable and quiet periods cost nothing extra.
   - Accessibility: reachable from anywhere with an Internet connection and from any device, which supports remote and distributed work.
   - Reliability and disaster recovery: providers replicate data across availability zones and regions and offer service level agreements of 99.9 percent or better.
   - Automatic updates and maintenance: patching, hardware replacement and upgrades are the provider's responsibility.
   - Speed of deployment: a server that once took weeks to procure is running in minutes.
   - Collaboration: many users can work on the same document or dataset at the same time.
   - Access to advanced services such as machine learning, big data analytics and content delivery networks that a small organisation could never build itself.

   Disadvantages:
   - Dependence on the Internet: if the connection fails, nothing works, which is a real constraint where bandwidth is expensive or unreliable.
   - Security and privacy concerns: the data resides on someone else's hardware, so confidentiality depends on the provider's controls and on correct configuration by the customer.
   - Data sovereignty and legal compliance: many countries, including Bangladesh for banking data, require certain data to remain within the national boundary.
   - Limited control and customisation, particularly in SaaS, where the customer cannot change how the software behaves.
   - Vendor lock-in: proprietary services and data transfer charges make later migration costly and difficult.
   - Long term cost: for a steady workload running continuously, owning the hardware can be cheaper over several years.
   - Downtime risk: an outage at the provider affects every customer at once and the customer can only wait.
   - Hidden charges, especially for outbound data transfer, and the need for staff with new skills.
6. **Describe the cloud base database briefly.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*


   Answer: A cloud based database is a database that runs on cloud infrastructure and is accessed over the Internet, with the provider taking responsibility for the underlying servers, storage and, in the managed form, for the database software itself.

   Two forms:
   - Self managed on IaaS: the customer installs MySQL, PostgreSQL or Oracle on a cloud virtual machine and administers it. Full control, but patching, backup and scaling remain the customer's work.
   - Managed database as a service, DBaaS: the provider runs the engine as well, and handles provisioning, patching, backup, replication, failover and scaling. Examples: Amazon RDS and Aurora, Azure SQL Database, Google Cloud SQL, MongoDB Atlas, Amazon DynamoDB and Firebase.

   Characteristics:
   - Elastic scaling: storage and compute can be increased with a setting change, and read replicas can be added to spread the query load.
   - High availability: automatic replication to a standby in another availability zone, with automatic failover in seconds.
   - Automated backup and point in time recovery, typically to any second within a retention window of days or weeks.
   - Pay per use billing, based on instance size, storage and I/O.
   - Security: encryption at rest and in transit, IAM based access control, VPC isolation and audit logging.
   - Both relational and NoSQL engines are offered, as well as data warehouse services such as Amazon Redshift, Google BigQuery and Snowflake.

   Advantages:
   - No hardware to buy or maintain, and no database administrator needed for routine work.
   - Fast provisioning, in minutes rather than weeks.
   - Built in redundancy and disaster recovery across regions.
   - Global reach, with replicas placed near the users.
   - Cost matches usage, so a small application pays very little.

   Disadvantages:
   - Latency depends on the network link, so a chatty application far from the region suffers.
   - Less control: superuser access, custom extensions and OS level tuning may not be permitted.
   - Vendor lock-in, particularly with proprietary engines such as Aurora or DynamoDB, and outbound data transfer charges make migration expensive.
   - Compliance and data residency limits, which matter for banking and government data in Bangladesh.
   - Cost can rise sharply and unpredictably at large scale.

## Virtualization & Containers (VM vs Container) (6)

1. VM vs Container in Submarine Cable Network: [BSCCPL AME 21-08-2026 (BUET)] A national submarine cable landing station provides international connectivity to several organizations. The organization wants to deploy DNS, Web, Database, Monitoring, and Network Management services on a shared physical server. The network administrator is considering two approaches:
Approach A: Deploy each service in a separate Virtual Machine.
Approach B: Deploy each service in a separate Container.
A submarine cable connects Bangladesh to an international data center. At the cable landing station, a server hosts 4 VMs, while another server runs 4 containers. Which one and why? [BSCCPL AME 21-08-2026 (BUET)]


   Answer:

   The two approaches compared:

   | Point | Approach A, Virtual Machines | Approach B, Containers |
   |---|---|---|
   | What is virtualised | The whole hardware, so each VM runs a complete guest OS | The operating system, so all containers share the host kernel |
   | Size | Gigabytes per VM | Megabytes per container |
   | Boot time | Minutes | Seconds or less |
   | Overhead | High: each VM needs its own OS, kernel and memory | Very low: only the application and its libraries |
   | Density on one server | Few, perhaps 4 to 10 | Many, dozens to hundreds |
   | Isolation | Strong, hardware level, enforced by the hypervisor | Weaker, process level, shared kernel |
   | Security blast radius | A kernel compromise affects only that VM | A host kernel exploit can affect every container |
   | Different operating systems | Yes, Windows and Linux can run side by side | No, all containers share the host kernel |
   | Portability | Heavy image, but fully self contained | Very light and portable, runs identically anywhere |
   | Typical management | VMware vSphere, KVM, Hyper-V | Docker, Kubernetes, Podman |

   Which one and why, for a submarine cable landing station:
   - The recommendation is a hybrid, and if a single choice is demanded it is Virtual Machines for this specific environment.
   - Reason 1, criticality and isolation: a cable landing station carries the international connectivity of a whole country. DNS and network management are the most security sensitive services on the site. Hardware level isolation by a hypervisor is far stronger than shared kernel isolation, so a compromise of the web service cannot reach the DNS or the network management system.
   - Reason 2, regulatory and audit requirements: national critical infrastructure is normally required to demonstrate strong workload separation, and VMs satisfy an auditor more readily than containers on a shared kernel.
   - Reason 3, mixed operating systems: network management and monitoring products in this sector are often supplied as appliances or as Windows software, which containers on a Linux host cannot run.
   - Reason 4, stability over density: only five services are involved, so the density advantage of containers is not needed, and the resource overhead of five VMs on one server is entirely affordable.
   - Where containers are the better answer: for the monitoring and web services, which change often and must be redeployed frequently, containers give much faster deployment, easy rollback and consistent environments.
   - Practical design actually used in industry: run VMs as the base isolation layer, one VM per security zone, and run containers inside those VMs for the stateless services. This gives the strong isolation of virtualisation and the agility of containers at the same time.
2. **What is Virtualization? Write down the benefits of Virtualization. Write down the top 5 virtual platform software.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 529 (ET: MIST)]*


   Answer:

   What virtualisation is:
   - Virtualisation is the creation of a software based, that is virtual, version of a physical resource such as a server, storage device, network or operating system, so that one physical resource can be presented as several independent logical ones.
   - A hypervisor sits between the hardware and the virtual machines and allocates CPU, memory, storage and network to each. Type 1 or bare metal hypervisors run directly on the hardware, and Type 2 hypervisors run on top of a host operating system.
   - Types: server virtualisation, storage virtualisation, network virtualisation including SDN and NFV, desktop virtualisation and application virtualisation.

   Benefits of virtualisation:

   - Server consolidation: many virtual machines run on one physical server, so utilisation rises from a typical 10 to 15 percent to 70 or 80 percent and far fewer machines are needed.
   - Cost saving: less hardware means less capital expenditure, less rack space, less power and less cooling.
   - Isolation: each VM is separated from the others, so a crash or a compromise in one does not affect the rest.
   - Rapid provisioning: a new server is created from a template in minutes rather than weeks.
   - Snapshots and rollback: the entire state of a machine can be saved before a risky change and restored instantly if it fails.
   - Live migration: a running VM can be moved to another host with no downtime, allowing hardware maintenance during working hours.
   - High availability and disaster recovery: VMs restart automatically on another host if one fails, and replication to a second site is straightforward.
   - Hardware independence: a VM is just a set of files, so it runs on any host with the same hypervisor.
   - Legacy support: an old operating system that no longer runs on modern hardware can continue inside a VM.
   - Excellent for testing and development, since several operating systems can be tried on one machine and reset at will.

   Top five virtual platform software:
   - VMware vSphere with ESXi, the enterprise market leader, a Type 1 hypervisor.
   - Microsoft Hyper-V, built into Windows Server, a Type 1 hypervisor.
   - KVM, Kernel-based Virtual Machine, the open source hypervisor built into the Linux kernel and the basis of most public clouds and of Red Hat and Proxmox.
   - Citrix Hypervisor, formerly XenServer, based on Xen and widely used for virtual desktop infrastructure.
   - Oracle VirtualBox, a free Type 2 hypervisor, used mainly for development and testing; VMware Workstation is its commercial equivalent.
3. **What is Server Virtualization? Explain with example of its.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 551 (ET: BIBM)]*


   Answer:

   Server virtualisation:
   - Server virtualisation is the technique of dividing one physical server into several isolated virtual servers, each running its own operating system and applications as if it were a separate machine.
   - A hypervisor sits between the hardware and the virtual machines, allocating CPU cores, memory, disk and network to each and keeping them isolated from one another.
   - Type 1, bare metal, hypervisors such as VMware ESXi, Microsoft Hyper-V and KVM run directly on the hardware and are used in production. Type 2 hypervisors such as VirtualBox and VMware Workstation run on top of a host operating system and are used for development.

   Example:
   - An office has one physical server with 32 CPU cores, 128 GB of RAM and 8 TB of storage, which as a single machine would run at perhaps 10 percent utilisation.
   - VMware ESXi is installed on it, and four virtual machines are created: a Windows Server domain controller with 4 cores and 16 GB, a Linux web server with 8 cores and 32 GB, a database server with 12 cores and 48 GB, and a test server with 4 cores and 16 GB.
   - Each behaves as an independent server with its own IP address and its own administrator, users cannot tell the difference, and yet only one physical box, one rack unit and one power feed are used instead of four.
   - If the database server needs more memory, it is given more with a configuration change rather than a hardware purchase. If the physical host must be serviced, the running VMs are migrated live to another host with no downtime.

   Why it matters:
   - Utilisation rises from about 10 percent to 70 or 80 percent, hardware, power, cooling and rack space costs fall sharply, provisioning takes minutes instead of weeks, and snapshots make risky changes safely reversible.
   - It is also the foundation of cloud computing: every IaaS offering is server virtualisation sold by the hour.
4. **How virtualization help physical server.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 566 (ET: N/A)]*


   Answer: Virtualisation helps a physical server in the following ways.

   - It raises utilisation dramatically. A dedicated physical server typically runs at only 10 to 15 percent of its capacity, because it is sized for peak load and runs one application. Virtualisation lets several workloads share it, taking utilisation to 70 or 80 percent, so the hardware already bought does far more work.
   - It consolidates many servers into one. Ten lightly loaded physical machines become ten virtual machines on one host, which cuts hardware, rack space, power, cooling and maintenance cost by roughly an order of magnitude.
   - It allows dynamic resource allocation. CPU, memory and disk can be added to or taken from a workload with a configuration change, without opening the case or buying anything.
   - It provides isolation. Each VM has its own operating system, so one application crashing or being compromised does not affect the others sharing the same physical server, which was the whole reason for having one server per application in the first place.
   - It makes provisioning instant. A new server is cloned from a template in minutes rather than procured over weeks.
   - It makes the workload independent of the hardware. A VM is a set of files, so it can be moved to a newer server, or to a different vendor's server, without reinstalling anything.
   - It enables live migration, so a running workload moves to another host while the physical server is serviced or upgraded, with no downtime at all.
   - It gives snapshots and instant rollback, so an upgrade or a patch can be reversed in seconds if it goes wrong.
   - It improves availability. If the physical server fails, its VMs are restarted automatically on another host in the cluster.
   - It simplifies backup and disaster recovery, since a whole server can be replicated to a second site as a file.
   - It extends the life of legacy applications, because an old operating system that will not install on modern hardware still runs happily inside a VM.
5. **Define a virtual machine with a neat diagram, explain the working of VM. What are the benefits of a VM?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 442 (ET: BIBM)]*


   Answer:

   Definition:
   - A virtual machine is a software emulation of a physical computer. It has its own virtual CPU, memory, disk and network interface, runs its own complete guest operating system, and behaves exactly as an independent machine, although it is actually sharing the hardware of a physical host with other virtual machines.

   Diagram:

   ```mermaid
   graph TD
       A["Physical Hardware: CPU, RAM, Disk, NIC"] --> B["Hypervisor: VMware ESXi, KVM, Hyper-V"]
       B --> C["VM 1: Guest OS Linux + Apps"]
       B --> D["VM 2: Guest OS Windows + Apps"]
       B --> E["VM 3: Guest OS Linux + Database"]
   ```

   Working of a VM:
   - The hypervisor sits between the physical hardware and the virtual machines and owns all the real resources.
   - When a VM is created, the hypervisor allocates it a share of CPU cores, a block of memory, a virtual disk file and a virtual network adapter.
   - The guest operating system inside the VM believes it is talking to real hardware. When it issues a privileged instruction or an I/O request, the hypervisor intercepts it, translates it to the real hardware and returns the result. Modern CPUs help this directly with Intel VT-x and AMD-V, so the overhead is small.
   - The hypervisor schedules the virtual CPUs of all the VMs onto the physical cores, maps guest memory pages to host memory, and multiplexes the disk and network.
   - Each VM is kept in its own memory space, so it cannot read or affect another VM. From outside, a VM is simply a set of files, which is why it can be copied, moved, snapshotted and restored.
   - Type 1 hypervisors run straight on the hardware and are used in production; Type 2 hypervisors run inside a host operating system and are used on desktops.

   Benefits of a VM:

   - Server consolidation: many virtual machines run on one physical server, so utilisation rises from a typical 10 to 15 percent to 70 or 80 percent and far fewer machines are needed.
   - Cost saving: less hardware means less capital expenditure, less rack space, less power and less cooling.
   - Isolation: each VM is separated from the others, so a crash or a compromise in one does not affect the rest.
   - Rapid provisioning: a new server is created from a template in minutes rather than weeks.
   - Snapshots and rollback: the entire state of a machine can be saved before a risky change and restored instantly if it fails.
   - Live migration: a running VM can be moved to another host with no downtime, allowing hardware maintenance during working hours.
   - High availability and disaster recovery: VMs restart automatically on another host if one fails, and replication to a second site is straightforward.
   - Hardware independence: a VM is just a set of files, so it runs on any host with the same hypervisor.
   - Legacy support: an old operating system that no longer runs on modern hardware can continue inside a VM.
   - Excellent for testing and development, since several operating systems can be tried on one machine and reset at will.
6. **What is docker? An application running on windows server shifted in linux server. What problem will occur? Can Docker solve it?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*


   Answer:

   What Docker is:
   - Docker is a containerisation platform that packages an application together with all its dependencies — libraries, runtime, configuration files and environment variables — into a single portable unit called a container image.
   - Containers share the host operating system kernel rather than each carrying a full guest OS, so they are megabytes rather than gigabytes in size and start in seconds.
   - Key concepts: the Dockerfile describes how to build the image, the image is the immutable package, the container is a running instance of it, and Docker Hub is the registry where images are stored.

   Problems when an application is moved from a Windows server to a Linux server:
   - Different system libraries and runtimes: a program built against the Windows API, the .NET Framework or specific DLLs will not run on Linux at all.
   - Path and file system differences: backslash versus forward slash, drive letters versus a single root, and Linux is case sensitive while Windows is not, so `Config.xml` and `config.xml` are different files.
   - Line ending differences, CRLF against LF, which break scripts and configuration parsing.
   - Permissions and user model: NTFS ACLs against POSIX ownership and permission bits, so file access fails.
   - Service management differs: Windows Services against systemd, so the startup mechanism must be rewritten.
   - Registry dependence: any setting stored in the Windows registry has no equivalent on Linux.
   - Environment differences: different versions of the runtime, the database client, OpenSSL and other libraries, which produces the classic "it works on my machine" failure.
   - Different default character encodings and time zone handling.

   Can Docker solve it?
   - Partly, and this is the honest answer the examiner is looking for.
   - What Docker does solve: the environment and dependency problem completely. Because the image contains the exact runtime, libraries and configuration the application needs, the container behaves identically on any host that runs Docker. Path, permission and library version mismatches disappear, deployment becomes one command, and the same image runs on the developer's laptop, in test and in production.
   - What Docker does not solve: the operating system boundary itself. Containers share the host kernel, so a Windows container cannot run on a Linux host and a Linux container cannot run natively on a Windows host. If the application genuinely depends on the Windows API or the .NET Framework, packaging it in a Linux container is impossible; the code has to be ported, for example to .NET Core or .NET 5 and later, which is cross platform.
   - The practical routes are therefore: port the application to a cross platform runtime and then containerise it, which is the correct long term solution; or run it in a Windows container on a Windows host; or, if porting is not possible, run the original Windows server as a virtual machine on the Linux host, since a VM does carry its own kernel and can therefore cross the operating system boundary that a container cannot.

## Cluster, Grid & Distributed Computing (3)

1. **(ক) উদাহরণসহ distributed এবং centralized computing -এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer:

   Centralized computing:
   - Ekti kendrio computer ba server-e shob processing, storage ar niyontron thake; byabaharkari-ra terminal ba client diye shudhu tar sathe jukto hoy.
   - Boishishtho: ek jaigay data, ek jaigay niyontron, sohoj babosthapona ar backup, kintu oi ekti machine-i single point of failure.
   - Udahoron: purono mainframe babostha, ekti bank-er shakhar shob terminal ekti kendrio server-er sathe jukto, ba ekti office-er ekti file server.

   Distributed computing:
   - Onek swadhin computer network-e jukto hoye ekshathe kaj kore, ar byabaharkari-r kache ta ekti-i babostha mone hoy. Kaj ar data onek node-e bhag kore deoa hoy.
   - Boishishtho: kono single point of failure nei, horizontal scaling somvob, ekti node noshto hole baki gulo cholte thake, kintu synchronization, consistency ar network delay-er somossa toiri hoy.
   - Udahoron: Internet nijei, Google-er search infrastructure, Hadoop ar Spark cluster, blockchain, ar DNS.

   | Bishoy | Centralized | Distributed |
   |---|---|---|
   | Processing | Ek jaigay | Onek node-e bhag kora |
   | Failure | Single point of failure | Fault tolerant |
   | Scalability | Vertical, mane boro machine kena | Horizontal, mane aro node jog kora |
   | Khoroch | Prathomik boro machine dami | Sadharon hardware onek gulo, tai kom |
   | Babosthapona | Sohoj | Jotil, synchronization lage |
   | Latency | Kom, ek jaigay | Beshi hote pare, network-er upor nirbhorshil |
2. **Difference between cluster computing and grid computing.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 750 (ET: N/A)]*


   Answer:

   | Point | Cluster computing | Grid computing |
   |---|---|---|
   | Composition | Homogeneous nodes, same hardware and OS | Heterogeneous nodes, different hardware, OS and owners |
   | Location | All nodes in one place, in one LAN or one data centre | Geographically distributed, connected over a WAN or the Internet |
   | Ownership and administration | A single organisation, one administrative domain | Many organisations, many administrative domains |
   | Coupling | Tightly coupled, high speed low latency interconnect | Loosely coupled, ordinary Internet links |
   | Resource sharing | Dedicated nodes, always available to the cluster | Volunteer or spare capacity, nodes join and leave freely |
   | Scheduling | Centralised scheduler in the cluster | Distributed grid middleware negotiating across domains |
   | Task type | Suits tightly coupled parallel work with heavy inter-node communication | Suits independent, embarrassingly parallel tasks |
   | Appearance | Behaves as one single powerful machine | Behaves as a shared pool of resources |
   | Failure handling | A node failure is handled by the cluster manager | Nodes are expected to disappear; work is simply reassigned |
   | Examples | A web server farm, a database cluster, a Beowulf HPC cluster | SETI@home, Folding@home, the CERN Worldwide LHC Computing Grid |

   - In one sentence: a cluster is many machines in one room acting as one computer, while a grid is many computers in many places lending their spare capacity to a common task.
3. **Imagine data in a system is green, red, yellow and blue in the system using distributed server in parallel. Design the system using reduce map.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*


   Answer: MapReduce is used to count the four colours in parallel across the distributed servers.

   ```mermaid
   graph LR
       A["Input data split into blocks"] --> B["Mapper 1"]
       A --> C["Mapper 2"]
       A --> D["Mapper 3"]
       B --> E["Shuffle and Sort by key: colour"]
       C --> E
       D --> E
       E --> F["Reducer: green"]
       E --> G["Reducer: red"]
       E --> H["Reducer: yellow"]
       E --> I["Reducer: blue"]
       F --> J["Final output"]
       G --> J
       H --> J
       I --> J
   ```

   Step 1, Input split:
   - The dataset is divided into blocks, typically 128 MB each, and the blocks are distributed across the servers of the cluster. Each block is processed by a mapper running on the server that already holds the data, which is the principle of data locality: move the computation to the data, not the data to the computation.

   Step 2, Map phase:
   - Each mapper reads its block record by record and emits a key value pair for every item, where the key is the colour and the value is 1.
   - Mapper 1 might emit (green, 1), (red, 1), (green, 1); mapper 2 might emit (blue, 1), (yellow, 1), (red, 1), and so on. The mappers run completely in parallel and never talk to each other.

   Step 3, Combiner, an optional local optimisation:
   - Before the data leaves the node, a combiner performs a local sum, so mapper 1 sends (green, 2), (red, 1) instead of three separate pairs. This greatly reduces the network traffic in the next phase.

   Step 4, Shuffle and Sort:
   - The framework groups all the values belonging to the same key and sends each group to a single reducer, so that all the green counts from every mapper arrive at the same reducer. With four colours there are four keys, so four reducers can be used.

   Step 5, Reduce phase:
   - Each reducer receives one colour and the list of counts for it, adds them, and emits the total: (green, 4500), (red, 3200), (yellow, 2100), (blue, 1900).

   Step 6, Output:
   - The four results are written to the distributed file system as the final output.

   Pseudocode:

   ```
   map(key, record):
       for each item in record:
           emit(item.colour, 1)

   combine(colour, counts):        # runs locally on each mapper node
       emit(colour, sum(counts))

   reduce(colour, counts):
       emit(colour, sum(counts))
   ```

   Why this design is correct:
   - The work is embarrassingly parallel, so throughput scales almost linearly with the number of servers.
   - The number of reducers is chosen as the number of distinct keys, here four, so each reducer does an equal share.
   - If one node fails, the framework simply re-runs its task elsewhere, since the map function is deterministic and has no side effects.
   - The combiner keeps the shuffle traffic small, which is normally the bottleneck of a MapReduce job.
   - One risk worth stating: if one colour dominates the data, its reducer becomes a hotspot. This is data skew, and it is handled by adding a random salt to the key and running a second reduce pass.

## Scalability (Horizontal & Vertical Scaling) (2)

1. **Server rack digram to draw horizontal and vertical scalling.** *[RPGCL Assistant Manager (ICT) 2022 compact it 655 (ET: BUET)]*


   Answer:

   Vertical scaling, that is scaling up, means making one server more powerful. Horizontal scaling, that is scaling out, means adding more servers.

   ```
   VERTICAL SCALING (scale up)          HORIZONTAL SCALING (scale out)
   one rack slot, a bigger server       more rack slots, more servers

   +---------------------------+        +----------+ +----------+ +----------+
   |  Server 1                 |        | Server 1 | | Server 2 | | Server 3 |
   |  4 CPU  -> 32 CPU         |        | 4 CPU    | | 4 CPU    | | 4 CPU    |
   |  16 GB  -> 256 GB         |        | 16 GB    | | 16 GB    | | 16 GB    |
   |  1 TB   -> 20 TB          |        | 1 TB     | | 1 TB     | | 1 TB     |
   +---------------------------+        +----------+ +----------+ +----------+
        the same one machine                    \        |        /
        grows in capacity                        +-------------------+
                                                 |   Load Balancer   |
                                                 +-------------------+
   ```

   | Point | Vertical scaling, scale up | Horizontal scaling, scale out |
   |---|---|---|
   | Method | Add CPU, RAM or disk to the existing server | Add more servers to the pool |
   | Limit | Hard: there is a maximum size of machine that can be bought | Practically unlimited |
   | Downtime | Usually needed, the server must be shut down to be upgraded | None, a new node is simply added |
   | Cost curve | Rises steeply; high end hardware is disproportionately expensive | Linear; ordinary commodity servers are added |
   | Fault tolerance | None, still a single point of failure | High, the load balancer routes around a failed node |
   | Complexity | Simple, the application does not change | Complex: needs a load balancer, session handling and data consistency |
   | Application requirement | Works with any application | The application must be stateless or share its state |
   | Typical use | Relational databases, legacy monolithic applications | Web servers, microservices, NoSQL databases, cloud native applications |

   - Cloud practice: horizontal scaling is preferred, because it is elastic, fault tolerant and cheap, and auto-scaling groups add and remove nodes automatically according to load. Vertical scaling is still used for the database tier, which is hardest to distribute.
2. **Difference between elasticity and scalability of resources in the cloud.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 749 (ET: N/A)]*


   Answer:

   | Point | Scalability | Elasticity |
   |---|---|---|
   | Meaning | The ability of a system to handle a growing workload by adding resources | The ability to add and remove resources automatically, in real time, as demand changes |
   | Direction | Growth, generally one way and planned | Both ways, expanding and contracting continuously |
   | Timescale | Long term, planned in advance by the architect | Short term, minute by minute and automatic |
   | Trigger | A human decision or a capacity plan | An automatic rule, for example CPU above 70 percent for 5 minutes |
   | Purpose | To meet a predicted long term increase in demand | To match unpredictable short term fluctuations and to avoid paying for idle capacity |
   | Cost effect | Capacity is provisioned for the expected peak and paid for continuously | Cost follows actual usage, so nothing is paid for unused capacity |
   | Applies to | Both on-premises and cloud systems | Essentially a cloud property; it needs pooled resources and pay per use billing |
   | Example | Designing an e-commerce platform so that servers can be added as the business grows over three years | The same platform automatically adding twenty servers during an Eid sale and removing them the next morning |

   - Relationship: elasticity is not possible without scalability, but scalability alone is not elasticity. A system may be highly scalable yet require a week and a purchase order to grow, in which case it is scalable but not elastic.
   - Types of scalability: vertical, that is a bigger machine, and horizontal, that is more machines. Elasticity in practice is nearly always horizontal, implemented by auto-scaling groups with a load balancer.

## Edge Computing & Fog Computing (2)

1. **What is the need of edge server?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*


   Answer: An edge server is needed because processing data close to where it is produced overcomes the limits of sending everything to a distant central cloud.

   The need for edge servers:
   - Latency: a round trip to a central cloud may take 50 to 200 ms, which is far too slow for an autonomous vehicle, an industrial robot, a video analytics camera or an augmented reality headset. An edge server a few kilometres away answers in single digit milliseconds.
   - Bandwidth cost and capacity: a single high definition camera produces several Mbps continuously. Sending the raw stream of hundreds of cameras to the cloud is neither affordable nor physically possible, particularly where international bandwidth is expensive. The edge server processes the video locally and sends only the events that matter.
   - Data volume from IoT: millions of sensors generate far more data than is worth transporting. Filtering and aggregating at the edge reduces the volume by orders of magnitude.
   - Reliability and offline operation: a factory, a hospital or a remote site must keep functioning when the WAN link fails. An edge server keeps the local service running and synchronises later.
   - Privacy, security and compliance: sensitive data such as patient records, faces or national data can be processed locally and never leave the country or the building, which satisfies data residency laws.
   - Real time decisions: safety critical control, such as stopping a machine when a person enters a danger zone, cannot depend on a network link at all.
   - Content delivery: a CDN edge server caches web content, video and software updates near the users, so pages load faster and the origin server and the international link are relieved.
   - Scalability: distributing the processing across many edge nodes removes the central bottleneck and lets the system grow geographically.

   - Typical deployments: CDN points of presence, 5G multi-access edge computing at the base station, smart factories, retail stores, and cable landing or telecom exchange sites.
2. **(গ) Edge Computing এর ধারণা সংক্ষেপে উপস্থাপন করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer:

   Edge Computing ki:
   - Edge Computing holo emon ekti computing model jekhane data jekhane toiri hoy tar kachakachi-i processing kora hoy, dur-er kono kendrio cloud data centre-e na pathiye.
   - "Edge" mane network-er prantobhag — mane sensor, camera, IoT device, ba tader kachakachi thaka choto server ba gateway.

   Kivabe kaj kore:
   - Device ba edge server sthaniyo bhabe data songroho kore, filter kore, bishleshon kore ar sathe sathe siddhanto ney.
   - Shudhu joruri ba songkhipto phalafol cloud-e pathano hoy, dirghomeyadi songrokkhon ar boro bishleshon-er jonno.

   Keno dorkar:
   - Kom latency: cloud-e jete-aste 50 theke 200 ms lage, ja self-driving car, industrial robot ba real-time video analytics-er jonno onek beshi. Edge-e uttor ashe koyek millisecond-e.
   - Bandwidth bachano: shoto shoto HD camera-r kancha video cloud-e pathano ashombhob ar khub dami; edge-e process kore shudhu ghotona pathano hoy.
   - Nirbhorjogyota: Internet link gele-o sthaniyo babostha cholte thake ebong pore sync kore.
   - Gopaniyota ar ain: rogi-r tothyo ba mukhomondol-er chobi sthaniyo bhabe process kore desher bhitorei rakha jay.
   - Real-time nirapotta siddhanto, jemon bipojjonok elakay manush dhukle machine bondho kora — eta network-er upor nirbhor korte pare na.

   Udahoron:
   - CDN-er edge server, 5G-r Multi-access Edge Computing, smart factory-r local controller, smart city-r traffic camera, ar smartwatch-er sthaniyo health analysis.

   Fog Computing-er sathe somporko:
   - Fog Computing edge ar cloud-er majhkhaner ekti star, jekhane gateway ba router porjaye processing hoy. Edge shob theke kache, Fog majhkhane, ar Cloud shob theke dure.

## Virtualization & Resource Allocation (1)

1. A physical server has 32 CPU cores, 96\text{ GB} RAM, and 4\text{ TB} storage. Each virtual machine (VM) requires 4 CPU cores, 16\text{ GB} RAM, and 500\text{ GB} storage. Calculate the maximum number of VMs that can be hosted on the server without overcommitting resources. Identify which hardware resource limits the number of VMs. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer:

   Given:
   - Physical server: 32 CPU cores, 96 GB RAM, 4 TB storage.
   - Each VM: 4 CPU cores, 16 GB RAM, 500 GB storage.

   Step 1, maximum VMs allowed by each resource:
   - By CPU: 32 ÷ 4 = 8 VMs
   - By RAM: 96 ÷ 16 = 6 VMs
   - By storage: 4 TB ÷ 500 GB = 4096 GB ÷ 500 GB = 8.19, so 8 VMs

   Step 2, take the minimum, since every VM needs all three resources at once:
   - Minimum of 8, 6 and 8 = 6

   Final answer: a maximum of 6 virtual machines can be hosted without overcommitting any resource.

   Limiting resource:
   - RAM is the limiting resource, because it allows only 6 VMs while CPU and storage would each allow 8.

   Leftover capacity with 6 VMs:
   - CPU used = 6 × 4 = 24 cores, leaving 8 cores idle.
   - RAM used = 6 × 16 = 96 GB, leaving 0 GB, which is the bottleneck.
   - Storage used = 6 × 500 GB = 3000 GB, leaving about 1 TB free.

   - Practical note the examiner values: memory is the resource that most often limits virtual machine density in real deployments, because CPU can be safely overcommitted, since VMs rarely peak together, whereas RAM cannot be overcommitted without severe swapping. Adding 32 GB of RAM here would raise the limit to 8 VMs and use the CPU and storage fully. A further reservation of about 4 to 8 GB for the hypervisor itself should also be made in a real design, which would reduce the count to 5.

## High Availability & System Redundancy (1)

1. High-Availability Design: [BSCCPL AME 21-08-2026 (BUET)] A submarine cable operator wants to ensure that a DNS service remains available even if one physical server fails. where VM/container technology helps and where network redundancy is required.


   Answer: The DNS service must survive the loss of any single component, so redundancy is needed at three levels: the service, the server and the network.

   Where VM or container technology helps:
   - Rapid recovery: if a physical host fails, its VMs are automatically restarted on another host in the cluster within a minute or two, so the DNS service returns without any manual rebuild.
   - Live migration: a running DNS VM can be moved to another host with no downtime while the original server is patched or repaired, which removes planned outages entirely.
   - Multiple instances: two or more DNS VMs or containers are run on different physical hosts, with an anti-affinity rule forcing the hypervisor to keep them apart, so one host failure never takes both down.
   - Fast rebuild from an image: a DNS container starts in seconds from a known good image, so a corrupted instance is replaced rather than repaired.
   - Snapshots and rollback: a bad configuration or a bad zone file is reverted instantly.
   - Efficient use of hardware: the standby instance does not need a whole dedicated physical server, so real redundancy becomes affordable.
   - Orchestration: Kubernetes or a similar platform health checks the containers and restarts or reschedules an unhealthy one automatically, and keeps the desired number of replicas running at all times.

   Where network redundancy is required, and why virtualisation alone is not enough:
   - Virtualisation protects against server and software failure, but it cannot help if the path to the server is broken. If the single switch, the single uplink or the single power feed fails, every VM on that host becomes unreachable even though it is running perfectly.
   - Dual network interfaces on each host, teamed or bonded, connected to two different switches, so a NIC or a cable failure is survived.
   - Redundant switches with MLAG or stacking, and Spanning Tree or a loop free fabric, so a switch failure does not isolate the servers.
   - Redundant routers with VRRP or HSRP, so the default gateway address survives the loss of a router.
   - Diverse WAN and upstream paths: at a cable landing station this means separate submarine cable systems and separate terrestrial routes, so one cable cut does not remove connectivity.
   - Anycast for the DNS service address: the same IP is advertised by BGP from several sites, so resolvers are drawn automatically to the nearest healthy instance and a failed site simply withdraws its route. This is how the DNS root servers achieve availability, and it is the single most important measure for DNS specifically.
   - Redundant power, dual feeds, UPS and generator, and redundant cooling.
   - Geographic redundancy: a second DNS instance in a physically separate site, so a fire, a flood or a power failure at one location does not remove the service.

   Recommended combined design:
   - Two physical hosts, each running a DNS VM or container, kept apart by an anti-affinity rule.
   - Each host dual homed to two switches, and the switches connected to two routers running VRRP.
   - The DNS service address advertised by anycast from both the primary site and a geographically separate secondary site.
   - Health checks that withdraw the route from an instance that stops answering queries, plus monitoring and alerting.
   - In one sentence: virtualisation gives redundancy of the service, and network redundancy gives redundancy of the path; a highly available DNS needs both, because either one alone leaves a single point of failure.

## Cloud Security & Compliance (1)

1. **How do assessment and audit reports help detect vulnerabilities and ensure compliance to cloud security posture?** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1431 (ET: BUET)]*


   Answer: Assessment and audit reports are the evidence base of cloud security posture management: an assessment finds what is wrong, and an audit proves what is in place.

   How they help detect vulnerabilities:
   - Configuration assessment: automated scanning against benchmarks such as CIS finds the misconfigurations that cause most cloud breaches — a publicly readable storage bucket, a security group open to 0.0.0.0/0, an unencrypted database, disabled logging, or a default password left in place.
   - Vulnerability scanning: workloads, container images and functions are scanned for unpatched software and known CVEs, and the findings are ranked by severity so the most dangerous are fixed first.
   - Identity and access review: audit reports expose over-privileged roles, unused access keys, accounts without multi-factor authentication and orphaned accounts of former staff, which is where privilege escalation begins.
   - Log and activity analysis: reviewing CloudTrail or equivalent logs reveals unusual API calls, access from unexpected countries, and privilege changes made outside the change window.
   - Penetration testing and red team reports: these show whether the vulnerabilities found are actually exploitable in combination, which a scanner cannot judge.
   - Drift detection: comparing the running environment with the approved infrastructure as code baseline shows every change made outside the process, which is a common source of silent exposure.
   - Trend analysis: comparing successive reports shows whether the posture is improving or degrading, and whether fixes are actually being completed rather than repeatedly deferred.

   How they ensure compliance:
   - Mapping controls to frameworks: the report maps the technical findings to the requirements of ISO 27001, PCI DSS, SOC 2, GDPR or the local regulator's guideline, so gaps are expressed in the language the regulator uses.
   - Evidence for auditors and regulators: dated reports, logs and remediation records constitute the documentary proof that controls existed and operated throughout the period, which is what an external audit actually tests.
   - Shared responsibility clarity: the provider's own SOC 2 and ISO certificates cover the infrastructure, while the customer's assessment covers configuration, identity and data. Together they show the whole picture, and they make clear which failures belong to whom.
   - Data residency and encryption verification: reports confirm where data is physically stored and that encryption at rest and in transit is actually enabled, which matters directly for banking and government data in Bangladesh.
   - Continuous compliance: cloud posture management tools evaluate the environment continuously rather than once a year, so a violation is detected within minutes instead of at the next audit.
   - Accountability and governance: findings are assigned owners and deadlines, and management reporting makes residual risk a conscious business decision rather than an accident.
   - Third party and vendor assurance: audit reports of the provider and of SaaS vendors support the due diligence required before a service is approved.

   - The practical cycle is: assess, prioritise by risk, remediate, verify, and report — repeated continuously, because a cloud environment changes daily and a posture verified last month proves nothing about today.
