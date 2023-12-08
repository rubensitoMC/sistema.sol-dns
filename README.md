# DNS Practice: Configuring Master and Slave DNS Servers for sistema.sol Domain

## Problem Description

### Network Configuration
All machines, both real and fictional, are on the network 192.168.57.0/24.

### Equipment Details

| Equipment           | FQDN                 | IP Address |
|---------------------|----------------------|------------|
| Linux (graphical)   | mercurio.sistema.sol | 192.168.57.101 |
| Debian (text)       | venus.sistema.sol    | 192.168.57.102 |
| Debian (text)       | tierra.sistema.sol   | 192.168.57.103 |
| Windows (graphical) | marte.sistema.sol    | 192.168.57.104 |

## DNS Configuration

### On Tierra

1. Set `dnssec-validation` option to `yes`.
2. Configure tierra as the default name server in `/etc/resolv.conf`.
3. Authorize the DNS server for the `sistema.sol` domain.
4. Allow recursive queries only from the networks 127.0.0.0/8 and 192.168.57.0/24.
5. Set tierra.sistema.sol as the master server for both forward and reverse zones.
6. Set a 2-hour time-to-live (TTL) for negative responses in both forward and reverse zones.
7. Forward unauthorized queries to the DNS server at 208.67.222.222.
8. Configure aliases: `ns1.sistema.sol` as an alias for tierra.sistema.sol.
9. Set `mail.sistema.sol` as an alias for marte.sistema.sol.
10. Configure marte.sistema.sol as the mail server for the sistema.sol domain.

### On Venus

1. Set `dnssec-validation` option to `yes`.
2. Configure venus as the default name server in `/etc/resolv.conf`.
3. Authorize the DNS server for the `sistema.sol` domain.
4. Allow recursive queries only from the networks 127.0.0.0/8 and 192.168.57.0/24.
5. Configure venus.sistema.sol as a slave server with tierra.sistema.sol as the master.
6. Set a 2-hour time-to-live (TTL) for negative responses in both forward and reverse zones.
7. Forward unauthorized queries to the DNS server at 208.67.222.222.
8. Configure aliases: `ns2.sistema.sol` as an alias for venus.sistema.sol.

## What have we done in this practice?

In this DNS configuration practice, we set up a master DNS server on the machine "Tierra" and a slave DNS server on the machine "Venus" for the `sistema.sol` domain. Key steps included enabling DNSSEC validation, configuring default name servers, authorizing the DNS servers, managing recursive queries, setting up master-slave relationships, handling negative responses, forwarding unauthorized queries, and creating aliases for simplifying DNS resolution. The practice also involved configuring a mail server on "Marte" and verifying the setup for successful DNS zone transfers.
