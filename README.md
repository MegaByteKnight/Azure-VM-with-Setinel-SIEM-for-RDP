Building a Security Operations Center (SOC) with Azure and Microsoft Sentinel
--------
Overview
--------

Hey there! In this project, I decided to dive into the world of cybersecurity by building my very own **Security Operations Center (SOC)** using **Microsoft Azure** and **Microsoft Sentinel**. The idea was to create a lab environment where I could monitor and generate alerts for security events across devices—kind of like setting up a mini business network. Plus, I wanted to set up a threat intelligence feed to keep tabs on common and new indicators of compromise (IOCs), all while keeping costs to a minimum.

What I Did
----------

*   **Deployed a Windows Virtual Machine (VM) in Azure** with Remote Desktop Protocol (RDP) access.
    
*   **Set up Microsoft Sentinel** to collect and analyze security events from the VM.
    
*   **Connected logs from the VM to Sentinel** using data connectors.
    
*   **Created analytics rules and alerts** to monitor successful and failed RDP login attempts.
    
*   **Simulated security risks** by leaving RDP open to the internet and observing unauthorized access attempts.
    
*   **Planned to integrate a threat intelligence feed** to enhance detection capabilities.
    

The Lab Setup
-------------

*   **Cloud Platform**: Microsoft Azure (used the free trial with $200 credit)
    
*   **SIEM Solution**: Microsoft Sentinel
    
*   **Tools Used**: Azure, Microsoft Sentinel, Log Analytics Workspace
    

How It Went Down
----------------

### 1\. Getting Started with Azure

First off, I signed up for a free Azure account. This gave me access to all the Azure services I needed.

### 2\. Spinning Up the Virtual Machine

I created a resource group called SOC-Lab-Group to keep everything organized. Then, I deployed a Windows 10 Pro VM named SOC-VM in the East US region. I kept most of the default settings to keep things simple. For the admin account, I went with AdminUser and a secure password.

**Networking Note**: I allowed inbound RDP traffic on port 3389 so I could access the VM remotely. This is crucial for RDP access but does come with security considerations.

### 3\. Setting Up Microsoft Sentinel

Next up, I created a Log Analytics Workspace called SOC-Workspace in the same resource group and region. Then, I added Microsoft Sentinel to the workspace to get my SIEM capabilities rolling.

### 4\. Connecting the VM to Sentinel

To get logs from my VM into Sentinel, I installed the Azure Monitor Agent on the VM. I set up a Data Collection Rule (DCR) to specify that I wanted to collect all security events.

### 5\. Creating Alerts and Analytics Rules

In Microsoft Sentinel, I set up custom analytics rules to keep an eye on RDP login attempts:

*   **Failed RDP Login Attempts**:
    
    *   Monitored for Event ID 4625 (failed login attempts).
        
    *   Set up alerts to trigger when there were multiple failed attempts.
        
*   **Successful RDP Login Attempts**:
    
    *   Monitored for Event ID 4624 (successful logins).
        
    *   Alerted on any successful login to detect potential unauthorized access.
        

I configured incidents to be created automatically from these alerts and set appropriate severity levels.

### 6\. Simulating Security Events

To put my setup to the test, I intentionally left the RDP port open to the internet. I then performed both successful and failed RDP login attempts. Interestingly, I started seeing unauthorized login attempts from external IP addresses—proof that bots and bad actors are always scanning for open ports.

### 7\. Monitoring and Analysis

I used the dashboards in Microsoft Sentinel to visualize security events and trends over time. It was fascinating to see real-time alerts and incidents popping up. I dug into the security logs to investigate the sources of failed login attempts and spotted some suspicious patterns.

What I Learned
--------------

*   **SIEM Deployment**: Setting up a SIEM in a cloud environment was an awesome learning experience. Microsoft Sentinel is powerful yet user-friendly.
    
*   **Importance of Monitoring**: This project underscored how critical continuous monitoring and alerting are in cybersecurity.
    
*   **Cloud Resource Management**: I learned to manage cloud resources efficiently to stay within the free trial credits.
    

Challenges Faced
----------------

*   **Resource Limits**: I had to be mindful of Azure's resource limits.
    
*   **Configuring Log Collection**: Ensuring the Azure Monitor Agent was properly installed and sending logs required some troubleshooting.
    
*   **Security Risks**: Leaving RDP open is inherently risky. I had to monitor the VM closely and planned to secure it after testing.
    

Future Plans
------------

*   **Integrate Threat Intelligence Feeds**: I'm planning to set up a threat intelligence feed to bring in IOCs into Sentinel, enhancing detection capabilities.
    
*   **Automate Responses**: Looking into using Azure Logic Apps to automate responses to certain alerts, making the SOC more proactive.
    
*   **Expand the Lab**: I want to add more VMs and services to monitor, creating a more robust and comprehensive lab environment.
    

Screenshots
-----------

Here are some screenshots from the project:

![Microsoft Sentinel Analytics](https://github.com/MegaByteKnight/Building-a-SOC-with-Azure-and-Microsoft-Sentinel/blob/main/images/sentinel%20analytics.jpg)

References
----------

*   [Microsoft Sentinel Documentation](https://docs.microsoft.com/en-us/azure/sentinel/)
    
*   [Azure Virtual Machines Documentation](https://docs.microsoft.com/en-us/azure/virtual-machines/)
