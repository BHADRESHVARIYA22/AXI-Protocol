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



