# Enterprise Campus Network Design & Implementation

A two-building enterprise campus network built and tested in Cisco Packet Tracer: three-tier design with routed core, redundant gateways, dual-stack OSPF, DHCP, PAT/static NAT with two ISPs, Layer 2 security and a wireless controller.

**Full report:** [`docs/Enterprise_Campus_Network_Report.pdf`](docs/Enterprise_Campus_Network_Report.pdf) (22 pages: design, addressing, configuration, 10 test cases, limitations)

## Highlights
- Core / distribution / access design across Building A (headquarters) and Building B (production)
- Routed LACP between the core switches and routed /30 links to every distribution switch
- OSPFv2 and OSPFv3 (area 0), default route originated by the CE router, floating static defaults to two ISPs
- HSRPv2 with Rapid-PVST+ roots aligned to the active gateway
- DHCP on the CE router with relay from the distribution layer; WLC with Management and Guest WLANs
- Port security, BPDU guard, DHCP snooping, Dynamic ARP Inspection, SSH-only management with a VTY ACL
- NAT: PAT for internal users, static NAT publishing the web server over HTTPS; inbound ACL on the WAN links

## Repository layout
| Path | Content |
|---|---|
| `docs/` | Final report (PDF) |
| `configs/` | Running configurations of the lab devices (secret hashes redacted) |
| `lab/` | Packet Tracer project file (`.pkt`) |

## Running the lab
Open the `.pkt` file in Cisco Packet Tracer (version stated in the report). Lab credentials are in the report; the configs here have the hashes removed.

## Known limitations
Documented in section 8 of the report (guest isolation, PAT on both ISPs, HSRP timers, Packet Tracer limits).

## Author
Yannick HUE
