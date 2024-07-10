AXI  protocol part of AMBA family, AMBA stands for Advanced Microcontroller Bus Architecture.  
The AMBA AXI protocol supports high-performance, high-frequency system designs.  
## **About AXI protocol**
#### **The AXI protocol:**  
- is suitable for high-bandwidth and low-latency designs
- provides high-frequency operation without using complex bridges
- meets the interface requirements of a wide range of components
- is suitable for memory controllers with high initial access latency
- provides flexibility in the implementation of interconnect architectures
- is backward-compatible with existing AHB and APB interfaces.  

#### **The key features of the AXI protocol are:**  
- separate address/control and data phases
- support for unaligned data transfers, using byte strobes
- uses burst-based transactions with only the start address issued
- separate read and write data channels, that can provide low-cost Direct Memory Access (DMA)
- support for issuing multiple outstanding addresses
- support for out-of-order transaction completion
- permits easy addition of register stages to provide timing closure.  

## **AXI Architecture**  
- The AXI protocol is burst-based and defines the following independent transaction channels:
- 2 Read Channels
  - read address
  - read data
- 3 write Channels
  - write address
  - write data
  - write response.  

An address channel carries control information that describes the nature of the data to be transferred. 
#### **The data is transferred between master and slave using either:**  
  - A write data channel to transfer data from the master to the slave. In a write transaction, the slave uses the write response channel to signal the completion of the transfer to the master.
  - A read data channel to transfer data from the slave to the master.
    
![image](https://github.com/BHADRESHVARIYA22/AXI-Protocol/assets/87941725/c780c079-6369-4cfa-824f-9544b340f712)

## **Channel Defination**

#### **Read and Write address channels**  
  - Read and write transactions each have their own address channel.
  - The appropriate address channel carries all of the required address and control information for a transaction  

#### **Read data channel**  
  - The read data channel carries both the read data and the read response information from the slave to the master, and includes:
    - the data bus, that can be 8, 16, 32, 64, 128, 256, 512, or 1024 bits wide
    - a read response signal indicating the completion status of the read transaction.  

#### **Write data channel**  
- The write data channel carries the write data from the master to the slave and includes:
  - the data bus, that can be 8, 16, 32, 64, 128, 256, 512, or 1024 bits wide
  - a byte lane strobe signal for every eight data bits, indicating which bytes of the data are valid.  
 - Write data channel information is always treated as buffered, so that the master can perform write transactions without slave acknowledgement of 
 previous write transactions.  

#### **Write response channel**  
 - A slave uses the write response channel to respond to write transactions. All write transactions require completion signaling on the write response channel.

#### **Transfer**
  - A piece of data transmitted on a single channel is called a transfer. A transfer happens when both the VALID and READY signal are high while there is a rising edge of the clock.  
  - For example, in the figure below, the transfer is happening on T3:
  - 
![image](https://github.com/BHADRESHVARIYA22/AXI-Protocol/assets/87941725/40cd945a-d788-432d-bc8b-2b62ad7280e7)

#### **AXI Read Transaction**
  -  An AXI Read transactions requires multiple transfers on the 2 Read channels.  
    -  First, the Address Read Channel is sent from the Master to the Slave to set the address and some control signals.  
    -  Then the data for this address is transmitted from the Slave to the Master on the Read data channel.  
    -  Note that, as per the figure below, there can be multiple data transfers per address. This type of transaction is called a burst.
     
     ![image](https://github.com/BHADRESHVARIYA22/AXI-Protocol/assets/87941725/4d149d73-cea9-426a-a2bf-94ec4476e9f2)

#### **AXI Write Transactions**  
  - An AXI Write transactions requires multiple transfers on the 3 Read channels.
    - First, the Address Write Channel is sent Master to the Slave to set the address and some control signals.
    - Then the data for this address is transmitted Master to the Slave on the Write data channel.
    - Finally the write response is sent from the Slave to the Master on the Write Response Channel to indicate if the transfer was successful.
    - 
      ![image](https://github.com/BHADRESHVARIYA22/AXI-Protocol/assets/87941725/30370aa4-8353-4ef2-b541-b480dc019d38)

## **Interface and interconnect**  
  - A typical system consists of a number of master and slave devices connected together through some form of interconnect
    ![image](https://github.com/BHADRESHVARIYA22/AXI-Protocol/assets/87941725/4235ae5e-cbcd-4eda-9650-b6898fe943a9)

  - The AXI protocol provides a single interface definition, for the interfaces:
    - between a master and the interconnect
    - between a slave and the interconnect
    - between a master and a slave.  
  - This interface definition supports a variety of different interconnect implementations.  
  - An interconnect between devices is equivalent to another device with symmetrical master and slave ports to which real master and slave devices can be connected.  

#### **Typical system topologies**  
- Most systems use one of three interconnect topologies:  
  - shared address and data buses  
  - shared address buses and multiple data buses  
  - multilayer, with multiple address and data buses.  
  
 In most systems, the address channel bandwidth requirement is significantly less than the data channel bandwidth
 requirement. Such systems can achieve a good balance between system performance and interconnect complexity
 by using a shared address bus with multiple data buses to enable parallel data transfers.  

#### **Register slices**  
  - Each AXI channel transfers information in only one direction, and the architecture does not require any fixed relationship between the channels.  
  - These qualities mean that a register slice can be inserted at almost any point in any channel at the cost of an additional cycle of latency.
  - These qualities make the following possible:  
    - Trade-off between cycles of latency and maximum frequency of operation.  
    - Direct, fast connection between a processor and high-performance memory, while using simple register slices to isolate longer paths to less performance critical peripherals.
      
#### **Terminology**    
**Component**    
  - Component can be used as a general term for master,slave, peripheral, and interconnect components.  
**Master component**
  - A component that initiates transactions.
  - It is possible that a single component can act as both a master component and as a slave component
**Slave component**
  - component that receives transactions and responds to them.
  - It is possible that a single component can act as both a slave component and as a master component
**Interconnect component**
  - A component with more than one AMBA interface that connects one or more master components to one or more slave components
  - An interconnect component can be used to group together either:
    - a set of masters so that they appear as a single master interface
    - a set of slaves so that they appear as a single slave interface.



 
 






