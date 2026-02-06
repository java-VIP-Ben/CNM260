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

Datastores are used to hold VM files, VM templates and ISO images. 
vSphere supports:
VMFS, NFS, vSAN, and vSphere virtual volumes. 

# Storage Overview 
ESXi hosts should be configured with shared access to datastores. 

# Storage Protocol overview:
Each datastore uses a protocol with varying support features.

VMFS: 
ESXi hosts supports VMFS5, and VMFS6: 
    Feature supported by both of these:
    - Concurrent access to shared storage
    - Dynamic expansion
    - On-disk locking 
    Features supported by VMFS6:
    - 4k native storage devices
    - automatic space reclamation

NFS: 
NFS is a file sharing protocol that ESXi hosts use to communicate with a network-attached
storage (NAS) device. NFS supports NFS 3 and 4.1 over TCP/IP.

vSAN: 
vSAN is hypervisor-converged, software-defined
storage for virtual environments that does not use traditional external storage. 
By clustering host-attached hard disk drives (HDDs) or solid state drives (SSDs) 
vSan creates an aggregated datastore shared by VMs. 

vSphere Virtual Volumes:
 Native representation of VMDKs on SAN/NAS:
No LUNs or volume management
• Works with existing SAN/NAS systems
• A new control path for data operations at the
VM and VMDK level
• Snapshots, replications, and other operations at
the VM level on external storage
• Automates control of per-VM service levels by
using storage policies
• Standard access to storage with the vSphere API
for Storage Awareness protocol endpoint
• Storage containers that span an entire array

Raw Device Mapping: 
Although not a datastore, raw device mapping (RDM) gives a VM direct access to a 
physical LUN. The mapping file (-rdm.vmdk) that points a VM to a LUN must be 
stored on a VMFS datastore. 

Physical storage considerations: 
before implementing your vSphere environment, discuss the storage needs with your storage
administration team. Consider the following factors:
- Lun sizes
- I/O bandwidth required by your applications.
- I/O requests per second that the LUN is capable of 
- Disk cache parameters
- Zoning and masking 
- Multipathing setting for your storage arrays (active-active or active-passive)
- Export properties for NFS datastores

# Lesson 2: Fibre Channel Storage

# lesson 3 iSCSI Components
An iSCSI SAN consists of an iscsi storage system, which contains LUNs and storage processors
Communication between the host and storage array occurs over a TCP/IP network. 

Storage device naming conventions:
Storage devices are identified in several ways 
Runtime name: Uses the vmhbaN:C:T;L convention. This name is not persistent through reboots
Target: Identifies the iSCSI target address and port. 
LUN: A unique identifier designated to individual or collections of hard disk devices.
A logical unit is addressed by the SCSI protocol or SAN protocols that encapsulate SCSI,
such as iSCSI or fibre channel. 

iSCSI Adapters: 
You must set up hardware iSCSI adapters before an ESXi host can work with iSCSI storage.
To access iSCSI targets, your host uses iSCSI initiators. 

ESXi Network Configuration for IP Storage: 
A VMkernel port must be created for ESXi to access software iSCSI. The same port can be 
used to access NAS and NFS storage. To optimize your vSphere networking setup, separate
iSCSI networks from NAS and NFS networks. Physical separation is preferred. If
physical separation is not possible, use VLANs. 

# Lesson 6: vSAN Datastores
About vSAN Datastores
vSAN is a software-defined storage solution
providing shared storage for vSphere clusters
without using traditional external storage.
A vSAN cluster requires:
• A minimum of three hosts to be part of the
vSphere cluster and enabled for vSAN
• A vSAN network
• Local disks on each host that are pooled to
create a virtual shared vSAN datastore

Disk Groups: 
Disk groups are vSAN management constructs on all ESXi hosts in a vSAN
cluster. A host can include a maximum of five disk groups.
The disk groups are combined to create a single
vSAN datastore. A disk group requires:
• One flash device for caching
• One to seven capacity devices for storage

vSAN hardware requirements: 
vSAN capabilities are native to ESXi and require no additional software. 
