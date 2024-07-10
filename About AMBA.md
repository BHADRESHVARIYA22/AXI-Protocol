## **What is AMBA protocol?**  
      - AMBA (Advanced Microcontroller Bus Architecture) is a set of specifications for on-chip communication protocols that  are widely used in   
        System-on-Chip (SoC) designs.  
      - The AMBA protocols are developed and licensed by ARM Holdings, which is a company known for designing microprocessors and 
        microcontrollers.

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
    AXI is the most advanced protocol with the highest number of channels, while AHB and APB are simpler protocols with fewer channels.  
    The number of channels used by each protocol determines the efficiency, performance, and complexity of the communication between   
    different components in a System-on-Chip (SoC).  
-----------------------------------------------------------------------------------------------------------------------------------------------
## **ADVANTAGES OF AXI OVER AHB PROTOCOL?**  
    1. AXI has 1 read address channel, 1 write address channel, 1 read data channel, 1 write data channel. 1  write response channel   
       That is all together it has 5 parallel channels.  
       Whereas AHB has 1 address channel, 1 read data channel, 1 write data channel.  
    2. AXI as native support for multiple outstanding transactions.   
    3. AXI supports transaction IDs. The user may issue multiple outstanding transactions per transaction ID.   
    4. User can insert a pipeline register anywhere in the path of any of the 5 channels, which helps in timing closure and help achieve higher operating frequency.
    
