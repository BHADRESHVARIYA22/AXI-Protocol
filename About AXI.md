AXI  protocol part of AMBA family, AMBA stands for Advanced Microcontroller Bus Architecture.

**The AXI protocol:**
  • is suitable for high-bandwidth and low-latency designs
  • provides high-frequency operation without using complex bridges
  • meets the interface requirements of a wide range of components
  • is suitable for memory controllers with high initial access latency
  • provides flexibility in the implementation of interconnect architectures
  • is backward-compatible with existing AHB and APB interfaces.

**The key features of the AXI protocol are:**
 • separate address/control and data phases
 • support for unaligned data transfers, using byte strobes
 • uses burst-based transactions with only the start address issued
 • separate read and write data channels, that can provide low-cost Direct Memory Access (DMA)
 • support for issuing multiple outstanding addresses
 • support for out-of-order transaction completion
 • permits easy addition of register stages to provide timing closure.

**AXI Architecture**
The AXI protocol is burst-based and defines the following independent transaction channels:
    read address
    read data
    write address
    write data
    write response.
An address channel carries control information that describes the nature of the data to be transferred. The data is
transferred between master and slave using either:
   • A write data channel to transfer data from the master to the slave. In a write transaction, 
     the slave uses the write response channel to signal the completion of the transfer to the master.
   • A read data channel to transfer data from the slave to the master.

![image](https://github.com/BHADRESHVARIYA22/AXI-Protocol/assets/87941725/95f42a38-0b15-49a8-8d65-cf37c253edca)
![image](https://github.com/BHADRESHVARIYA22/AXI-Protocol/assets/87941725/f0f95770-4b4c-479f-9e72-aebb405768e7)


**VALID , READY and LAST signal**
VALID : At Source Side : show when Valid Address, data & control information available on the channel
READY : At Destination : show when accept information (Both Read and Write data channel)
LAST  : At Destination : Indicates the transfer of final data item in transaction


**Read and Write address channels**
 Read and write transactions each have their own address channel. 
 The appropriate address channel carries all of the required address and control information for a transaction

**Read data channel**
 The read data channel carries both the read data and the read response information from the slave to the master, and includes:
   • the data bus, that can be 8, 16, 32, 64, 128, 256, 512, or 1024 bits wide
   • a read response signal indicating the completion status of the read transaction.

**Write data channel**
  The write data channel carries the write data from the master to the slave and includes:
    • the data bus, that can be 8, 16, 32, 64, 128, 256, 512, or 1024 bits wide
    • a byte lane strobe signal for every eight data bits, indicating which bytes of the data are valid.
 Write data channel information is always treated as buffered, so that the master can perform write transactions without slave acknowledgement of 
 previous write transactions.

**Write response channel**
 A slave uses the write response channel to respond to write transactions. All write transactions require completion signaling on the write    
 response channel.

**Interface and interconnect**
 A typical system consists of a number of master and slave devices connected together through some form of interconnect
 The AXI protocol provides a single interface definition, for the interfaces:
   • between a master and the interconnect
   • between a slave and the interconnect
   • between a master and a slave.
This interface definition supports a variety of different interconnect implementations.

**Typical system topologies**
 Most systems use one of three interconnect topologies:
   • shared address and data buses
   • shared address buses and multiple data buses
   • multilayer, with multiple address and data buses.
   
 In most systems, the address channel bandwidth requirement is significantly less than the data channel bandwidth
 requirement. Such systems can achieve a good balance between system performance and interconnect complexity
 by using a shared address bus with multiple data buses to enable parallel data transfers.


 
 






