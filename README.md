# Traffic Capture & Threat Visualization — Lab

**Environment:** VMWare (Host-Only), Kali (attacker) + Ubuntu (victim)  
**Tools:** tcpdump, nmap, Wireshark

## Summary
Captured controlled traffic in an isolated VM lab. Generated ping and nmap SYN scan from attacker VM and analyzed the PCAP.

## Artifacts
- capture_lab.pcap
- protocol_hierarchy.png
- io_graph.png
- conversation.png
- packet_detail_syn.png

## Findings
- SYN spikes observed during the SYN scan — typical reconnaissance signature.
- Majority UDP traffic due to DNS/mDNS.
- Repeated SYN retransmissions to dst port 53 without completing handshake.

---

## Screenshots & captions

<figure>
  <img src="1.png" alt="Protocol Hierarchy" width="800">
  <figcaption><strong>Figure 1:</strong> Protocol Hierarchy — heavy UDP (DNS/mDNS) and IPv4 traffic.</figcaption>
</figure>

<figure>
  <img src="2.png" alt="I/O Graph" width="800">
  <figcaption><strong>Figure 2:</strong> I/O Graph showing SYN and ICMP spikes during scan/ping activity.</figcaption>
</figure>

<figure>
  <img src="3.png" alt="Conversations" width="800">
  <figcaption><strong>Figure 3:</strong> Conversations — attacker (192.168.56.128) -> victim (192.168.56.1) top talker.</figcaption>
</figure>

<figure>
  <img src="4.png" alt="SYN Packet Details" width="800">
  <figcaption><strong>Figure 4:</strong> SYN packets with retransmissions to dst port 53 — indicates scanning attempts.</figcaption>
</figure>
