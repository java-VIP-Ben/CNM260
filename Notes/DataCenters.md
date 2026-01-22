# Benjamin Lukens CNM260 Data Centers Notes

Data centers main components: 
Compute, Network infrastructure, storage, power, cooling, cybersecurity systems

Compute components: 
Cpu, Ram, Storage, Network/Fabric connection.

Blades: 
CPU, Ram, Storage
A blade chassis separates the power and other various components from the main components


# Networking 

Core Network:
- Large Cache Technology
    The data center switch has changed the outgoing port caching method of the 
    traditional switch. It adopts a distributed cache architecture, and the 
    cache is much larger than that of an ordinary switch. The cache capacity 
    can reach more than 1G, while the general switch can only reach 2-4m. For each 
    port, the burst traffic cache capacity can reach 200ms under the condition
    of 10 gigabit full line speed, so that in the case of burst traffic, the large
    cache capacity can still ensure zero packet loss in network forwarding, which 
    is just suitable for a large number of servers in the data center and the burst
    traffic. 
- High Capacity Equipment
    The network traffic in the data center has the characteristics of high density application
    scheduling and surge burst buffering. However, ordinary switches cannot achieve
    accurate identification and control of services with the purpose of 
    interconnection. Neither can they achieve rapid response and zero packet loss, 
    so business continuity cannot be guaranteed. The reliability of the system 
    depends on the reliability of the equipment. 
- TRILL technology
    In terms of building a layer two network in the data center, the original 
    standard is FTP protocol. But it has the following defects: 
        - STP works through port blocking, and all redundant links do not forward data,
        resulting in a waste of broadband resources. 
        - The network has only one spanning tree, and data packets must pass through 
        the root bridge, which effects the forwarding efficiency of the entire network. 
- Link Redundancy
    In order to maintain the stability of the network, in a network environment
    composed of multiple switches, some backup connections are used to improve the efficiency
    and stability of the network. The backup connections here are also called backup links
    or redundancy links. 

# Core Network
- Stacking of switches
    Connected via proprietary stacking cables, multiple swtiches can be stacked into a single
    logical switch. All switches in this logical switch contain the same configuration
    and routing information. The performance of a logical switch will not be affected
    as an individual switch is added and removed. 

# About Datastores
A datastore is a physical is a logical storage unit that can use disk space on one physical 
device or span several physical devices.
