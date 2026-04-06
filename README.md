# 📡 Packet Analysis with Wireshark — Complete Learning Series

> **3-Document Technical Reference Series** | From Beginner to Expert-Level Mastery  
> Covering TCP/UDP · Fibre Channel (FC) & FCoE · iSCSI  

---

## 📚 About This Series

This repository contains three comprehensive, self-contained technical learning guides built from a combination of hands-on packet trace training (covering TCP/UDP, FC/FCoE, and iSCSI traces across a 5-day intensive course) and deep independent research into protocol specifications, RFC documentation, and real-world capture analysis.

Each document is structured to take a reader from **zero knowledge** to **expert-level diagnostic capability** on the respective protocol, following an identical 6-part structure across all three volumes for consistency and cross-referencing ease.

---

## 📂 Documents in This Series

| # | Document | Protocol Focus | Key Topics |
|---|----------|---------------|------------|
| **Doc 1** | `TCP_UDP_Wireshark_Guide.docx` | TCP & UDP | 3-way handshake, retransmissions, zero windows, flow control, RST analysis, UDP behaviour |
| **Doc 2** | `FC_FCoE_Wireshark_Guide.docx` | Fibre Channel & FCoE | FLOGI/PLOGI/PRLI login sequence, FCP SCSI IO, zoning, RSCN storms, PFC/DCB |
| **Doc 3** | `iSCSI_Wireshark_Guide.docx` | iSCSI | PDU types, CHAP auth, ITT tracking, R2T/Data-Out, SCSI errors, TCP-iSCSI interaction |

> **Video Resources & YouTube Learning Roadmap for all three documents are consolidated in Doc 3 — Appendix A.**

---

## 🗂️ Document Structure (Identical Across All 3)

Every document follows the same 6-part structure:

```
Part 1 — Wireshark Fundamentals
         Interface, capture vs display filters, coloring rules,
         column customisation, stream following, IO graphs, Expert Info

Part 2 — Networking & Storage Foundations
         OSI model application, frame/packet structure,
         protocol-specific addressing and topology

Part 3 — Protocol Deep Dive
         Every header field, every flag bit, every PDU type —
         with normal values, abnormal indicators, and Wireshark field names

Part 4 — Packet Identification & Multi-Device Tracing
         Flow identifiers (5-tuple / Exchange IDs / ITT),
         multi-point captures, correlation across devices

Part 5 — Live Trace Walkthroughs
         Annotated packet-by-packet traces for every major scenario:
         normal flows, errors, retransmissions, login failures, performance issues

Part 6 — Troubleshooting Patterns & Expert Diagnosis
         Failure signatures, performance baselining, latency analysis,
         filter cheat sheets, remediation steps
```

---

## 🔍 What Each Document Covers

### Document 1 — TCP/UDP Packet Analysis

- Complete Wireshark interface walkthrough with all panels, toolbars, and menus
- BPF capture filter syntax vs Wireshark display filter syntax (with tables of examples)
- Full TCP header — all fields, all 9 flag bits, with Wireshark field name cross-reference
- TCP 3-way handshake, sequence/acknowledgment mechanics, full-duplex data transfer
- Flow control, windowing, bandwidth-delay product, Window Scale option (RFC 7323)
- Retransmission types: RTO, Fast Retransmit, Spurious; SACK selective recovery
- Zero window anatomy, probing, and root cause analysis
- Connection teardown (graceful FIN, abrupt RST), TIME_WAIT state
- TCP options: MSS, SACK, Timestamps, Window Scale — negotiation and impact
- UDP header, stateless behaviour, use cases (DNS, DHCP, NTP, QUIC, RTP)
- 5-tuple conversation identification, multi-point capture correlation
- 6 annotated live traces: HTTP session, retransmission recovery, zero window, RST, DNS, WAN degradation

### Document 2 — Fibre Channel (FC) & FCoE Packet Analysis

- Wireshark configuration for FC/FCoE dissectors and FCoE EtherType 0x8906
- SAN fundamentals: block vs file storage, FC vs FCoE vs iSCSI decision matrix
- FC layer model (FC-0 through FC-4) mapped to Wireshark dissectors
- Port types: N_Port, F_Port, E_Port, G_Port, VN_Port, NL_Port — roles and login implications
- Addressing: WWN, WWNN, WWPN, FC-ID (domain/area/port breakdown), well-known addresses
- FCoE encapsulation with full byte-offset layout, SOF/EOF delimiter encoding
- Data Center Bridging: PFC (IEEE 802.1Qbb), ETS (802.1Qaz), DCBX via LLDP
- Complete FC login sequence: FIP discovery → FLOGI → PLOGI → PRLI → FCP IO → LOGO
- FLOGI/PLOGI/PRLI payload field tables with LS_RJT reason codes
- FCP: FCP_CMND, FCP_DATA, FCP_XFER_RDY, FCP_RSP — all fields and SCSI status codes
- Exchange mechanics: OX-ID, RX-ID, SEQ_ID, SEQ_CNT — the FC transaction identifier
- Zoning: hard vs soft, WWN vs port, Wireshark identification of zoning violations
- RSCN, ADISC, SCR — fabric services and state change notification
- 7 annotated live traces: full login, FLOGI busy, PLOGI zoning rejection, FCP read, FCP write, RSCN storm, PFC PAUSE

### Document 3 — iSCSI Packet Analysis

- Three-layer Wireshark configuration (TCP reassembly, iSCSI reassembly, SCSI sub-dissector)
- iSCSI over TCP — the complete encapsulation stack with byte-level accounting
- IQN naming format, TSIH/ISID/CID session identifiers, ERL error recovery levels
- CHAP and Mutual CHAP authentication mechanism and Wireshark-visible fields
- Complete PDU structure: BHS (all 48 bytes), AHS, Header Digest, Data Digest (CRC32C)
- All 17 iSCSI opcode types with direction, purpose, and every BHS field
- Login phase state machine: Security Negotiation → Operational Negotiation → Full Feature Phase
- Negotiation parameters: MaxBurstLength, FirstBurstLength, InitialR2T, ImmediateData, ErrorRecoveryLevel
- ITT (Initiator Task Tag) — lifecycle, tracking, and Wireshark filter patterns
- Write IO data flow: Immediate Data → Unsolicited Data-Out → R2T-solicited Data-Out
- Task Management PDUs: all 8 function codes and when they appear in captures
- CmdSN / StatSN / ExpCmdSN / MaxCmdSN sequencing and window analysis
- TCP impact on iSCSI: retransmissions, zero windows, RST — how each manifests as IO failure
- 9 annotated live traces: full login with CHAP, 3 login failure scenarios, READ IO, WRITE IO (both modes), CHECK CONDITION with sense data, NopIn RTT, logout, TCP retransmission impact

---

## 🎯 Key Reference Tables (Across the Series)

| Reference | Location |
|-----------|----------|
| Wireshark shortcut keys | Doc 1, Appendix |
| TCP option types (MSS/SACK/WSCALE/TSopt) | Doc 1, Section 3.10 |
| SCSI status codes | Doc 2, Section 3.14 / Doc 3, Section 6.3 |
| FC ELS command code table | Doc 2, Appendix A |
| SCSI opcode reference | Doc 2, Appendix B |
| iSCSI opcode reference | Doc 3, Section 3.3 |
| iSCSI Login Status Code reference | Doc 3, Section 6.2 |
| SCSI Sense Key / ASC / ASCQ reference | Doc 3, Section 6.3 |
| Display filter cheat sheets | Doc 1 §6.5 / Doc 2 §6.7 / Doc 3 §6.7 |

---

## 📺 Video Learning Resources

A curated YouTube resource guide covering all three documents — with **35+ videos** across beginner foundations and expert deep-dives — is included in **Doc 3, Appendix A**, organised as:

- **A.1** — TCP/UDP resources (NetworkChuck, Chris Greer, Practical Networking, Professor Messer, Sharkfest)
- **A.2** — FC/FCoE resources (CBTNuggets, Cisco Learning, NetApp, Brocade, Sharkfest)  
- **A.3** — iSCSI resources (Chris Greer, Tony Fortunato, Laura Chappell, Learn Linux TV, NetApp)
- **A.4** — 12-week combined study roadmap with lab exercises

---

## 🛠️ Tools Referenced

| Tool | Purpose |
|------|---------|
| **Wireshark** (GUI) | Primary capture and analysis tool |
| **tshark** | CLI capture, field extraction, automated analysis |
| **editcap** | Split, trim, and anonymise capture files |
| **mergecap** | Merge multi-point captures chronologically |
| **dumpcap** | Lightweight capture daemon (no GUI overhead) |
| **tcpdump** | Unix capture for remote/headless environments |

---

## 📋 Prerequisites

| Document | Assumed Knowledge |
|----------|------------------|
| Doc 1 (TCP/UDP) | Basic networking concepts (IP, ports). No Wireshark experience required. |
| Doc 2 (FC/FCoE) | Doc 1 recommended. Familiarity with enterprise data centre concepts helpful. |
| Doc 3 (iSCSI) | Doc 1 required (TCP knowledge essential). Doc 2 helpful for SCSI context. |

---

## 📖 External References

- RFC 793 — Transmission Control Protocol
- RFC 768 — User Datagram Protocol  
- RFC 7323 — TCP Extensions for High Performance
- RFC 5681 — TCP Congestion Control
- RFC 3720 / RFC 7143 — iSCSI Protocol
- ANSI T11 FC-BB-5 — Fibre Channel over Ethernet
- IEEE 802.1Qbb — Priority Flow Control
- IEEE 802.1Qaz — Enhanced Transmission Selection
- [Wireshark Official Documentation](https://www.wireshark.org/docs/)
- [Wireshark Wiki](https://wiki.wireshark.org/)

---

## 👤 Author Notes

These guides were produced from a combination of live packet trace training sessions (5-day intensive covering all three protocol families) supplemented by deep independent research into protocol specifications and production capture analysis. All trace examples are representative of real-world scenarios encountered in enterprise network and storage environments.

---

*Part of a 3-document series. All documents are self-contained and can be read independently.*
