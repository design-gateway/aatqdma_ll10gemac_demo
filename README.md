# FPGA-based HLS (High-Level-Synthesis) Accelerated Algorithmic Trading Demo

## Overview
This repository provides detailed instructions for configuring the Alveo Accelerator Card and setting up the test environment to run the customized Accelerated Algorithmic Trading (AAT) demo from Design Gateway – **DG AAT QDMA demo**.

![Block Diagram](https://github.com/design-gateway/aatqdma_ll10gemac_demo/blob/main/docs/AATQDMA_BlockDiagram.png)

## Introduction
Software-based trading applications typically respond to market changes in microseconds or more, even with the fastest Smart Network Card. In contrast, FPGA-based hardware solutions reduce response times to less than 900 nanoseconds or much lower—offering a massive advantage in today's high-stakes trading environments. In high-frequency trading, every nanosecond counts; staying behind means falling behind.

## Why Choose FPGA-based HLS for High-Frequency Trading?

1. **FPGA-based HLS (High-Level Synthesis) for Software Developers**
   - HLS-based example designs use C/C++, languages familiar to most software developers. Transitioning to hardware programming might take 6–18 months of learning, but the long-term benefits in speed and cost-efficiency make it worthwhile.

2. **Cost-Effective FPGA Accelerator Card**
   - The X3522PV Card from AMD offers unmatched performance at a fraction of the cost of ultra-fast FPGA cards, some of which can exceed $100K.

3. **Proven Success in Real-World Trading**
   - The low-latency 10G EMAC IP core has already been validated in live trading environments, such as the Stock Exchange of Thailand (SET), and supports key protocols, including NASDAQ.

## Comparison: FPGA-based HLS vs. Software & Smart NIC for High Frquency Trading

| Feature                        | FPGA-based HLS          | Software & Smart NIC |
|--------------------------------|-------------------------|----------------------|
| Latency                       | Sub-900 NanoSeconds     | Multi MicroSeconds   |
| Win opportunity               | High                    | Low                  |
| Cost-Effectiveness            | Best in Class(X3522PV)  | Low                  |
| Ease of Development           | Moderate(HLS)           | High(Software)       |

## About This Demo
This demo is a modified version of AMD’s proprietary Accelerated Algorithmic Trading (AAT) demo, known as the **AAT QDMA demo**. It is specifically designed to achieve lower latency by utilizing the **LL10GEMAC-IP** from Design Gateway (DG).

### Resources
- Detailed information about the DG AAT QDMA demo: [Reference Design Document](https://dgway.com/products/IP/Lowlatency-IP/ll10gemac-ip-aat-qdma-refdesign-amd/)
- Latency details for the LL10GEMAC-IP: [Datasheet](https://dgway.com/products/IP/Lowlatency-IP/dg_ll10gemacip_data_sheet_xilinx_en/)

### Test Environment
The demo operates on the Alveo Accelerator Card and demonstrates performance over a 10G Ethernet connection. Here are the supported configurations and components:

#### Supported Alveo Cards
- **U250, U55C**: Two QSFP28 ports, supporting up to four 10G Ethernet channels per QSFP28.
- **U50**: One QSFP28 port, supporting up to four 10G Ethernet channels.
- **X3522**: Two DSFP28 ports, supporting up to two 10G Ethernet channels per DSFP28.

#### Required 10G Ethernet Channels
1. **Market Data Transmission**: Transmits sample market data using the UDP protocol.
2. **Order Transmission**: Handles order data transmission using FIX over TCP.

### Setup Components
1. **Host System for Alveo Accelerator Card**
   - Turnkey accelerator system (TKAS-D2101). Detailed specifications: [DG Solutions](https://dgway.com/solutions.html)
   - Vivado Design Suite installed on the host system to program the Alveo card.

2. **10G Ethernet Cables**
   - U50/U250/U55C: [QSFP+ to 4 SFP+ Breakout Cable](https://www.sfpcables.com/5-meter-40g-qsfp-to-4-sfp-aoc-cable-om3-mmf-cisco-oem-compatible)
   - X3522: [2xSFP+ Active Optical Cable (AOC)](https://www.10gtek.com/10gsfp+aoc)

3. **Programming Cables**
   - U250/U55C: Micro-USB cable.
   - U50: Alveo programming cable.
   - X3522: Alveo Debug Kit (ADK2).

4. **Target System Configuration**
   - **Operating System**: Ubuntu 20.04 LTS Server.
   - **Market Data**: Sample file (cme_input_arb.pcap).
   - **Packet Replay**: “tcpreplay” package for transmitting market data.
   - **Ethernet Ports**: Two 10G Ethernet ports using [Intel X710-DA2 Adapters](https://ark.intel.com/content/www/us/en/ark/products/83964/intel-ethernet-converged-network-adapter-x710da2.html).

### Running the Demo
1. Connect the required hardware components.
2. Transmit market data using the “tcpreplay” tool.
3. Monitor order reception by opening a TCP port on the target system.
4. Initiate the demo on the Alveo accelerator by executing the “`aat_qdma_exe`” application.

## Demo Download
1. Demo Configuration files for Alveo Card: Available in the **config** folder.
2. Example sample data to run with Demo on X3522PV Card: Request via the [demo inquiry form](https://dgway.com/download/download_form.html?d=AATQDMA_LL10GEMAC_X3522.zip).
3. For more information, please visit Design Gateway’s Low Latency IP Cores: [Visit Here](https://dgway.com/Lowlatency-IP_X_E.html).

## Watch the Demo on YouTube

[![Watch on YouTube](https://img.youtube.com/vi/booe3aAAYwk/0.jpg)](https://youtu.be/booe3aAAYwk)

---

Feel free to explore and contribute to this repository for further optimizations and insights into FPGA-based trading acceleration.
