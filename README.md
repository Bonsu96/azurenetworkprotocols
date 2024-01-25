# Azure Network Protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />
</p>

What is Network Security Groups?

**Network Security Groups (NSGs)** in Azure are a fundamental element of the network security model. They act as a basic, stateful, packet-filtering firewall that enables or denies inbound and outbound traffic to network interfaces (NIC), VMs, and subnets. NSGs can be associated with either subnets or individual NICs attached to Azure Virtual Machines.

Each NSG contains a set of security rules that allow or deny traffic based on source and destination IP addresses, port ranges, and protocols. These rules are processed in priority order, with lower numbers having higher priority.

<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04


### Tracking Traffic Between Virtual Machines in Azure:

To track traffic between virtual machines (VMs) in Azure, you can follow these steps:

1. **Understand NSG Rules:**
   - Review and understand the NSG rules associated with the source and destination VMs. Ensure that the rules are configured to allow the desired traffic.

2. **Check NSG Associations:**
   - Ensure that the NSG is associated with the correct subnet or NIC. If an NSG is not associated correctly, it may not be applying the rules to the traffic.

3. **Use Network Watcher:**
   - Azure provides a tool called [Network Watcher](https://docs.microsoft.com/en-us/azure/network-watcher/network-watcher-monitoring-overview) that can help you monitor and diagnose network issues.
   - You can use the "Traffic Analytics" feature within Network Watcher to get insights into traffic flows between your VMs.

4. **Enable Diagnostic Logging:**
   - Enable diagnostic logging for your network security group. This can be done in the Azure portal or using Azure PowerShell or Azure CLI.
   - Diagnostic logs provide detailed information about NSG traffic, including allowed and denied traffic.

   Example PowerShell command to enable NSG logs:

   ```powershell
   Set-AzNetworkWatcherConfigFlowLog -NetworkWatcher <NetworkWatcherName> -TargetResourceId <ResourceId> -Enabled $true
   ```

5. **Review Logs and Metrics:**
   - Once diagnostic logging is enabled, you can review the logs in Azure Monitor. Logs provide information about allowed and denied traffic, helping you identify any issues.

6. **Azure Monitor and Log Analytics:**
   - Use Azure Monitor and Log Analytics to query and analyze logs for traffic patterns.
   - Create custom queries to filter and search for specific traffic between VMs.

Remember that traffic between VMs in the same subnet may not pass through the NSG if the NSG is associated with the subnet. However, if the VMs are in different subnets or if the NSG is associated with individual NICs, the NSG rules will be applied.

Regularly review and update NSG rules based on your application requirements, and leverage Azure's monitoring and diagnostic tools to track and troubleshoot traffic between virtual machines.
