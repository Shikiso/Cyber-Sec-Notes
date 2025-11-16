An Azure service that allows you to evenly distribute incoming network traffic across a group of VMs or across instances in a VM Scale Set.

Load Balances deliver high availability and network performance. This is done by these ways:
- Load-balancing rules determine how traffic is distributed to instances that comprise the back end.
- Health probes ensure the resources in the back end are healthy and that traffic isn't directed to unhealthy back-end instances.

You can deploy public or private (internal) load balance's in Azure.
- Public are used to load balance internet traffic to your VMs
- Private directs traffic to resources inside a virtual network.

# How they work
They operate at the transport layer, allowing traffic management  based on specific properties of the traffic.

Load balancer has several elements that work together to ensure an applications high availability and performance:
- Front-end IP - Address clients use to connect to your web application
- Load balancer rules - Defines how traffic is distributed
- Back-end pool - Group of VMs or instances
- Health probes - Determines the health status of instances in back-end pool
- Inbound NAT rules 
- High availability ports - A load balancer rule with `protocol - all and port 0` configured
- Outbound rules

# When to use
Azure Load Balancer is best suited for applications that require ultra-low latency and high performance.

Do not use when the application only receives a small amount of traffic and the existing infrastructure is competent.