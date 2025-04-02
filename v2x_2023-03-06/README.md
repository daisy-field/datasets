# V2X 2023-03-06

This dataset was generated as a proof of concept for a master's thesis. It features
two V2X communication devices and is a capture of real network traffic. The two
hosts use the identifiers 2 and 5, as they are part of a bigger network with 
several additional machines. The following attacks are part of this dataset:

| Attack                                  | Machine | Start Time | End Time | IP Addresses                     | Protocols    |
|-----------------------------------------|---------|------------|----------|----------------------------------|--------------|
| Tool Installation                       | 5       | 12:34:17   | 12:40:28 | 192.168.213.86 and 185.0.0.0/8   | TCP and HTTP |
| SSH Brute Force (outgoing)              | 5       | 12:49:04   | 13:23:16 | 192.168.213.86 and 192.168.230.3 | TCP and SSH  |
| SSH Brute Force (incoming)              | 2       | 12:49:04   | 13:23:16 | 192.168.230.3 and 130.149.98.119 | TCP and SSH  |
| Privilege Escalation over SSH           | 5       | 13:25:37   | 13:31:11 | 192.168.213.86 and 192.168.230.3 | TCP and SSH  |
| Data Exfiltration over C2 Channel (SSH) | 2       | 13:25:27   | 13:31:11 | 192.168.230.3 and 130.149.98.119 | TCP and SSH  |

## Licensing

This dataset is licensed under the Creative commons Attribution International 
Version 4.0 [(CC BY 4.0)](https://github.com/daisy-field/datasets/blob/main/LICENSE.txt)