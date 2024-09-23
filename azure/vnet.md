### Why Do We Need Azure Virtual Network (VNet)?

Azure Virtual Network (VNet) is an essential service in Microsoft Azure that enables you to create a private, isolated network within the cloud. Here's why it's needed:

#### 1. **Isolation and Security**

- **Isolation**: VNet ensures that resources such as virtual machines (VMs), databases, and services deployed within your network are logically isolated from other networks, including other VNets and the public internet.
- **Security**: By defining network security rules, like **Network Security Groups (NSGs)**, you can control inbound and outbound traffic. VNet allows for **network segmentation**, **firewalls**, and **encryption** to protect data in transit.

#### 2. **Private Communication**

- Resources within the VNet can communicate securely with each other through **private IP addresses**. This avoids exposure to the public internet, adding an extra layer of protection for sensitive workloads.
- You can also connect your VNet to **on-premises environments** via **VPN Gateway** or **ExpressRoute**, allowing hybrid cloud solutions with secure connectivity.

#### 3. **Network Segmentation and Traffic Control**

- **Subnets** within a VNet allow for better organization and isolation of resources. For example, you can separate different types of workloads (e.g., frontend web servers, backend databases) into different subnets.
- Use **Route Tables** to control the flow of traffic between subnets or between a VNet and the internet. This can improve network efficiency and security by directing traffic to where it needs to go.

#### 4. **Scalability and Flexibility**

- VNet supports **auto-scaling** as your application grows. You can easily add more resources (e.g., VMs, databases) without affecting network performance.
- You can also **peering** between VNets to extend your network across regions, allowing resources in different VNets to communicate as though they are within the same network.

#### 5. **Integration with Azure Services**

- Many Azure services, such as **Azure Kubernetes Service (AKS)**, **Azure App Service Environment**, **Azure SQL Database**, and others, can be deployed within a VNet, enabling secure access and integration with other networked resources.

#### 6. **Hybrid Connectivity**

- VNet supports **hybrid cloud environments**, where your on-premises infrastructure and cloud infrastructure can be securely connected. Tools like **VPN Gateway** and **ExpressRoute** facilitate this integration, allowing organizations to extend their private networks into the cloud seamlessly.

#### 7. **Enhanced Traffic Monitoring**

- With tools like **Azure Network Watcher** and **Network Security Groups (NSGs)**, you can monitor network traffic, detect issues, and troubleshoot connectivity problems within the VNet.
- **Azure Firewall** and **Distributed Denial of Service (DDoS) Protection** can also be integrated to enhance security and monitor against malicious traffic.

#### 8. **Cost Management**

- VNet is a cost-effective way to organize and optimize your resources in Azure. You only pay for outbound data transfer and certain optional services like VPN gateways, making it flexible to suit budget needs.

---

### What is Azure Virtual Network (VNet)?

Azure Virtual Network (VNet) is a foundational networking service in Microsoft Azure that enables users to create their own isolated network in the cloud. VNet allows Azure resources, such as virtual machines (VMs), containers, and services, to communicate securely with each other, the internet, and on-premises networks. It functions similarly to a traditional on-premises network but with the flexibility and scalability of the cloud.

#### Key Features of Azure VNet:

1. **Private Networking**

   - VNet provides a secure, isolated environment where Azure resources can communicate with each other using **private IP addresses**. It ensures that only authorized resources can interact with the services inside the VNet.

2. **Subnets**

   - A VNet can be divided into multiple **subnets**, which are smaller segments of the network. Subnets allow for better network organization and control of traffic between different parts of your application (e.g., separating web servers from database servers).

3. **Security**

   - **Network Security Groups (NSGs)**: NSGs allow you to define security rules to control inbound and outbound traffic for resources within a VNet.
   - **Azure Firewall and DDoS Protection**: For more advanced security, you can add services like Azure Firewall or Distributed Denial of Service (DDoS) Protection.

4. **Connectivity Options**

   - **VNet Peering**: You can link multiple VNets together, even across different Azure regions, allowing resources in different VNets to communicate as though they are in the same network.
   - **Hybrid Connectivity**: Connect your on-premises network to your VNet using **VPN Gateway** or **Azure ExpressRoute** for secure, private communication.
   - **Internet Connectivity**: VNets support outbound internet traffic for resources that require public access (e.g., web applications).

5. **Integration with Azure Services**

   - Many Azure services, such as **Azure App Service**, **Azure SQL Database**, and **Azure Kubernetes Service (AKS)**, can be deployed within a VNet, ensuring secure access and reducing exposure to the public internet.

6. **Routing and Traffic Control**

   - Azure allows you to configure **route tables** to control traffic flow within your VNet or between a VNet and other networks (e.g., the internet or on-premises).
   - You can also integrate **Load Balancers** and **Application Gateways** to manage incoming traffic efficiently.

7. **Scalability and Flexibility**

   - VNets are highly scalable and can grow as your application requirements increase. Resources can be added or removed without affecting the overall network performance.
   - You can define IP address ranges, subnets, and security rules to fit your specific needs.

8. **Monitoring and Troubleshooting**
   - **Azure Network Watcher** provides monitoring capabilities to troubleshoot connectivity issues, view metrics, and log data for your VNet.
   - **Traffic analytics** and **diagnostics logs** help track network health and detect potential security or performance issues.

#### Common Use Cases for Azure VNet:

- Hosting a web application with secure backend services (e.g., databases or APIs).
- Setting up a hybrid cloud by securely connecting an on-premises network with Azure using VPN or ExpressRoute.
- Creating isolated, internal networks for workloads that should not be exposed to the public internet.
- Building microservices architectures by segregating services using subnets within the same VNet.

---

### How to Define the Size of a VNet in Azure

When creating a Virtual Network (VNet) in Azure, you define its size by specifying the **IP address space** using **CIDR notation** (Classless Inter-Domain Routing). This determines the range of private IP addresses available within the VNet, which can be subdivided into smaller segments called **subnets**.

Here’s a step-by-step guide to defining the size of a VNet:

### 1. **Choose the IP Address Space**

When you create a VNet, you need to specify the IP address space in **CIDR** (e.g., `10.0.0.0/16`). This defines how many IP addresses are available in your VNet.

- **CIDR Notation**: It specifies both the IP range and the number of bits used for the network prefix.

  - Example: `10.0.0.0/16`
    - `10.0.0.0` is the starting IP address.
    - `/16` means the first 16 bits represent the network portion of the address, leaving 16 bits for defining hosts.

- **Size of the VNet**: The `/16` block provides 65,536 IP addresses, allowing you to create multiple subnets within that VNet. Smaller networks (like `/24` or `/28`) provide fewer addresses.

| CIDR Notation | Number of IP Addresses | Usable Addresses |
| ------------- | ---------------------- | ---------------- |
| `/16`         | 65,536                 | 65,532           |
| `/24`         | 256                    | 251              |
| `/28`         | 16                     | 11               |

### 2. **Plan the Address Space**

- **Default IP Ranges**: Azure uses certain ranges for private VNets:
  - `10.0.0.0/8`
  - `172.16.0.0/12`
  - `192.168.0.0/16`
- It's essential to avoid conflicts with existing on-premises networks or other VNets if you plan to connect them via **VPN Gateway** or **ExpressRoute**.

### 3. **Subnet Design**

- After defining the IP address space for the VNet, you divide it into **subnets**.
- For example, if your VNet address space is `10.0.0.0/16`, you could split it into subnets:
  - `10.0.0.0/24`: Subnet 1 with 256 addresses
  - `10.0.1.0/24`: Subnet 2 with 256 addresses
- **Azure Reserved IPs**: Each subnet has 5 reserved IPs (e.g., for Azure routing, gateway, and other internal purposes), so if a subnet is `/24` (256 addresses), only 251 are usable.

### 4. **Choosing the Right VNet Size**

- **Small Applications**: A smaller address space (e.g., `/24`, providing 256 addresses) may be sufficient if you only need a few VMs or services.
- **Large Applications**: If you plan to scale or integrate with other networks, a larger range (e.g., `/16`, providing 65,536 addresses) might be necessary to avoid future reconfiguration.
- **Future Growth**: Always consider future expansion. If you expect your VNet to grow, allocate a larger address space upfront (e.g., `/16`), even if your initial subnets are small.

### 5. **Avoiding Overlap with On-Premises Networks**

- If you are setting up a hybrid network (connecting Azure with your on-premises environment), ensure that the VNet’s IP address range doesn’t overlap with your existing on-premises IP ranges.
- This is important for smooth communication between the on-premises network and Azure resources over **VPN Gateway** or **ExpressRoute**.

### Example of VNet and Subnet Allocation:

- **VNet Address Space**: `10.0.0.0/16` (65,536 addresses)
  - **Subnet 1**: `10.0.0.0/24` (256 addresses, 251 usable)
  - **Subnet 2**: `10.0.1.0/24` (256 addresses, 251 usable)
  - **Subnet 3**: `10.0.2.0/28` (16 addresses, 11 usable)

This allows you to structure your application into distinct subnets (e.g., web, database, and management), each with its own security and routing rules.

---

### How to Subnet a VNet in Azure

Subnetting a Virtual Network (VNet) in Azure is the process of dividing the VNet's address space into smaller segments, known as **subnets**. Subnets allow you to organize and manage resources more efficiently by isolating different types of workloads and controlling network traffic. Here's how you can subnet a VNet:

### 1. **Plan the VNet and Subnet Address Spaces**

Before creating subnets, plan your VNet's address space. This involves choosing an IP range for the VNet using **CIDR notation** and then defining smaller ranges for each subnet.

- **Example of a VNet Address Space**: `10.0.0.0/16` (This provides 65,536 IP addresses for the entire VNet).
- From this range, you can divide it into multiple smaller subnets. For example:
  - Subnet 1: `10.0.1.0/24` (256 addresses)
  - Subnet 2: `10.0.2.0/24` (256 addresses)
  - Subnet 3: `10.0.3.0/28` (16 addresses)

### 2. **Choose Appropriate Subnet Sizes**

Determine how large each subnet needs to be based on the number of resources you plan to deploy. Remember that Azure reserves **5 IP addresses** in each subnet for internal use, so consider this when planning.

- **/24 subnet** provides 256 addresses, but 251 usable.
- **/28 subnet** provides 16 addresses, but 11 usable.

### 3. **Create the Subnets**

Once you have planned the address spaces, you can create the subnets within the VNet in the Azure portal, through PowerShell, the Azure CLI, or via an ARM template.

#### Using Azure Portal

1. **Navigate to Virtual Networks**:

   - Open the [Azure Portal](https://portal.azure.com) and search for "Virtual Networks".
   - Select the VNet you want to subnet or create a new one.

2. **Create a Subnet**:

   - In the VNet settings, click on **Subnets**.
   - Click **+ Subnet** to add a new subnet.

3. **Configure the Subnet**:

   - **Subnet Name**: Provide a meaningful name for the subnet (e.g., "WebSubnet", "DbSubnet").
   - **Address Range (CIDR block)**: Specify the subnet address range using CIDR notation (e.g., `10.0.1.0/24` for 256 IP addresses).
   - **Network Security Group (Optional)**: You can associate an NSG to control inbound and outbound traffic for the subnet.
   - **Route Table (Optional)**: You can also associate a route table if you need custom routing.

4. **Repeat for Additional Subnets**:
   - Add as many subnets as needed, ensuring that the address spaces do not overlap.

#### Example: Creating Two Subnets

- **VNet Address Space**: `10.0.0.0/16`
  - **Subnet 1**: `10.0.1.0/24` (for web servers)
  - **Subnet 2**: `10.0.2.0/24` (for database servers)

Each subnet now has a dedicated segment of the VNet’s address space.

#### Using Azure CLI

You can also create subnets using the Azure CLI. Here’s how to create a subnet:

```bash
# Create a VNet with a specific address range
az network vnet create \
  --resource-group MyResourceGroup \
  --name MyVNet \
  --address-prefix 10.0.0.0/16

# Add Subnet 1 (WebSubnet) with 10.0.1.0/24 address space
az network vnet subnet create \
  --resource-group MyResourceGroup \
  --vnet-name MyVNet \
  --name WebSubnet \
  --address-prefix 10.0.1.0/24

# Add Subnet 2 (DbSubnet) with 10.0.2.0/24 address space
az network vnet subnet create \
  --resource-group MyResourceGroup \
  --vnet-name MyVNet \
  --name DbSubnet \
  --address-prefix 10.0.2.0/24
```

#### Using Azure PowerShell

Here’s how to create subnets using PowerShell:

```powershell
# Create a VNet
$virtualNetwork = New-AzVirtualNetwork `
  -ResourceGroupName "MyResourceGroup" `
  -Location "EastUS" `
  -Name "MyVNet" `
  -AddressPrefix "10.0.0.0/16"

# Add Subnet 1 (WebSubnet)
Add-AzVirtualNetworkSubnetConfig `
  -Name "WebSubnet" `
  -AddressPrefix "10.0.1.0/24" `
  -VirtualNetwork $virtualNetwork

# Add Subnet 2 (DbSubnet)
Add-AzVirtualNetworkSubnetConfig `
  -Name "DbSubnet" `
  -AddressPrefix "10.0.2.0/24" `
  -VirtualNetwork $virtualNetwork

# Commit the changes
Set-AzVirtualNetwork -VirtualNetwork $virtualNetwork
```

### 4. **Consider Subnet Security and Traffic Control**

Each subnet can have its own **Network Security Group (NSG)** to control inbound and outbound traffic. For example, you might want to allow HTTP/HTTPS traffic to a web subnet but restrict access to a database subnet.

- **WebSubnet**: NSG allows inbound traffic on port 80 (HTTP) and port 443 (HTTPS).
- **DbSubnet**: NSG only allows inbound traffic from the WebSubnet on specific ports (e.g., 3306 for MySQL or 1433 for SQL Server).

### 5. **Route Table (Optional)**

You can associate **route tables** with your subnets to customize traffic flow. This can be useful for scenarios such as directing traffic to a firewall or VPN gateway.

### Example Subnet Design:

Assume you are hosting a multi-tier web application with the following components:

- **Frontend (Web Servers)** in a web subnet.
- **Backend (API Servers)** in an app subnet.
- **Database (SQL Servers)** in a database subnet.

You might plan your VNet as follows:

| Subnet Name | Address Space | Usage                                |
| ----------- | ------------- | ------------------------------------ |
| WebSubnet   | `10.0.1.0/24` | Web servers (public-facing)          |
| AppSubnet   | `10.0.2.0/24` | API servers (internal communication) |
| DbSubnet    | `10.0.3.0/24` | Database servers (isolated)          |

---

### **NSG (Network Security Group)** vs. **ASG (Application Security Group)** in Azure

Both **NSGs** and **ASGs** are essential components in managing and securing traffic within a Virtual Network (VNet) in Azure, but they serve different purposes. Here's an overview of each:

---

### 1. **NSG (Network Security Group)**

**NSG** is a core component in Azure networking used to control **inbound and outbound traffic** to network interfaces (NICs), VMs, or subnets within a VNet. It works as a virtual firewall with **rules** that allow or deny traffic based on certain conditions like **IP addresses**, **ports**, and **protocols**.

#### Key Features:

- **Security Rules**: An NSG consists of inbound and outbound security rules that determine what traffic is allowed or denied.
  - Example rule: Allow HTTP traffic (port 80) from the internet to a specific VM.
- **Applied to Subnets or NICs**: You can apply an NSG to:
  - **Subnet**: Affects all resources in the subnet.
  - **Network Interface (NIC)**: Affects only the associated VM or resource.
- **Direction**: NSG rules can be for inbound or outbound traffic.
- **Priority**: Rules have priority values, and Azure evaluates the rules in ascending order, applying the first matching rule.

#### Example Scenario for NSG:

You have a web application hosted on Azure, and you want to:

- **Allow inbound traffic** to the web servers on **port 80 (HTTP)** and **port 443 (HTTPS)**.
- **Deny all other inbound traffic**.
- Allow **outbound traffic** only to specific external services or APIs.

#### Example of NSG Rules:

| Priority | Source          | Source Port | Destination | Destination Port | Protocol | Action |
| -------- | --------------- | ----------- | ----------- | ---------------- | -------- | ------ |
| 100      | Internet        | \*          | WebSubnet   | 80, 443          | TCP      | Allow  |
| 200      | Virtual Network | \*          | WebSubnet   | \*               | \*       | Allow  |
| 300      | WebSubnet       | \*          | AppSubnet   | \*               | \*       | Allow  |
| 400      | \*              | \*          | WebSubnet   | \*               | \*       | Deny   |

---

### 2. **ASG (Application Security Group)**

**ASG** is a more flexible way to group resources such as VMs and apply security rules based on **logical groupings** rather than individual IP addresses or NICs. ASGs simplify the management of NSG rules by allowing you to create dynamic groups of VMs, enabling you to apply security policies to these groups.

#### Key Features:

- **Logical Grouping**: ASGs allow you to group VMs or network interfaces based on application tiers (e.g., **WebServers**, **DatabaseServers**, etc.), making it easier to manage security policies.
- **Used with NSG**: You use ASGs within an NSG to apply security rules to a group of VMs rather than specifying individual IP addresses.
- **Dynamic Membership**: You can add or remove resources from an ASG without modifying the security rules. This is useful for dynamic environments, such as scaling out a web server farm.

#### Example Scenario for ASG:

You have a multi-tier application with:

- A group of **Web Servers**.
- A group of **Database Servers**.

You want the **Web Servers** to communicate with the **Database Servers** on specific ports, and to control access based on group membership instead of IP addresses.

#### Example of ASG Usage in NSG:

1. **Create ASGs**:

   - **ASG-WebServers**: Group containing all web server VMs.
   - **ASG-DbServers**: Group containing all database server VMs.

2. **Define NSG Rules using ASGs**:

   - Allow traffic from **ASG-WebServers** to **ASG-DbServers** on port **1433** (SQL Server).
   - Deny all other traffic between groups.

   | Priority | Source ASG     | Destination ASG | Port | Protocol | Action |
   | -------- | -------------- | --------------- | ---- | -------- | ------ |
   | 100      | ASG-WebServers | ASG-DbServers   | 1433 | TCP      | Allow  |
   | 200      | \*             | ASG-WebServers  | \*   | \*       | Deny   |

### 3. **Key Differences between NSG and ASG**

| **Feature**         | **NSG (Network Security Group)**                                 | **ASG (Application Security Group)**                                |
| ------------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Purpose**         | Control traffic to/from resources based on IP, port, protocol    | Logical grouping of VMs or NICs for easier application of NSG rules |
| **Scope**           | Can be applied to a subnet or individual NIC/VM                  | Cannot apply rules on its own; used within NSG rules                |
| **Traffic Control** | Controls traffic using IP addresses, port numbers, and protocols | Controls traffic between groups of resources without specifying IPs |
| **Use Case**        | Enforcing security rules for individual resources or subnets     | Simplifying NSG rules for application tiers or dynamic workloads    |
| **Management**      | Requires specifying IP addresses or ranges                       | Simplifies management by grouping resources logically               |
| **Flexibility**     | Less flexible for large-scale management of dynamic resources    | More flexible, allowing easier management and scaling of VMs        |
| **Example Usage**   | Enforcing inbound/outbound security for a subnet or VM           | Grouping VMs into web, app, and database tiers for easier NSG rules |

### 4. **Using NSG and ASG Together**

You typically use **NSG** and **ASG** together for better manageability:

- **NSG** is the firewall that enforces security policies.
- **ASG** is used within the NSG rules to create logical groupings, simplifying rule management.

For example, you can create a rule in the NSG that allows communication between ASGs (like WebServers and DbServers) rather than managing IP addresses and individual VMs.

---

### **Route Tables in Azure**

**Route Tables** in Azure, also known as **User-Defined Routes (UDR)**, control the flow of network traffic within and outside of a Virtual Network (VNet). By default, Azure sets up some routes, but you can also create custom route tables to direct traffic according to your requirements.

---

### 1. **Default Routing in Azure VNets**

When you create a VNet in Azure, Azure automatically handles routing to enable basic connectivity:

- **Within the VNet**: VMs in the same VNet can communicate with each other automatically.
- **Between Subnets**: Subnets within the same VNet have automatic connectivity unless otherwise restricted (e.g., with Network Security Groups).
- **Outbound to the Internet**: Traffic to public IP addresses is routed through the default internet gateway if the VM has a public IP.
- **Inbound via VPN/ExpressRoute**: Routes are created automatically for traffic between VNets and on-premises networks when you configure **VPN** or **ExpressRoute**.

---

### 2. **User-Defined Routes (UDR)**

While the default routes work for most scenarios, there are cases where you need more control. This is where **User-Defined Routes (UDR)** come in. You can create custom routes to direct traffic through **Network Virtual Appliances (NVAs)**, **firewalls**, or other destinations.

#### Common Use Cases for Custom Route Tables:

- **Traffic Filtering**: Route traffic through a **firewall** or a **Network Virtual Appliance (NVA)** for filtering.
- **Forced Tunneling**: Direct all outbound internet traffic through an **on-premises** network (via VPN or ExpressRoute) instead of directly through Azure’s internet gateway.
- **Custom Routing for Subnets**: Control the traffic between different subnets, VNets, or external networks by specifying next-hop addresses.

---

### 3. **Components of a Route Table**

A Route Table consists of one or more **routes**. Each route defines the **destination** and the **next hop**.

#### Key Components of a Route:

- **Address Prefix (Destination)**: The destination IP range (in CIDR notation) that the route applies to.
- **Next Hop Type**: Specifies where the traffic should be directed. Available types include:
  - **Virtual Network Gateway**: Used to route traffic through an Azure VPN Gateway for on-premises connections.
  - **Virtual Network**: Default route within the VNet.
  - **Internet**: Directs traffic to the internet.
  - **Virtual Appliance**: Directs traffic to a **Network Virtual Appliance (NVA)**, such as a firewall or load balancer, using its private IP.
  - **None**: Blocks traffic to the specified address range.

#### Example of Custom Route Table:

| **Destination** | **Next Hop Type** | **Next Hop Address** |
| --------------- | ----------------- | -------------------- |
| 10.0.2.0/24     | Virtual Appliance | 10.0.1.4 (NVA)       |
| 0.0.0.0/0       | Internet          | N/A                  |
| 10.0.0.0/16     | Virtual Network   | N/A                  |

---

### 4. **Creating a Custom Route Table**

To create a custom route table and associate it with a subnet:

1. **Create a Route Table**:

   - Go to **Azure Portal**.
   - Search for **Route Tables**.
   - Click **Add** and provide a name, resource group, and region.

2. **Add Routes to the Route Table**:

   - Within the route table, go to the **Routes** section and click **Add**.
   - Define the **Address Prefix** (destination) and choose the **Next Hop Type**.
   - For example, you might route traffic to an **NVA** using the **Virtual Appliance** option.

3. **Associate the Route Table with a Subnet**:
   - In the Route Table page, click **Subnets**.
   - Select the VNet and subnet to which you want to associate the route table.
   - Click **Save**.

---

### 5. **Example Scenarios for Route Tables**

#### 1. **Traffic through an NVA (Firewall)**

You might want to route all internal traffic through a firewall or NVA for logging, inspection, or filtering.

**Scenario**: VMs in Subnet A need to send traffic to Subnet B, but all traffic must go through a firewall.

- Create a custom route table for Subnet A, where the **next hop** is the IP of the NVA (firewall).
- Associate the route table with Subnet A.

**Route Table Example**:
| Destination | Next Hop Type | Next Hop Address |
|--------------|------------------|-------------------|
| 10.0.2.0/24 | Virtual Appliance | 10.0.1.4 (NVA IP) |

#### 2. **Forced Tunneling**

**Forced tunneling** ensures that all traffic destined for the internet is sent to your on-premises network (via VPN or ExpressRoute) rather than going directly to the internet.

**Scenario**: You want all internet-bound traffic to pass through an on-premises network for security reasons.

- Set up a custom route for `0.0.0.0/0` (representing all external IPs) with a **next hop** of a **virtual network gateway** (VPN).

**Route Table Example**:
| Destination | Next Hop Type |
|--------------|------------------------|
| 0.0.0.0/0 | Virtual Network Gateway |

---

### 6. **Route Propagation**

Azure **VPN Gateway** and **ExpressRoute Gateway** automatically advertise routes to Azure subnets through **route propagation**. You can enable or disable this feature in the route table settings:

- **Enabled**: Routes learned via the gateway (e.g., from on-premises) are automatically added.
- **Disabled**: Routes from the gateway are ignored, and you must define all custom routes manually.

---

### 7. **Monitoring and Troubleshooting Route Tables**

To ensure your routes are working as expected, you can use:

- **Effective Routes**: Azure provides a tool to view the effective routes applied to a VM or NIC, including system default and user-defined routes.
- **Network Watcher**: This tool allows you to diagnose routing issues by testing packet flow, checking connectivity, and tracing hops.

---

### 8. **Important Considerations**

- **Default Routes**: Azure VNets come with default routes that allow connectivity within the VNet and to the internet. Custom routes override these default routes.
- **Overlap**: Be careful with overlapping routes, as more specific routes (e.g., `/24`) will take precedence over less specific ones (e.g., `/16`).
- **Route Limits**: Each route table has a limit on the number of routes that can be added (400 for UDRs by default). Be mindful of this when designing complex network architectures.

---
