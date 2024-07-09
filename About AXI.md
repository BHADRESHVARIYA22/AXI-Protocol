AXI  protocol part of AMBA family, AMBA stands for Advanced Microcontroller Bus Architecture.

The AXI protocol:
 • is suitable for high-bandwidth and low-latency designs
 • provides high-frequency operation without using complex bridges
 • meets the interface requirements of a wide range of components
 • is suitable for memory controllers with high initial access latency
 • provides flexibility in the implementation of interconnect architectures
 • is backward-compatible with existing AHB and APB interfaces.

The key features of the AXI protocol are:
 • separate address/control and data phases
 • support for unaligned data transfers, using byte strobes
 • uses burst-based transactions with only the start address issued
 • separate read and write data channels, that can provide low-cost Direct Memory Access (DMA)
 • support for issuing multiple outstanding addresses
 • support for out-of-order transaction completion
 • permits easy addition of register stages to provide timing closure.

AXI Architecture


