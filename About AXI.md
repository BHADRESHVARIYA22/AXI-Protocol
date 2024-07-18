AXI  protocol part of AMBA family, AMBA stands for Advanced Microcontroller Bus Architecture.  
The AMBA AXI protocol supports high-performance, high-frequency system designs.  
# **1. About AXI protocol**
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
- Write request, which has signal names beginning with AW.
- Write data, which has signal names beginning withW.
- Write response, which has signal names beginning with B.
- Read request, which has signal names beginning with AR.
- Read data, which has signal names beginning with R.
- A request channel carries control information that describes the nature of the data to be transferred. This is known as a request.
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

### **Register slices**  
  - Each AXI channel transfers information in only one direction, and the architecture does not require any fixed relationship between the channels.  
  - These qualities mean that a register slice can be inserted at almost any point in any channel at the cost of an additional cycle of latency.
  - These qualities make the following possible:  
    - Trade-off between cycles of latency and maximum frequency of operation.  
    - Direct, fast connection between a processor and high-performance memory, while using simple register slices to isolate longer paths to less performance critical peripherals.
      
### **Terminology**    

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
      
**AXI Transaction**
  - An AXI master initiates an AXI transaction to communicate with an AXI slave. Typically, the transaction requires information to be exchanged between the master and slave on multiple channels. The complete set of required information exchanges form the AXI transaction.
    
**AXI Brust**
  - In an AXI transaction, the payload data is transferred in a single burst, that can comprise multiple beats, or individual data transfers.
    
**AXI Beat**
  - An individual data transfer within an AXI burst.

# 2. Signal Descriptions  
### Contains the following sections:
  - Global signals  
  - Write address channel signals   (AW)
  - Write data channel signals      (W)
  - Write response channel signals  (B) 
  - Read address channel signals    (AR)
  - Read data channel signals       (R)
  - Low-power interface signals  

## Global signals 
  - **ACLK**    : Global clock signal.
    - All input signals are sampled on the rising edge of ACLK. All output signal changes must occur after the rising edge of ACLK.   
  - **ARESETn** : Global reset signal, active LOW.
    
## Write address channel signals  
  - Signals on this channel have the prefix AW.
![image](https://github.com/user-attachments/assets/8c915d88-8139-43d1-9e96-5e43035c6698)  

## Write data channel signals 
  - Signals on this channel have the prefix W.
![image](https://github.com/user-attachments/assets/1734826a-37fc-4428-aa59-caa63d7cc3a4)   
 
## Write response channel signals  
  - Signals on this channel have the prefix B.
![image](https://github.com/user-attachments/assets/52ae9b54-5894-4e86-a97a-f139b240463a)
## Read address channel signals  
  - **ARID** Master  
    - Read address ID. This signal is the identification tag for the read address group of signals. 
  - **ARADDR** Master 
    - Read address. The read address gives the address of the first transfer in a read burst transaction. 
  - **ARLEN** Master  
    - Burst length. This signal indicates the exact number of transfers in a burst. This changes between AXI3 and AXI4.  
  - **ARSIZE** Master  
    - Burst size. This signal indicates the size of each transfer in the burst.  
  - **ARBURST** Master  
    - Burst type. The burst type and the size information determine how the address for each transfer within the burst is calculated.  
  - **ARLOCK** Master  
    - Lock type. This signal provides additional information about the atomic characteristics of the transfer. This changes between AXI3 and AXI4.  
  - **ARCACHE** Master  
    - Memory type. This signal indicates how transactions are required to progress through a system.  
  - **ARPROT** Master  
    - Protection type. This signal indicates the privilege and security level of the transaction, and whether the transaction is a data access or an instruction access.  
  - **ARQOS** Master  
    - Quality of Service, QoS. QoS identifier sent for each read transaction. Implemented only in AXI4.   
  - **ARREGION** Master  
    - Region identifier. Permits a single physical interface on a slave to be used for multiple logical interfaces. Implemented only in AXI4.   
  - **ARUSER** Master  
    - User signal. Optional User-defined signal in the read address channel. Supported only in AXI4.   
  - **ARVALID** Master  
    - Read address valid. This signal indicates that the channel is signaling valid read address and control information.   
  - **ARREADY** Slave  
    - Read address ready. This signal indicates that the slave is ready to accept an address and associated control signals.  
## Read data channel signals  
  - **RID** Slave  
    - Read ID tag. This signal is the identification tag for the read data group of signals generated by the slave.   
  - **RDATA** Slave   
    - Read data.
  - **RRESP** Slave   
    - Read response. This signal indicates the status of the read transfer.   
  - **RLAST** Slave   
    - Read last. This signal indicates the last transfer in a read burst.   
  - **RUSER** Slave    
    - User signal. Optional User-defined signal in the read data channel. Supported only in AXI4.  
  - **RVALID** Slave   
    - Read valid. This signal indicates that the channel is signaling the required read data.   
  - **RREADY** Master   
    - Read ready. This signal indicates that the master can accept the read data and response  
information.
## Low-power interface signals   
  - **CSYSREQ** Clock controller   
    - System exit low-power state request. This signal is a request from the system clock controller for the peripheral to exit from a low-power state.   
  - **CSYSACK** Peripheral device   
    - Exit low-power state acknowledgement. This signal is the acknowledgement from a peripheral to a system exit low-power state request.   
  - **CACTIVE** Peripheral device   
    - Clock active. This signal indicates that the peripheral requires its clock signal.
   
# 3. Single Interface Requirements  
## 3.1 Clock and Reset
### Clock (ACKL) 
  - Each AXI component uses a single clock signal (ACKL)
  - All input Signal are samples on the rising edge of ACKL
  - All Output Signal must occur after rising edge of ACKL
### Reset (ARESETn) : Active LOW
  - The reset signal can be asserted Asynchronously but Deassertion must be Synchronous with rising edge of ACKL
  - During reset Following interface requirements apply:
    - a master interface must drive ARVALID, AWVALID, and WVALID LOW
    - a slave interface must drive RVALID and BVALID LOW
    - all other signals can be driven to any value
  -  The earliest point after reset that a master is permitted to begin driving ARVALID, AWVALID, or WVALID HIGH is at a rising ACLK edge after ARESETn is HIGH.  
  ![image](https://github.com/user-attachments/assets/d74f0f79-b82c-4705-a0a8-c6b44a601da1)

### 3.2.1 Channel Handshake  
  - All five transaction channels use the same VALID/READY handshake process to transfer address, data, and control
  - information. This two-way flow control mechanism means both the master and slave can control the rate at which the information moves between master and slave.
  - The source generates the VALID signal to indicate when the address, data or control information is available.
  - The destination generates the READY signal to indicate that it can accept the information.
  - Transfer occurs only when both the VALID and READY signals are HIGH.

  - In Figure A3-2, the source presents the address, data or control information after T1 and asserts the VALID signal.
  - The destination asserts the READY signal after T2, and the source must keep its information stable until the transfer occurs at T3, when this assertion is recognized.
    
  - ![image](https://github.com/user-attachments/assets/3714a566-5626-46a9-8dd3-40710b4b6f09)
  - In Figure A3-3, the destination asserts READY, after T1, before the address, data or control information is valid,indicating that it can accept the information.
  - The source presents the information, and asserts VALID, after T2, and the transfer occurs at T3, when this assertion is recognized.
  - In this case, transfer occurs in a single cycle.
  - ![image](https://github.com/user-attachments/assets/52dfa5fd-51f1-457e-beef-eb3ec152dcad)

  - In Figure A3-4, both the source and destination happen to indicate, after T1, that they can transfer the address, data or control information.
  - In this case the transfer occurs at the rising clock edge when the assertion of both VALID and READY can be recognized.
  - This means the transfer occurs at T2.
  - ![image](https://github.com/user-attachments/assets/e2895977-b187-4b74-8294-6b3c34b22df5)

### 3.2.2 
    


 






