**AXI-Protocol**
 below feature for This development:
1) All basic Feature i.e. Handshaking, normal operation, multiple AXI channel (AXI parallel phases) , data strobing etc.
2) Burst based transaction
3) Multiple pipelined transaction (multiple outstanding addresses) 
4) Interleaving
5) out-of-order transaction
6) Slave as Memory
With different topologies like master VIP + slave VIP, master VIP + slave RTL, master RTL + slave VIP and both RTL with monitor/passive VIP.
-----------------------------------------------------------------------------------------------------------
**Reference : **
-----------------------------------------------------------------------------------------------------------
  https://github.com/marcoz001/axi-uvm/tree/master/rtl
  https://github.com/taichi-ishitani/tvip-axi/tree/master/src
  https://www.intel.com/content/www/us/en/docs/programmable/683364/18-1/lite-protocol-specification-support.html
  

-----------------------------------------------------------------------------------------------------------
**  Directory Stucture ** 
-----------------------------------------------------------------------------------------------------------
  AXI : RTL  : RTL design Files
        SIM  : tools command SCRIP
        ENV  :
        TEST :
        TOP  :
-----------------------------------------------------------------------------------------------------------
**Test Bench Architecture**
-----------------------------------------------------------------------------------------------------------


