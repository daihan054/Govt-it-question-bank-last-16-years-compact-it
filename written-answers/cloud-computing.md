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
   - The startup does not want to manage hardware, OS or runtime. PaaS gives exactly that. The provider supplies the servers, the OS, the runtime, the middleware and the database. The startup supplies only its own code and data.
   - IaaS is not right. They would still have to install and patch the OS and the runtime. That is exactly what they want to avoid.
   - SaaS is not right either. It gives a finished application to use, not a place to run your own code.
   - PaaS also gives automatic scaling, ready deployment pipelines and managed backups. So a very small team can run a live service.

   Two real-world examples:
   - Heroku: the developer pushes code with `git push heroku main`, and the platform builds and runs it.
   - Google App Engine: it runs the application and scales it automatically as traffic changes.
   - Other correct answers: AWS Elastic Beanstalk, Microsoft Azure App Service, Red Hat OpenShift.
2. What is cloud computing? Mention its service models. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*


   Answer:

   - Cloud computing means we get computing services over the Internet and pay only for what we use. These services are servers, storage, databases, networking, software and analytics. We do not buy or run the physical hardware ourselves.
   - NIST lists five key features: on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Service models:

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What it provides | Virtualised computing resources over the internet: servers, storage and networking, on a rental basis | A ready to use platform for building, testing, deploying and managing applications | A fully working, ready to use software application, usually on subscription |
   | The user controls | The operating system, the applications and the data | Only the application code and the data | Nothing. Only the data and the settings |
   | The provider manages | The physical infrastructure: hardware, virtualisation, network, storage | Servers, storage and the whole runtime environment | Absolutely everything: infrastructure, updates, bug fixes and security |
   | How much the customer manages | The most | Less | The least |
   | Who it is for | System administrator, network engineer | Application developer | End user |
   | Popular providers | AWS EC2, Microsoft Azure Virtual Machines, Google Compute Engine, DigitalOcean | AWS Elastic Beanstalk, Google App Engine, Heroku, Microsoft Azure App Service | Salesforce, Microsoft Office 365, Google Workspace, Dropbox, Zoho, Slack |
   | Car analogy | You rent a car and drive it yourself | You hire a car with a driver | You take a taxi |

   - Deployment models: public cloud, private cloud, hybrid cloud and community cloud.
3. **What is SaaS and multi-tenant architecture? How are they related? What are the advantages and disadvantages of multi-tenancy? For a multi-vendor e-commerce application, you can choose a database architecture where you can put all the vendors in a single database or each vendor in a separate database. Which architecture will you follow and why?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 328 (ET: BIBM)]*


   Answer:

   SaaS:
   - Software as a Service means the provider hosts a complete application and gives it to customers over the Internet, usually on subscription. The customer installs nothing. It manages only its own data and settings. Examples: Gmail, Salesforce, Office 365, Zoom.

   Multi-tenant architecture:
   - One running copy of the application, and usually one shared database, serves many customers. We call each customer a tenant. Each tenant's data is kept separate by logic, so no tenant can see another tenant's data, even though they share the same resources.
   - The opposite is single tenancy. There each customer gets its own separate copy and its own database.

   How they are related:
   - Multi-tenancy is what makes SaaS affordable. Running one shared copy for ten thousand customers costs far less than running ten thousand separate copies. That saving is why SaaS can be sold at a low monthly price. In practice, almost every big SaaS product is multi-tenant.

   Advantages of multi-tenancy:
   - Much lower cost per customer, because hardware, licences and operations work are all shared.
   - One codebase and one deployment. So an update or a security patch reaches every customer at the same time.
   - Better use of resources, because different tenants are busy at different times.
   - Adding a new customer is easy. It is just a new configuration row, not a new server.
   - Monitoring, backup and scaling are done centrally for everyone.

   Disadvantages of multi-tenancy:
   - Noisy neighbour problem: one heavy tenant can slow the system down for everybody.
   - The security risk is concentrated. One bug in the tenant separation logic can expose every customer's data.
   - Little room for customisation, because the schema and the code must suit all tenants.
   - One bug or one bad deployment brings down all the tenants together.
   - Compliance is hard. If a customer must keep its data in another country, or under its own encryption keys, that is difficult to arrange.
   - Development is harder. Every query must filter by tenant, and one missing filter means a serious data leak.

   Which database architecture for a multi-vendor e-commerce application:
   - For most vendors I would choose one shared database, with a `vendor_id` column on every table. This is the shared schema multi-tenant model.

   Reasons:
   - Cost and scalability: an e-commerce platform may have thousands of small vendors. Thousands of separate databases would mean thousands of connection pools, backups and migration jobs. That is too costly and impossible to manage.
   - Cross-vendor features become easy. Product search across all vendors, one cart holding items from several vendors, platform wide analytics and recommendations all need queries across vendors. That is simple in one database, and very painful across many.
   - We apply a schema change once, not thousands of times. So releases are fast and the same everywhere.
   - A new vendor can join instantly, which matters a lot for a marketplace.
   - Better use of hardware, because most vendors are small and idle most of the time.

   How the risks are controlled:
   - Every table carries `vendor_id`, and every query filters on it. We enforce this in one data access layer, instead of trusting each developer to remember it.
   - Row level security in the database gives a second line of defence, separate from the application code.
   - Partitioning or sharding by `vendor_id` keeps the large tables manageable.
   - For the biggest vendors we use a hybrid approach. A very large vendor with special compliance or performance needs is moved to its own database or its own shard. All the small vendors stay in the shared one. Real marketplaces work this way.
4. **6.11 A startup company wants to launch a new web application. They do not want to manage any underlying hardware, operating systems, or even the runtime environment; they only want to focus on writing and deploying their code. Based on your understanding of Cloud Service Models, which model (IaaS, PaaS, or SaaS) is most appropriate for them? Provide two real-world examples of platforms that provide this specific type of service.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer: PaaS, Platform as a Service, is the appropriate model.

   Reason:
   - The requirement says clearly: do not manage hardware, OS or runtime, and focus only on writing and deploying code. That is exactly what PaaS is. The provider manages everything up to the runtime. The customer manages only the application and its data.
   - We reject IaaS, because the customer would still have to install, patch and secure the OS and the runtime.
   - We reject SaaS, because it gives a finished application, not a place to run your own code.

   Two real-world examples:
   - Heroku
   - Google App Engine
   - These are also correct: AWS Elastic Beanstalk, Microsoft Azure App Service, Red Hat OpenShift.

   Additional benefits for a startup:
   - Automatic scaling as traffic grows, ready deployment and rollback, managed database add-ons, and no need to hire a system administrator. So a very small team can run a live service.
5. **Describe SaaS, IaaS and PaaS.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*


   Answer: These are the three service models of cloud computing. They differ in how much the provider manages, and how much is left to the customer.

   SaaS, Software as a Service:
   - A complete, ready to use application, given over the Internet, usually on subscription. The customer manages nothing except its own data and settings. There is nothing to install, nothing to patch and no server to look after.
   - Examples: Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom.

   PaaS, Platform as a Service:
   - A ready platform that already has the OS, web server, database and development tools. The customer just deploys its own code on it. The provider manages everything below the application.
   - Examples: Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service.

   IaaS, Infrastructure as a Service:
   - Raw virtual infrastructure, that is virtual machines, storage and networking, rented on demand. The customer installs and manages the OS, the middleware and the applications. So the customer keeps the most control.
   - Examples: AWS EC2, Google Compute Engine, Azure Virtual Machines, DigitalOcean.

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What it provides | Virtualised computing resources over the internet: servers, storage and networking, on a rental basis | A ready to use platform for building, testing, deploying and managing applications | A fully working, ready to use software application, usually on subscription |
   | The user controls | The operating system, the applications and the data | Only the application code and the data | Nothing. Only the data and the settings |
   | The provider manages | The physical infrastructure: hardware, virtualisation, network, storage | Servers, storage and the whole runtime environment | Absolutely everything: infrastructure, updates, bug fixes and security |
   | How much the customer manages | The most | Less | The least |
   | Who it is for | System administrator, network engineer | Application developer | End user |
   | Popular providers | AWS EC2, Microsoft Azure Virtual Machines, Google Compute Engine, DigitalOcean | AWS Elastic Beanstalk, Google App Engine, Heroku, Microsoft Azure App Service | Salesforce, Microsoft Office 365, Google Workspace, Dropbox, Zoho, Slack |
   | Car analogy | You rent a car and drive it yourself | You hire a car with a driver | You take a taxi |
6. **Explain IaaS, PaaS, and SaaS with respect to cloud computing.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*


   Answer: IaaS, PaaS and SaaS are the three service models of cloud computing. They differ in where the line of responsibility falls between the provider and the customer.

   IaaS, Infrastructure as a Service:
   - The provider gives virtual hardware: compute, storage and network. The customer chooses and installs the OS and everything above it.
   - It gives the most control and freedom. We use it when an organisation wants to move its existing servers to the cloud without changing how they are built.
   - Examples: AWS EC2, Azure Virtual Machines, Google Compute Engine.

   PaaS, Platform as a Service:
   - The provider gives the whole runtime stack: OS, web server, runtime, database and development tools. The customer gives only the application code and its data.
   - It takes all the infrastructure work away from the developer. It also adds automatic scaling and deployment pipelines. But it gives less control over the environment.
   - Examples: Heroku, Google App Engine, AWS Elastic Beanstalk.

   SaaS, Software as a Service:
   - The provider gives a complete finished application over the Internet. The customer just uses it, and manages only its own data and settings.
   - It is the easiest to start with, and the least flexible. It is normally multi-tenant, that is one shared copy serving many customers.
   - Examples: Gmail, Office 365, Salesforce.

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What it provides | Virtualised computing resources over the internet: servers, storage and networking, on a rental basis | A ready to use platform for building, testing, deploying and managing applications | A fully working, ready to use software application, usually on subscription |
   | The user controls | The operating system, the applications and the data | Only the application code and the data | Nothing. Only the data and the settings |
   | The provider manages | The physical infrastructure: hardware, virtualisation, network, storage | Servers, storage and the whole runtime environment | Absolutely everything: infrastructure, updates, bug fixes and security |
   | How much the customer manages | The most | Less | The least |
   | Who it is for | System administrator, network engineer | Application developer | End user |
   | Popular providers | AWS EC2, Microsoft Azure Virtual Machines, Google Compute Engine, DigitalOcean | AWS Elastic Beanstalk, Google App Engine, Heroku, Microsoft Azure App Service | Salesforce, Microsoft Office 365, Google Workspace, Dropbox, Zoho, Slack |
   | Car analogy | You rent a car and drive it yourself | You hire a car with a driver | You take a taxi |
7. **What do you mean by multi-tenancy in the cloud? Why is it beneficial for cloud service providers?** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 749 (ET: N/A)]*


   Answer:

   Multi-tenancy in the cloud:
   - Multi-tenancy means one copy of an application, or one set of physical resources, serves many separate customers at the same time. We call each customer a tenant. Each tenant's data and settings are kept apart by logic, so no tenant can see or disturb another, even though they share the same software and hardware.
   - It comes in several levels: shared hardware with separate VMs; a shared application with separate databases; and a fully shared application and database, with a tenant id on every record.
   - The opposite is single tenancy, where each customer gets its own dedicated copy.

   Why it is beneficial for cloud service providers:
   - Economy of scale: one deployment serves thousands of customers. So hardware, licences, power and staff are all shared, and the cost per customer drops sharply. This is why a service can be sold for a few dollars a month.
   - High resource use: tenants are busy at different times, and most are idle most of the time. So pooled resources are used far better than dedicated ones.
   - One codebase and one deployment: we write a feature or a security patch once, and it reaches every customer at once. We do not have to roll it out to thousands of separate installations.
   - Fast onboarding: adding a customer is just a configuration change, not a new server build. So the business can grow without the operations work growing at the same rate.
   - Monitoring, backup, scaling and support are all central. This cuts the operational work a great deal.
   - Capacity planning is easier. The total demand of many tenants is much smoother and easier to predict than the demand of any single tenant.
   - Higher profit margin, because the extra cost of one more customer is very small.

   - In return, the provider must give strong tenant separation, must stop the noisy neighbour problem with quotas and throttling, and must promise clear data separation in the service level agreement.
8. **(ক) Cloud Computing এর সার্ভিসগুলো লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*

   Answer: The three main service models of cloud computing:

   - SaaS, Software as a Service: a complete ready made application, used over the Internet. The user installs nothing and maintains nothing. It manages only its own data and settings. Examples: Gmail, Google Docs, Office 365, Salesforce, Dropbox, Zoom.
   - PaaS, Platform as a Service: a ready platform that already has the OS, runtime, database and development tools. The developer deploys only its own code on it. Examples: Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service.
   - IaaS, Infrastructure as a Service: virtual machines, storage and networking, that is the raw infrastructure, rented on demand. The customer installs and controls everything from the OS upwards. Examples: AWS EC2, Google Compute Engine, Azure VM, DigitalOcean.

   | Point | IaaS | PaaS | SaaS |
   |---|---|---|---|
   | What it provides | Virtualised computing resources over the internet: servers, storage and networking, on a rental basis | A ready to use platform for building, testing, deploying and managing applications | A fully working, ready to use software application, usually on subscription |
   | The user controls | The operating system, the applications and the data | Only the application code and the data | Nothing. Only the data and the settings |
   | The provider manages | The physical infrastructure: hardware, virtualisation, network, storage | Servers, storage and the whole runtime environment | Absolutely everything: infrastructure, updates, bug fixes and security |
   | How much the customer manages | The most | Less | The least |
   | Who it is for | System administrator, network engineer | Application developer | End user |
   | Popular providers | AWS EC2, Microsoft Azure Virtual Machines, Google Compute Engine, DigitalOcean | AWS Elastic Beanstalk, Google App Engine, Heroku, Microsoft Azure App Service | Salesforce, Microsoft Office 365, Google Workspace, Dropbox, Zoho, Slack |
   | Car analogy | You rent a car and drive it yourself | You hire a car with a driver | You take a taxi |

   Other services now named separately:
   - FaaS, Function as a Service, also called Serverless: we write and deploy just one function. We never think about servers at all. Example: AWS Lambda.
   - DaaS for Database or Desktop as a Service, STaaS for Storage as a Service, and NaaS for Network as a Service.

   Deployment models:
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
   | Search engine for a web server | SaaS | The user simply uses a finished search application over the Internet and manages nothing beneath it |
   | Google Docs | SaaS | A complete ready to use application accessed through the browser |
   | Microsoft Azure | IaaS, and also PaaS | Azure Virtual Machines provide raw infrastructure, which is IaaS; Azure App Service provides a managed runtime, which is PaaS |
   | Dropbox | SaaS | A finished file storage and sharing application; the user manages only the files |
   | Amazon Web Services (AWS) | IaaS, and also PaaS | EC2, S3 and VPC are IaaS; Elastic Beanstalk and Lambda are PaaS |

   - Simple rule: if the customer only uses a finished application, it is SaaS. If the customer puts its own code on a managed runtime, it is PaaS. If the customer manages the OS itself, it is IaaS.
   - Azure and AWS are whole platforms. They offer services in all three categories. So the correct answer is to name IaaS as the main category, and to mention that they also give PaaS and SaaS services.
10. **(c) What are the three types of services provided by the cloud?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888 (ET: N/A)]*


    Answer: The three types of services provided by the cloud are IaaS, PaaS and SaaS.

    - IaaS, Infrastructure as a Service: virtual machines, storage and networking, rented on demand. The customer manages the OS and everything above it. Examples: AWS EC2, Azure VM, Google Compute Engine.
    - PaaS, Platform as a Service: a ready runtime with the OS, middleware, database and development tools. The customer deploys only its own code. Examples: Heroku, Google App Engine, AWS Elastic Beanstalk.
    - SaaS, Software as a Service: a complete finished application, given over the Internet. The customer manages nothing but its own data. Examples: Gmail, Office 365, Salesforce, Dropbox.

    | Point | IaaS | PaaS | SaaS |
    |---|---|---|---|
    | What it provides | Virtualised computing resources over the internet: servers, storage and networking, on a rental basis | A ready to use platform for building, testing, deploying and managing applications | A fully working, ready to use software application, usually on subscription |
    | The user controls | The operating system, the applications and the data | Only the application code and the data | Nothing. Only the data and the settings |
    | The provider manages | The physical infrastructure: hardware, virtualisation, network, storage | Servers, storage and the whole runtime environment | Absolutely everything: infrastructure, updates, bug fixes and security |
    | How much the customer manages | The most | Less | The least |
    | Who it is for | System administrator, network engineer | Application developer | End user |
    | Popular providers | AWS EC2, Microsoft Azure Virtual Machines, Google Compute Engine, DigitalOcean | AWS Elastic Beanstalk, Google App Engine, Heroku, Microsoft Azure App Service | Salesforce, Microsoft Office 365, Google Workspace, Dropbox, Zoho, Slack |
    | Car analogy | You rent a car and drive it yourself | You hire a car with a driver | You take a taxi |
11. **Write the three basic function of cloud services?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*


    Answer: The three basic functions, that is the three service categories, of cloud services are:

    - Infrastructure as a Service, IaaS: it gives computing infrastructure on demand, that is virtual servers, storage and networking. The customer manages the OS and the applications. Examples: AWS EC2, Azure Virtual Machines.
    - Platform as a Service, PaaS: it gives a complete platform for development and deployment. The OS, runtime, database and tools are already there. The customer supplies only the application code. Examples: Heroku, Google App Engine.
    - Software as a Service, SaaS: it gives a finished application over the Internet, ready to use. There is nothing to install and nothing to maintain. Examples: Gmail, Office 365, Salesforce.

    - If we look at the basic functions instead of the models, every cloud service gives three things: computing power, storage and networking. All three are pooled, virtualised and metered.
12. **ক্লাউড কম্পিউটিং এর সুবিধা ও অসুবিধা লিখুন।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

    Answer:

    Advantages of cloud computing:
    - We need almost no money up front. The cost becomes a monthly running expense.
    - Scalability and elasticity: we can add or remove resources within minutes to match the demand. So a site survives a sudden traffic surge, and pays nothing extra when the traffic drops.
    - We can use it from anywhere. With an Internet connection, any device can reach the service. This helps remote working.
    - Reliability and disaster recovery: the provider copies the data across several availability zones and regions, and promises uptime of up to 99.9 percent in the SLA.
    - Updates and maintenance are automatic. Patching, hardware replacement and upgrades are all the provider's job.
    - Fast deployment: a server that once took weeks to buy and set up now runs in minutes.
    - Teamwork: many users can work on the same document or dataset at the same time.
    - We get advanced services like machine learning, big data analytics and content delivery networks. A small organisation could never build these on its own.

    Disadvantages of cloud computing:
    - It depends fully on the Internet. If the connection fails, nothing works. Where bandwidth is costly or unreliable, this is a serious problem.
    - Security and privacy: the data sits on someone else's hardware. So privacy depends on the provider's controls, and on the customer setting up the service correctly.
    - Data sovereignty and law: many countries require certain data to stay inside the country. In Bangladesh, the rules for banking data say this.
    - Less control and less customisation, especially in SaaS, where we cannot change how the software behaves.
    - Vendor lock-in: the provider's own special services, plus data transfer charges, make it hard and costly to move to another provider later.
    - Long term cost: if the workload is steady and predictable, buying our own hardware may be cheaper after a few years.
    - Downtime risk: one outage at the provider hits every customer at the same time, and the customer can only wait.
    - Hidden charges, especially for data going out of the cloud. We also need staff with new skills.

## Cloud Storage & Fundamentals (6)

1. What is cloud computing? Why is it used? State the difference between cloud storage and traditional storage. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer:

   What cloud computing is:

   - Cloud computing means we get computing services over the Internet and pay only for what we use. These services are servers, storage, databases, networking, software and analytics. We do not buy or run the physical hardware ourselves.
   - NIST lists five key features: on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Why it is used:
   - To avoid the big up front cost and the long wait of buying and installing physical servers.
   - To raise or lower capacity quickly as demand changes, and pay only for what we use.
   - To reach our data and applications from anywhere, on any device.
   - To get reliability, backup and disaster recovery that one organisation could never afford to build alone.
   - To hand patching, hardware maintenance and upgrades to the provider. Then our own team can work on the business instead.
   - To use advanced services like analytics and machine learning, without building the infrastructure for them.

   Cloud storage vs traditional storage:

   | Point | Cloud storage | Traditional, that is local or on-premises storage |
   |---|---|---|
   | Where the data is | On the provider's servers, reached over the Internet | On our own disks, servers, NAS or SAN |
   | Cost model | Running cost, pay per GB per month | Up front cost, we buy the hardware once |
   | Capacity | Almost unlimited, grows instantly | Fixed by the hardware we bought. To grow, we must buy more |
   | Access | From anywhere with an Internet connection | Normally only from within the local network |
   | Maintenance | Fully done by the provider | Our own job |
   | Backup and redundancy | Already built in, copied across zones and regions | We must plan, buy and run it ourselves |
   | Speed | Limited by the Internet line | Very fast, limited only by the local bus or LAN |
   | Availability without network | None | Full |
   | Security and control | Shared responsibility. The data sits on someone else's hardware | Full physical and logical control |
   | Examples | Amazon S3, Google Drive, Dropbox, Azure Blob Storage | Internal hard disk, USB drive, NAS, SAN, tape library |
2. **What is Cloud Computing? What are its characteristics? Briefly describe the types of cloud computing.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer:

   What cloud computing is:

   - Cloud computing means we get computing services over the Internet and pay only for what we use. These services are servers, storage, databases, networking, software and analytics. We do not buy or run the physical hardware ourselves.
   - NIST lists five key features: on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Essential characteristics, as defined by NIST:
   - On demand self service: the user takes computing resources automatically, through a portal or an API. No person from the provider is involved.
   - Broad network access: the service is available over the network. Any normal device can reach it, whether a phone, a tablet or a desktop.
   - Resource pooling: the provider puts its resources into one pool and serves many customers from it, using a multi-tenant model. Resources are given and taken back as the demand changes.
   - Rapid elasticity: we can add or remove capacity quickly. To the customer, the resources look unlimited.
   - Measured service: usage is metered and billed. So the customer pays only for what it uses, and both sides can see exactly what was used.

   Other practical features: virtualisation, high availability, automation, self healing, and servers spread across the world.

   Deployment types:
   - Public cloud: a third party provider owns, manages and maintains the whole infrastructure, and delivers it over the internet to the general public. Many customers share the same resources.
     - Advantages: minimal investment, because it works on a pay per use model with no big up front cost. Zero setup and maintenance, because the provider handles all the hardware. Dynamic scalability, because the resources are almost unlimited and scale instantly.
     - Disadvantages: lower security, because the resources are shared publicly, so meeting strict compliance rules is hard. Low customisation, because the environment is standardised.
     - Examples: AWS, Azure, Google Cloud.
   - Private cloud: a one to one environment for a single customer. We do not share the hardware with anyone else. It sits behind strong firewalls, under the organisation's own IT department.
     - Advantages: total control over IT operations, service integration and user behaviour. Elite security and privacy, so it suits sensitive corporate data. It supports legacy applications, because it is highly customisable.
     - Disadvantages: high cost, because of the dedicated hardware and internal IT staff. Limited scalability, because we are bound by the physical hardware we bought.
   - Hybrid cloud: it bridges the public and the private worlds through a layer of software. We can move applications and data between the two as needed.
     - Advantages: ultimate flexibility, because we keep sensitive data safe on the private cloud and run heavy, non-sensitive work on the public cloud. Cost efficiency, because we pay for extra public capacity only during traffic spikes. This is called cloud bursting. Targeted security, because the most critical data stays fully isolated.
     - Disadvantages: hard to manage, because it combines two different clouds, so it is complex. Slow data transmission, because data moves through the public cloud, which adds latency.
     - Most banks use this model.
   - Community cloud: a shared infrastructure used by a specific group of organisations from a similar industry, who have the same concerns, such as compliance or security rules. It may be managed internally or by a third party.
     - Advantages: cost effective, because several organisations share it. Better security than a public cloud. Shared resources and infrastructure. Good for collaboration and data sharing.
     - Disadvantages: less scalable, because many organisations share the same resources. Rigid in customisation, because a change requested by one organisation affects the others.
     - Example: a group of government offices, or a group of hospitals.

   Service types: IaaS, PaaS and SaaS, and now also FaaS or serverless.
3. **Explain cloud computing and evaluate its advantages and disadvantages.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer:

   - Cloud computing means we get computing services over the Internet and pay only for what we use. These services are servers, storage, databases, networking, software and analytics. We do not buy or run the physical hardware ourselves.
   - NIST lists five key features: on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Advantages:
   - Low starting cost: we spend nothing up front on servers, data centre space, cooling or power. The cost becomes a monthly running expense.
   - Scalability and elasticity: we can add or remove resources within minutes to match the demand. So a sudden peak is survivable, and quiet periods cost nothing extra.
   - Accessibility: we can reach it from anywhere with an Internet connection, on any device. This helps remote and spread out teams.
   - Reliability and disaster recovery: providers copy the data across availability zones and regions, and promise 99.9 percent uptime or better in the SLA.
   - Automatic updates and maintenance: patching, hardware replacement and upgrades are all the provider's job.
   - Fast deployment: a server that once took weeks to buy now runs in minutes.
   - Teamwork: many users can work on the same document or dataset at the same time.
   - We get advanced services like machine learning, big data analytics and content delivery networks. A small organisation could never build these itself.

   Disadvantages:
   - It depends on the Internet. If the connection fails, nothing works. Where bandwidth is costly or unreliable, this is a real problem.
   - Security and privacy worries: the data sits on someone else's hardware. So privacy depends on the provider's controls, and on the customer setting things up correctly.
   - Data sovereignty and law: many countries require certain data to stay inside the country. Bangladesh does this for banking data.
   - Less control and less customisation, especially in SaaS, where the customer cannot change how the software behaves.
   - Vendor lock-in: the provider's own special services, plus data transfer charges, make it costly and hard to move later.
   - Long term cost: if a workload runs steadily all the time, buying our own hardware can be cheaper over a few years.
   - Downtime risk: one outage at the provider hits every customer at once, and the customer can only wait.
   - Hidden charges, especially for data going out of the cloud. We also need staff with new skills.

   - Which to choose: for a startup, or for any workload whose demand goes up and down, the advantages clearly win. Owning hardware would cost too much and take too long. But for a large organisation with a steady workload and strict data residency rules, such as a central bank, a private or hybrid cloud is better. It keeps the regulated data in-house, and uses the public cloud for the elastic, non-sensitive work.
4. **(খ) Cloud computing কী? উহার বৈশিষ্ট্য ও সুবিধা বর্ণনা করুন ।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 616 (ET: N/A)]*

   Answer:

   What cloud computing is:
   - Cloud computing means we rent computing services over the Internet, on demand. These are servers, storage, databases, networking, software and analytics. We do not buy and run our own physical hardware.
   - We pay only for what we actually use. That is why it is called a pay as you go model.

   Characteristics:
   - On demand self service: the user gets resources through a portal or an API, with no help from the provider's staff.
   - Broad network access: any normal device can reach the service over the network.
   - Resource pooling: the provider keeps its resources in one pool, in a multi-tenant model, and moves them around as demand changes.
   - Rapid elasticity: we can raise or lower capacity within minutes. To the customer, the resources look unlimited.
   - Measured service: usage is metered and billed by that meter. So both sides can see exactly what was used.
   - Also: virtualisation, high availability, automation, and servers spread across regions.

   Advantages:
   - We need almost no money up front. The cost becomes a monthly running expense.
   - We can raise or lower resources within minutes, as the demand changes.
   - We can use the service from anywhere, on any device.
   - The provider copies the data across several regions. So backup and disaster recovery come built in.
   - Patching, upgrades and hardware maintenance are all the provider's job.
   - Deployment is fast. A server runs within minutes.
   - Many users can work on one file at the same time.
   - Advanced services like machine learning and big data analytics are ready to use.

   Disadvantages, which should also be mentioned in the answer:
   - It depends fully on the Internet. There are worries about security and data sovereignty. We get less control, we face vendor lock-in, and the total cost can be higher in the long run.
5. **What is Cloud Computing? Write its adventages and Disadventages?** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*


   Answer:

   - Cloud computing means we get computing services over the Internet and pay only for what we use. These services are servers, storage, databases, networking, software and analytics. We do not buy or run the physical hardware ourselves.
   - NIST lists five key features: on demand self service, broad network access, resource pooling, rapid elasticity and measured service.

   Advantages:
   - Low starting cost: we spend nothing up front on servers, data centre space, cooling or power. The cost becomes a monthly running expense.
   - Scalability and elasticity: we can add or remove resources within minutes to match the demand. So a sudden peak is survivable, and quiet periods cost nothing extra.
   - Accessibility: we can reach it from anywhere with an Internet connection, on any device. This helps remote and spread out teams.
   - Reliability and disaster recovery: providers copy the data across availability zones and regions, and promise 99.9 percent uptime or better in the SLA.
   - Automatic updates and maintenance: patching, hardware replacement and upgrades are all the provider's job.
   - Fast deployment: a server that once took weeks to buy now runs in minutes.
   - Teamwork: many users can work on the same document or dataset at the same time.
   - We get advanced services like machine learning, big data analytics and content delivery networks. A small organisation could never build these itself.

   Disadvantages:
   - It depends on the Internet. If the connection fails, nothing works. Where bandwidth is costly or unreliable, this is a real problem.
   - Security and privacy worries: the data sits on someone else's hardware. So privacy depends on the provider's controls, and on the customer setting things up correctly.
   - Data sovereignty and law: many countries require certain data to stay inside the country. Bangladesh does this for banking data.
   - Less control and less customisation, especially in SaaS, where the customer cannot change how the software behaves.
   - Vendor lock-in: the provider's own special services, plus data transfer charges, make it costly and hard to move later.
   - Long term cost: if a workload runs steadily all the time, buying our own hardware can be cheaper over a few years.
   - Downtime risk: one outage at the provider hits every customer at once, and the customer can only wait.
   - Hidden charges, especially for data going out of the cloud. We also need staff with new skills.
6. **Describe the cloud base database briefly.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*


   Answer: A cloud based database is a database that runs on cloud infrastructure, and we reach it over the Internet. The provider looks after the servers and the storage. In the managed form, the provider also looks after the database software itself.

   Two forms:
   - Self managed on IaaS: the customer installs MySQL, PostgreSQL or Oracle on a cloud virtual machine and runs it. This gives full control, but patching, backup and scaling stay the customer's work.
   - Managed database as a service, DBaaS: the provider runs the database engine too. It handles setup, patching, backup, replication, failover and scaling. Examples: Amazon RDS and Aurora, Azure SQL Database, Google Cloud SQL, MongoDB Atlas, Amazon DynamoDB, Firebase.

   Characteristics:
   - Elastic scaling: we can raise storage and compute with just a setting change. We can also add read replicas to spread the query load.
   - High availability: the data is copied automatically to a standby in another availability zone, and failover happens in seconds.
   - Automatic backup and point in time recovery. We can normally go back to any second within a window of days or weeks.
   - We pay per use, based on instance size, storage and I/O.
   - Security: the data is encrypted at rest and while moving. There is IAM based access control, VPC isolation and audit logging.
   - Both relational and NoSQL engines are offered. There are also data warehouse services like Amazon Redshift, Google BigQuery and Snowflake.

   Advantages:
   - No hardware to buy or maintain. We do not need a database administrator for the routine work.
   - Fast setup, in minutes instead of weeks.
   - Redundancy and disaster recovery across regions come built in.
   - Global reach, because we can put replicas near the users.
   - The cost follows the usage. So a small application pays very little.

   Disadvantages:
   - Delay depends on the network link. An application that talks a lot, and sits far from the region, will be slow.
   - Less control: we may not be allowed superuser access, custom extensions or OS level tuning.
   - Vendor lock-in, especially with the provider's own engines like Aurora or DynamoDB. Charges for data going out also make migration costly.
   - Compliance and data residency limits. These matter a lot for banking and government data in Bangladesh.
   - At large scale the cost can rise sharply, and in ways we did not expect.

## Virtualization & Containers (VM vs Container) (6)

1. VM vs Container in Submarine Cable Network: [BSCCPL AME 21-08-2026 (BUET)] A national submarine cable landing station provides international connectivity to several organizations. The organization wants to deploy DNS, Web, Database, Monitoring, and Network Management services on a shared physical server. The network administrator is considering two approaches:
Approach A: Deploy each service in a separate Virtual Machine.
Approach B: Deploy each service in a separate Container.
A submarine cable connects Bangladesh to an international data center. At the cable landing station, a server hosts 4 VMs, while another server runs 4 containers. Which one and why? [BSCCPL AME 21-08-2026 (BUET)]


   Answer:

   The two approaches compared:

   Definitions:
   - A virtual machine is software that lets us install other software inside it, and control it virtually. A hypervisor sits between the hardware and the VM.
   - A container lets the different parts of an application run independently. It runs on top of a host operating system, and does not need its own operating system.
   - Hypervisor: it sits between the hardware and the VMs, and shares out the physical resources among them. Examples: KVM, Xen and VMware are Type 1; VirtualBox is Type 2.
   - Container engine: it manages containers that all share one host operating system. Examples: Docker, RancherOS, PhotonOS.

   | Aspect | Approach A, Virtual Machines | Approach B, Containers |
   |---|---|---|
   | Core function | Installs software inside an isolated software environment | Lets the parts of an application run independently |
   | Operating system | Each VM runs its own guest OS | All containers share one host OS |
   | Virtualisation type | Hardware virtualisation | OS or software virtualisation |
   | Size | Large, in gigabytes | Light, in hundreds of megabytes |
   | Startup time | Longer, in minutes | Much faster, in seconds |
   | Memory usage | Uses a lot of system memory | Needs very little memory |
   | Security | More secure, because there is no shared underlying kernel | Less secure, because it is software based with shared memory |
   | Different operating systems | Yes. Windows and Linux can run side by side | No. All containers share the host kernel |
   | Agility and portability | Lower | Higher |
   | Use case | When an application needs all the OS resources | When we want to fit the most applications onto the fewest servers |
   | Typical tools | VMware vSphere, KVM, Hyper-V | Docker, Kubernetes, Podman |

   Which one and why, for a submarine cable landing station:
   - The recommendation is a hybrid, and if a single choice is demanded it is Virtual Machines for this specific environment.
   - Reason 1, criticality and isolation: a cable landing station carries the international connectivity of a whole country. DNS and network management are the most security sensitive services on the site. A VM is more secure, because it does not share the underlying kernel with the others. A container is less secure, because it is software based and shares memory. So a break-in through the web service cannot reach the DNS or the network management system if we use VMs.
   - Reason 2, regulatory and audit requirements: national critical infrastructure is normally required to demonstrate strong workload separation, and VMs satisfy an auditor more readily than containers on a shared kernel.
   - Reason 3, mixed operating systems: network management and monitoring products in this sector often come as appliances, or as Windows software. A VM can run its own guest OS, so Windows and Linux can sit side by side. Containers share the host kernel, so they cannot do this.
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
   - All the processing, the storage and the control reside on a single central computer or server, and users connect to it through terminals or clients.
   - Characteristics: the data and the control are in one place, so administration and backup are simple, but that single machine is also a single point of failure.
   - Examples: the old mainframe systems, all the terminals of a bank branch connected to one central server, and a single file server in an office.

   Distributed computing:
   - Many independent computers, joined by a network, work together on a task that would be hard for one machine alone. To the user the whole thing looks like one system. The work and the data are divided among many nodes.
   - Architecture: decentralised control, unlike the client-server model of a centralised system.
   - Advantages: there is no single point of failure, we can scale horizontally, resources are used well, and tasks can run in parallel.
   - Disadvantages: synchronisation and consistency become hard, network delay appears, and the system gets complex.
   - Examples: the Internet itself, Google's search infrastructure, Hadoop and Spark clusters, blockchain, and DNS.

   | Point | Centralized | Distributed |
   |---|---|---|
   | Processing | In one place | Divided among many nodes |
   | Failure | Single point of failure | Fault tolerant |
   | Scalability | Vertical, that is buying a bigger machine | Horizontal, that is adding more nodes |
   | Cost | A large machine is expensive up front | Many ordinary machines, so cheaper |
   | Management | Simple | Complex, synchronisation is required |
   | Latency | Low, everything is in one place | Possibly higher, since it depends on the network |
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

   Grid computing in more detail:
   - Definition: a network of computers working together on a task that would be difficult for a single machine.
   - Architecture: a distributed model with decentralised control. It is application oriented, and it uses grid middleware.
   - Advantages: high resource utilisation, parallel task processing, and a scalable design. There is usually no usage fee, because members share their spare capacity.
   - Disadvantages: the software is often immature, it adds complexity, it has limited flexibility, and it carries security risks.

   How grid computing differs from cloud computing:

   | Point | Grid computing | Cloud computing |
   |---|---|---|
   | Architecture | Distributed, decentralised control | Client-server, centralised control |
   | Orientation | Application oriented | Service oriented |
   | Payment | Usually no usage fee | The user pays for what is used |
   | Accessibility | Lower | High, through standard web protocols |
   | Resource pattern | Collaborative, members share spare capacity | Pooled resources rented from a provider |
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

   What edge computing is:
   - Edge computing is a computing model in which data is processed close to where it is produced, instead of being sent to a distant central cloud data centre.
   - The edge means the outer boundary of the network, that is the sensors, cameras and IoT devices themselves, or a small server or gateway near them.

   How it works:
   - The device or the edge server collects the data locally, filters it, analyses it and takes a decision immediately.
   - Only the important or summarised results are sent to the cloud, for long term storage and larger scale analysis.

   Why it is needed:
   - Low latency: a round trip to the cloud takes 50 to 200 ms, which is far too long for a self driving car, an industrial robot or real time video analytics. At the edge the answer comes back within a few milliseconds.
   - Saving bandwidth: sending the raw video of hundreds of HD cameras to the cloud is impossible and very expensive, so the edge processes it and sends only the events.
   - Reliability: even when the Internet link fails, the local system keeps working and synchronises later.
   - Privacy and law: patient records or facial images can be processed locally and kept inside the country.
   - Real time safety decisions, such as stopping a machine when a person enters a dangerous area, cannot depend on a network link at all.

   Examples:
   - CDN edge servers, Multi-access Edge Computing in 5G, local controllers in a smart factory, traffic cameras in a smart city, and local health analysis on a smartwatch.

   Relationship with fog computing:
   - Fog computing is an intermediate layer between the edge and the cloud, where the processing happens at the gateway or router level. The edge is closest, the fog is in between, and the cloud is furthest away.

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
