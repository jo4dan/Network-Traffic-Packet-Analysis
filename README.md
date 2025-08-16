# Network Traffic Packet Analysis

This repository contains packet-level details extracted from the provided `capture.pcapng` file. The dataset helps analyze network flows, identify protocols, and troubleshoot communication issues.

---

## 📂 File Details
- **File Name:** capture.pcapng
- **Format:** PCAP-NG (Packet Capture Next Generation)
- **Tool to Open:** Wireshark, Tshark, Scapy, Pyshark

---

## 📊 Packet Summary (Example)
| No. | Time (s) | Source        | Destination   | Protocol | Length | Info |
|-----|----------|--------------|--------------|----------|--------|------|
| 1   | 0.000001 | 192.168.1.2  | 192.168.1.1  | TCP      | 74     | SYN, Seq=0, Win=64240 |
| 2   | 0.000245 | 192.168.1.1  | 192.168.1.2  | TCP      | 74     | SYN, ACK, Seq=0, Ack=1 |
| 3   | 0.000532 | 192.168.1.2  | 192.168.1.1  | TCP      | 66     | ACK, Seq=1, Ack=1 |
| …   | …        | …            | …            | …        | …      | …    |

---

## 🔧 How to Extract Packet Details
Run the following commands depending on your environment:

### Using **tshark**
```bash
tshark -r capture.pcapng -T fields \
-e frame.number -e frame.time_relative \
-e ip.src -e ip.dst -e _ws.col.Protocol \
-e frame.len -e _ws.col.Info \
> packets.csv
