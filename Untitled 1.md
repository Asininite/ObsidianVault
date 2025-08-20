## On-premise 
	Complete control over the tech stack
Local speed and performance
Governance and regulatory compliance

## Cloud data warehouses provide:

	On-demand scalability
Cost efficiency
Bundled capabilities such as IAM and analytics
Security
System uptime and availability

### On-premises data warehouses
On-premises data warehousing uses a three-tier architecture, generally referred to simply as bottom, middle, and top tiers.

Bottom tier – storage layer
This is the data warehouse itself. It includes the database server, the storage media, a meta repository, and data marts.

Middle tier – compute layer
This is the online analytical processing (OLAP) server. It processes the complex queries to present results in a form suitable for data mining, analytics, and business intelligence.

Top tier – services layer
This is the user front end: the actual data mining, analytics, and BI tools.

On-premises: benefits
Benefits of on-premises data warehouses include control, speed, security, governance, and availability.

#### Control

An organization has complete control of what hardware and software to use, where it sits, and who has access to it with an on-premises deployment. The hardware could be the same kind of commodity servers and storage devices used for other applications, or purpose-built servers.

In the event of a failure, an IT team has physical access to the hardware and access to every layer of software to facilitate troubleshooting. They can see indicator lights, cycle power, or replace hardware as required. They don't have to rely on third parties to get the system back up and running.

#### Speed

Locating all hardware and tools on premises alleviates concerns over network latency, although some data sources may be off-site, accessible only over the net. Keep in mind, though, that other factors may impact performance more than network latency. This is especially true if your on-prem solution is not sized properly.

#### Governance

Data governance and regulatory compliance often are easier to achieve using an on-premises data warehouse. For example, many organizations struggle to meet General Data Protection Regulation (GDPR) requirements concerning the ability to identify data location. You know exactly where your data is located with an on-prem data warehouse.

#### On-premises: challenges
An on-premises data warehouse provides total control — and total responsibility. Database administrators and analysts, systems administrators, systems engineers, network engineers, and security specialists must design, procure, and install on-premises systems. They must handle moves, adds, and changes — all administration and maintenance of hardware and software. They have full responsibility to ensure that the underlying infrastructure stays up and running efficiently, reliably, and securely.

Additionally, an on-premises data warehouse cannot accommodate bursts of activity that require more compute or memory. An organization must purchase "up," sizing its data warehouse to handle peak load, even if that level of usage occurs only intermittently. And scaling up to meet changing needs may require replacing systems that cannot meet new demands.


## Cloud data warehouses
Many organizations that currently use on-premises data warehouses are choosing to migrate the data to cloud data warehouses. Sometimes, they choose a hybrid solution that includes both on-premises and cloud data warehouses.

Let's look at a few popular cloud data warehouses:

#### Amazon Redshift
Amazon Redshift's approach might be described as platform-as-a-service (PaaS). Redshift is highly scalable, provisioning clusters of nodes to customers as their storage and computing needs evolve. Each node has individual CPU, RAM, and storage space.

To set up Redshift, one must provision the clusters through Amazon Web Services (AWS). As of March 2019, Redshift has concurrency scaling that lets users automatically add clusters in times of high demand.

#### Google BigQuery
Perhaps the best thing about BigQuery's architecture is that you don't need to know anything about it. BigQuery is serverless, so the underlying architecture is hidden — in a good way — from users. BigQuery can scale to thousands of machines by structuring computations as an execution tree. It sends queries through a root server, intermediate servers, and ultimately leaf servers with local storage.

#### Snowflake
Snowflake separates storage, compute, and services into separate layers, allowing them to scale independently. The automatically managed storage layer can contain structured or semistructured data. The compute layer is composed of clusters, each of which can access all data but work independently and concurrently to enable automatic scaling, distribution, and rebalancing. Snowflake is a data warehouse-as-a-service, and operates across multiple clouds, including AWS, Microsoft Azure, and, soon, Google Cloud.

#### Microsoft Azure SQL Data Warehouse
Azure SQL Data Warehouse is an elastic, large-scale data warehouse platform-as-a-service that leverages the broad ecosystem of SQL Server. Like other cloud storage and computing platforms, it uses a distributed MPP architecture and columnar data store. It gathers data from databases and SaaS platforms into one powerful, fully-managed centralized repository. Storage and compute are billed separately, so they can scale independently.


 

### Cloud data warehouse: benefits
Cloud data warehouses provide the same benefits that drive organizations to migrate other applications to the cloud. According to NIST's definition of cloud computing, "Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction." Benefits of a cloud data warehouse include scalability, cost, security, availability, and time to market.

#### Scalability

With a cloud data warehouse, capacity isn't an issue, so data can flow seamlessly at peak and slow times.

#### Cost

With a cloud data warehouse, there are no physical servers to buy or set up. Businesses pay only for the storage and CPU time they need. This pay-as-you-go pricing means no capital expenditures for idle resources to handle peaks in demand. Additionally, the cloud provider handles ongoing maintenance, administration, and updates.

#### Built-in ecosystem

The top-tier data warehouses can leverage other cloud services on their platforms, such as identity and access management services and data analytics tools.

#### Security

Security often is cited as a concern when migrating to the cloud — but it's also mentioned as a benefit. Cloud service providers invest heavily in physical and logical security controls. Few organizations are capable of investing more in security than Amazon, Google, or Microsoft. They also ensure the tightest security controls with certifications such as ISO 27001 and SOC 2. Odds are that an organization's security posture is better with a cloud data warehouse than an on-premises solution.

#### Availability

Availability and reliability is another area in which cloud service providers invest heavily. A service level of 99.9% availability is common among cloud data warehouses. The ability to have data replicated across different regions and zones within the cloud environment makes your data highly available, even in the event of a failure.

#### Time to market

All of these benefits of cloud data warehouses lead to another — time to market. Cloud computing leads to faster deployment, scaling, analytics, and access to business intelligence. That means faster time to insight and, ultimately, faster time to market.

Cloud data warehouse: challenges
The challenges that come with a cloud data warehouse include data integration, provider lock-in, security, and, possibly, latency.

Ingesting data into a cloud data warehouse is not a trivial task. It typically requires writing ETL code, which consumes time and expensive resources, and the introduction of any new data source requires more coding. However, third-party ETL tools make this task faster and easier.

Once you select a cloud data warehouse provider, changing to a different platform can be a difficult process, involving technical challenges and contractual issues.

Data latency, the time it takes to store or retrieve data, may be a challenge, depending on your performance requirements. If data that is an hour old meets your requirements, then latency is less of a challenge than if you need data that is less than a minute old. Several factors contribute to latency, such as the location of data sources, quantity of data, and type of data. The best way to assess the impact of latency is to do testing in as close to a production environment as possible. Some cloud data warehouse services have free trials that you can use for testing purposes.