## **What is AMBA protocol?**  
  AMBA (Advanced Microcontroller Bus Architecture) is a set of specifications for on-chip communication protocols that  are widely used in System-on-Chip (SoC) designs.  
  The AMBA protocols are developed and licensed by ARM Holdings, which is a company known for designing microprocessors and microcontrollers.

**the main components of AMBA protocol?**  
    1. Advanced Peripheral Bus (APB)  
    2. Advanced High-performance Bus (AHB)  
    3. Advanced eXtensible Interface (AXI)  

------------------------------------------------------------------------------------------------------------------------------------------------
## **What are the difference between all 3 Protocol (AXI, AHB, APB)?**    
   - The AMBA protocols — AXI, AHB, and APB — are designed for on-chip communication between different components in a System-on-Chip (SoC).  
   - Here are some key differences between these protocols(Bandwidth, Performance, Features, Power Consumption, Complexity, Application)  

**Bandwidth**  
      - AXI is the highest bandwidth protocol among the three, providing up to 256-bit data transfers.  
      - AHB provides up to 64-bit data transfers  
      - APB provides up to 32-bit data transfers.  
**Performance**  
      - AXI is designed for high-performance applications and can support multiple outstanding transactions, allowing for efficient pipelining of data transfers.  
      - AHB is also a high-performance bus, but with a slightly lower performance than AXI.  
      - APB is designed for low-bandwidth, low-power applications.  
**Features:**  
      - AXI provides several advanced features like burst transactions, separate read and write channels, and support for multiple outstanding transactions.  
      - AHB also provides some of these features, but not all.  
      - APB is a simpler protocol and does not have these features.  
**Power consumption:**   
      - AXI and AHB are designed to be power-efficient, but APB is optimized for low-power consumption.  
**Complexity:**  
      - AXI is the most complex protocol among the three, with a higher number of signals and more advanced features.  
      - AHB is less complex than AXI, but more complex than APB, which is the simplest protocol.  
**Applications:**  
      - AXI is suitable for high-performance applications like video processing, networking, and graphics.  
      - AHB is used for mid-range applications like microcontrollers.  
      - APB is used for low-bandwidth applications like sensors and audio codecs.   
      
------------------------------------------------------------------------------------------------------------------------------------------------------
## **How many channels are there in AXI, AHB, and APB Protocols?**  
  The AMBA protocols — AXI (Advanced eXtensible Interface), AHB (Advanced High-performance Bus), and APB (Advanced Peripheral Bus) — use different numbers of channels for data transfer.  
  Here is a summary of the number of channels used by each protocol:  
  **AXI: The AXI protocol uses five independent channels for data transfer. They are:**   
    - Write Address channel  
    - Write Data channel  
    - Write Response channel  
    - Read Address channel  
    - Read Data channel  

  **AHB: The AHB protocol uses two independent channels for data transfer. They are:**  
    - Address/Data channel  
    - Control channel  

  **APB: The APB protocol uses two independent channels for data transfer. They are:**  
    - Address channel  
    - Data channel  

  In summary,
  AXI is the most advanced protocol with the highest number of channels, while AHB and APB are simpler protocols with fewer channels.The number of channels used by each protocol determines the efficiency, performance, and complexity of the communication between different components in a System-on-Chip (SoC).  
  
-----------------------------------------------------------------------------------------------------------------------------------------------
## **ADVANTAGES OF AXI OVER AHB PROTOCOL?**  
  1.AXI has 1 read address channel, 1 write address channel, 1 read data channel, 1 write data channel. 1  write response channel That is all together it has 5 parallel channels,Whereas AHB has 1 address channel, 1 read data channel, 1 write data channel.  
  2. AXI as native support for multiple outstanding transactions.   
  3. AXI supports transaction IDs. The user may issue multiple outstanding transactions per transaction ID.   
  4. User can insert a pipeline register anywhere in the path of any of the 5 channels, which helps in timing closure and help achieve higher operating frequency.

-------------------------------------------------------------------------------------------------------------------------------------------------
## **What do you mean by multiple outstanding transactions? Why is it useful?**  
  - Master initiates a transaction and doesn’t wait for it to complete(response to arrive) and initiates another transaction. So the first transaction is an outstanding transaction.  
  - AXI supports multiple outstanding transactions so an AXI master doesn’t have to wait for a transaction to complete to initiate a new one. So the performance is boosted.  

## **Difference between AHB and APB?**  
  - AHB is a high-performance bus that is used to connect high-speed modules like CPUs, DMA controllers, and memory controllers.  
  - APB, on the other hand, is a low-power, low-bandwidth bus that is used to connect slower peripherals like UARTs, timers, and GPIOs.  

## **the AXI protocol** 
  - The AXI (Advanced eXtensible Interface) protocol is a point-to-point interconnect protocol that is used to connect high-speed components such as processors, memories, and other peripherals in a system-on-chip (SoC) design.  
  - it is high speed, low latency protocol.
  - It is a widely used protocol in the semiconductor industry, as it provides a high-bandwidth and low-latency interconnect solution.  
    
  **the key features of the AXI protocol**  
  - Separate read and write channels, Support for burst transactions, allowing for efficient data transfer, Support for multiple data widths and transfer sizes.  

  **AXI burst**  
  - An AXI burst is a type of transaction that transfers a sequence of data between two components in a single transaction.  
  - Bursts are used to improve data transfer efficiency  

## **APB** :  
  - The Advanced Peripheral Bus (APB) is used for connecting low bandwidth peripherals.  
  - It is a simple non-pipelined protocol that can be used to communicate(read or write) from a bridge/master to a number of slaves through the shared bus.  
  - The reads and writes shares the same set of signals and no burst data transfers are supported.  
## **AHB**  
  - The Advanced High-performance Bus (AHB) is used for connecting components that need higher bandwidth on a shared bus.  
  - These could be a internal memory or an external memory interface, DMA , DSP etc but the shared bus would limit the number of agents.  
  - Similar to APB, this is a shared bus protocol for multiple masters and slaves, but higher bandwidth is possible through burst data transfers.  
  - **AHB-lite** protocol is a simplified version of AHB. The simplification comes with support for only a single master design and that removes need for any arbitration, retry, split transactions etc.  
## **AXI**:   
  - The Advanced Extensible interface (AXI) is useful for high bandwidth and low latency interconnects.  
  - This is a point to point interconnect and overcomes the limitations of a shared bus protocol in terms of number of agents that can be connected.  
  - The protocol also was an enhancement from AHB in terms of supporting multiple outstanding data transfers (pipe-lined), burst data transfers, separate read and write paths and supporting different bus widths.  
  - **AXI-lite** protocol is a simplified version of AXI and the simplification comes in terms of no support for burst data transfers.
Both AXI (Advanced extensible Interface) and AHB (Advanced High Performance Bus) are part of the AMBA (Advanced Microcontroller Bus Architecture) Bus which are targeted towards High Performance, High Bandwidth, and High-Frequency System Design but due to some extra features in AXI as compared to AHB makes it more usable protocol in ASIC Verification and on-chip communication.

## Difference Between AXI and AHB protocol 
1] AXI is a multi-channel bus with 5 independent channels like Write address channel, Read address channel, Write data channel, Read data channel, Write response channel (Read Response is sent along with the Read data) while AHB is a single channel bus.  

2] Because of the proper ordering model, AXI supports for multiple outstanding transactions while AHB support for Single outstanding transaction per bus master.  

3] AXI support for out of order transaction completion with masters having different ID tag is allowed to complete in any order while AHB does not support any out of order transaction completion.  

4] The minimum address space assigned for a single slave in AXI is 4 kb while the address space assigned for a slave in AHB is 1 kb.  

5] AXI support Full-duplex mode of communication because of multiple and independent channels while AHB does not support Full-duplex mode.  

6] AXI support system low power acknowledgement with the introduction of low power request signal csysack which enable AXI to operate in low power mode while AHB doesn't support low power request acknowledgement.  

7] Since each channel is independent in AXI, there is no requirement to have a fixed relationship between the channel concerning data transfer which makes it easier to add Register slices and because of this AXI can operate in a higher frequency of operation as compared to AHB.  

8] The features like unaligned data transfer using strobe and byte invariance are supported in AXI while AHB wouldn't support any of these features.  

9] QOS and Write Data Interleaving are supported in AXI while no QOS and Write Data interleaving features are supported in AHB.  

10] There are additional Signalling mechanism like AxRegion (Single Interface on a slave to be used for multiple logical interfaces) , AxUser (User Defined Signalling Mechanism) are present in AXI as compared to AHB.  

11] Early Burst termination feature is absent in AXI but is present in AHB.  

12] Semaphore mode of Operation is present in AXI with the help of Exclusive Access support while this is absent in AHB.     
    
