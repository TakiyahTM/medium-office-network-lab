# Medium Office Network Lab

I built this Cisco Packet Tracer project to practise setting up an office network with separate departments, shared services and controlled access. It includes a simulated ISP, a public website in a DMZ, and an internal office network.

After building a network with physical equipment in a controlled environment, I wanted to explore DMZs, PAT and the restrictions needed when connecting an office to the internet.

## What I configured

- VLANs for Staff, Finance, IT, printers, guests, servers and management.
- Inter-VLAN routing, static routes, DHCP relay and DNS.
- Outbound PAT and a static TCP port mapping for the public website.
- ACLs for department access, guest isolation and server restrictions.
- SSH management restricted to the admin PC, plus unused office ports shut down in VLAN 999.

## Testing

I checked allowed and blocked connections: staff could ping the office printer but not the Finance printer, while Finance could ping both. Guests could browse the simulated internet while direct intranet and DMZ access was blocked. External users could load the public website while ping to the edge was blocked. I also tested admin SSH, restricted non-admin access and server-to-admin traffic.

For the blocked staff printer test, the matching ACL deny counter increased from **39 to 47**. The PDF includes addressing tables, configuration explanations, troubleshooting notes and a linked test-results table. A glossary links key terms to their use in the lab.

## Project files

- [Project documentation](docs/Medium%20Office%20Network%20Documentation.pdf)
- [Packet Tracer project](packet-tracer/Documentation.pkt) — open in Cisco Packet Tracer to explore the lab.
- [Device configurations](configs/) — seven saved router and switch running configurations.

## What I learned

The main faults I worked through were an incorrect NAT inside/outside setting and the admin PC being connected to the wrong switch port. They reminded me to check the physical connection, addressing and configuration before assuming an ACL was the problem.

This is a simulated learning lab using HTTP and stateless ACLs. The local account is `netadmin`, and the login and enable secrets are `cisco` for lab use only. Printer tests check ping reachability, not actual printing.

I plan to keep expanding this project as I learn more and test different ways to secure the network.

*Built and documented by Takiyah.*
