# 1. Introduction

Upward Health, LLC ("Upward Health") is committed to ensuring the confidentiality, privacy, integrity, and availability of all electronic protected health information (ePHI) it receives, maintains, processes and/or transmits on behalf of its Customers. As providers of compliant, hosted infrastructure used by health technology vendors, developers, designers, agencies, custom development shops, and enterprises, Upward Health strives to maintain compliance, proactively address information security, mitigate risk for its Customers, and assure known breaches are completely and effectively communicated in a timely manner. The following documents address core policies used by Upward Health to maintain compliance and assure the proper protections of infrastructure used to store, process, and transmit ePHI for Upward Health Customers.

Upward Health provides secure and compliant cloud-based software. This hosted software falls into two broad categories: 1) **Platform as a Service (PaaS)** and 2) **Platform Add-ons**. These Categories are cited throughout policies as Customers in each category inherit different policies, procedures, and obligations from Upward Health.

## 1.1 Platform as a Service (PaaS)

PaaS Customers utilize hosted software and infrastructure from Upward Health to deploy, host, and scale custom developed applications and configured databases. These customers are deployed into compliant containers run on systems secured and managed by Upward Health. Upward Health does not have insight or access into application level data of PaaS Customers and, as such, does not have the ability to secure or manage risk associated with application level vulnerabilities and security weaknesses. Upward Health makes every effort to reduce the risk of unauthorized disclosure, access, and/or breach of PaaS Customer data through network (firewalls, dedicated IP spaces, etc) and server settings (encryption at rest and in transit, OSSEC throughout the Platform, etc).

## 1.2 Compliance Inheritance

Upward Health provides compliant hosted software infrastructure for its Customers. Upward Health has been through a HIPAA compliance audit by a national third-party compliance firm to validate and map organizational policies and technical controls to HIPAA rules. Upward Health's company policies, procedures, and technologies are HITRUST Certified. Upward Health's service offerings are available on AWS, Azure, Rackspace, and SoftLayer; current production systems on these platforms are included in Upward Health's third-party audits and HITRUST certification.

Upward Health signs business associate agreements (BAAs) with its Customers. These BAAs outline Upward Health obligations and Customer obligations, as well as liability in the case of a breach. In providing infrastructure and managing security configurations that are a part of the technology requirements that exist in HIPAA and HITRUST, as well as future compliance frameworks, Upward Health manages various aspects of compliance for Customers. The aspects of compliance that Upward Health manages for Customers are inherited by Customers, and Upward Health assumes the risk associated with those aspects of compliance. In doing so, Upward Health helps Customers achieve and maintain compliance, as well as mitigates Customers' risk.

Upward Health does not act as a covered entity. When Upward Health does operate as a business associate (not a subcontractor), Upward Health does not interface with users to obtain or provide access to ePHI. Access to ePHI is through our customers' applications.

Certain aspects of compliance cannot be inherited. Because of this, Upward Health Customers, in order to achieve full compliance or HITRUST Certification, must implement certain organizational policies. These policies and aspects of compliance fall outside of the services and obligations of Upward Health.

Mappings of HIPAA Rules to Upward Health controls and a mapping of what Rules are inherited by Customers, both Platform Customers and Add-on Customers, are covered in [§2](#2.-hipaa-inheritance).

## 1.3 Upward Health Organizational Concepts

The physical infrastructure environment is hosted at [Rackspace](https://www.rackspace.com/), [Amazon Web Services](https://aws.amazon.com/) (AWS), [Microsoft Azure](https://azure.microsoft.com/), and [IBM SoftLayer](http://www.softlayer.com/). The network components and supporting network infrastructure are contained within the Rackspace, AWS, Azure, and SoftLayer infrastructures and managed by Rackspace, AWS, Microsoft, and IBM (respectively). Upward Health does not have physical access into the network components. The Upward Health environment consists of Cisco firewalls; nginx web servers; Java, Python, and Go application servers; Percona and PostgreSQL database servers; Logstash logging servers; Linux Ubuntu monitoring servers; Windows Server virtual machines; Chef and Salt configuration management servers; OSSEC IDS services; Docker containers; and developer tool servers running on Linux Ubuntu.

Within the Upward Health Platform on Rackspace, AWS, Azure, and SoftLayer, all data transmission is encrypted and all hard drives are encrypted so data at rest is also encrypted; this applies to all servers - those hosting Docker containers, databases, APIs, log servers, etc. Upward Health assumes all data *may* contain ePHI, even though our Risk Assessment does not indicate this is the case, and provides appropriate protections based on that assumption.

In the case of PaaS Customers, it is the responsibility of the Customer to restrict, secure, and assure the privacy of all ePHI data at the Application Level, as this is not under the control or purview of Upward Health.

The data and network segmentation mechanism differs depending on the primitives offered by the underlying cloud provider infrastructure:

* Within Rackspace, hosted load balancers segment data and traffic while Cisco firewalls route traffic to private subnets for PaaS Customers and for Platform Add-ons.
* Within AWS, hosted load balancers segment data across dedicated Virtual Private Clouds for PaaS Customers and for Platform Add-ons.
* Within Azure, hosted load balancers segment data across dedicated Virtual Networks for PaaS Customers and for Platform Add-ons.
* Within SoftLayer, hosted load balancers segment data across dedicated Private Networks for PaaS Customers and for Platform Add-ons.

The segmentation strategies employed by Upward Health effectively create RFC 1918, or dedicated, private segmented and separated networks and IP spaces, for each PaaS Customer and for Platform Add-ons.

Additionally, IPtables is used on each server for logical segmentation. IPtables is configured to restrict access to only justified ports and protocols. Upward Health has implemented strict logical access controls so that only authorized personnel are given access to the internal management servers. The environment is configured so that data is transmitted from the load balancers to the application servers over a TLS encrypted session.

In the case of Platform Add-ons, once the data is received from the application server, a series of Application Programming Interface (API) calls is made to the database servers where the ePHI resides. The ePHI is separated into PostgreSQL and Percona databases through programming logic built so that access to one database server will not present you with the full ePHI spectrum.

The VPN server, nginx web server, and application servers are externally facing and accessible via the Internet. The database servers, where the ePHI resides, are located on the internal Upward Health network and can only be accessed through a bastion host over a VPN connection. Access to the internal database is restricted to a limited number of personnel and strictly controlled to only those personnel with a business-justified reason. Remote access to internal servers is not accessible except through load balancers.

All Platform Add-ons and operating systems are tested end-to-end for usability, security, and impact prior to deployment to production.

## 1.4 Requesting Audit and Compliance Reports

Upward Health, at its sole discretion, shares audit reports, including its HITRUST reports and Corrective Action Plans (CAPs), with customers on a case by case basis. All audit reports are shared under explicit NDA in Upward Health format between Upward Health and party to receive materials. Audit reports can be requested by Upward Health workforce members for Customers or directly by Upward Health Customers.

The following process is used to request audit reports:

1. Email is sent to compliance-reports@datica.com. In the email, please specify the type of report being requested and any required timelines for the report.
2. Upward Health staff will log an issue with the details of the request into the Upward Health Quality Management System. The Upward Health Quality Management System is used to track requests' status and outcomes.
3. Upward Health will confirm if a current NDA is in place with the party requesting the audit report. If there is no NDA in place, Upward Health will send one for execution.
4. Once it has been confirmed that an NDA is executed, Upward Health staff will move the issue to "Under Review".
5. The Upward Health Security Officer or Privacy Officer must Approve or Reject the Issue. If the Issue is rejected, Upward Health will notify the requesting party that we cannot share the requested report.
6. If the issue has been Approved, Upward Health will send the customer the requested audit report and complete the Quality Management System issue for the request.

## 1.5 Version Control

Refer to the GitHub repository at [https://github.com/catalyzeio/policies/](https://github.com/catalyzeio/policies/) for the full version history of these policies.
