# DSFIDS24

This dataset is a live capture of eight extended road-side units (eRSU). The dataset and
attacks were collected on real infrastructure. It features captures of eight 
multi-access edge computing (MEC) units in a distributed network. It was captured on
the 22nd of July 2024, starting on the 21st at 20:00 CEST and ending on the 22nd at
20:00 CEST. The dataset is split into the eight hosts. Each host contains CSV files with
100.000 packets per file.

## Network Layout

<img src="DSFIDS24/graphics/eRSU.png" alt="drawing" width="400"/>

The graphic above shows the network of a single eRSU. The network features a road-side 
unit (RSU), which is a vehicle to everything (V2X) communication device used to 
communicate with vehicles (for autonomous driving) and the internet. The location 
additionally features sensors, like camera and Lidar sensors and a MEC unit. The 
internal network uses the 192.168.213.0/22 address space.

<img src="DSFIDS24/graphics/locations.png" alt="drawing" width="400"/>

For the dataset eight eRSUs were used. In the graphic above, the network layout of most
of the infrastructure is shown. The eRSUs use a VPN (dotted line) to communicate with an
office network. The IP space for the VPN is 10.1.1.0/24. An additional VPN is present in 
the dataset, but not used for any attacks. Its IP space is 192.168.100.0/24. The 
infected machine is the machine used by the adversary to attack the systems initially.
As the attack scenario progresses, the adversary moves into the network.

## Attacks

The dataset features multiple attacks. They were labeled using the MITRE ATT@CK® Matrix
in Enterprise Edition in Version 15. Each Label has the following structure:

extra-information:TA0000-T0000;TA0000-T0000

The label can contain any number of TA0000-T0000 pairs separated using semicolon. 
The TA0000 is the identifier of a tactic in the MITRE ATT@CK Matrix, while the T0000
is a technique under the tactic. If multiple techniques fall into the same tactic, they 
can be written as TA0000-T0000-T0000. In some cases extra information is provided to 
specify the type of attack. This extra information is provided at the start of the 
label and separated from the tactic-technique pairs using a double point. The exception
is the label "benign", which denotes the normal traffic. The following labels are 
present in the dataset. All tactics can be found 
[here](https://attack.mitre.org/versions/v15/tactics/), all techniques 
[here](https://attack.mitre.org/versions/v15/techniques/).

| Label                                               | Tactic and Technique                                                                                                      | Description                                                                |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| benign                                              |                                                                                                                           | Benign traffic                                                             |
| TA0043-T1595                                        | Reconnaissance - Active Scanning                                                                                          | Port Scan from infected machine                                            |
| SSH-Brute-Force:TA0006-T1110                        | Credential Access - Brute Force                                                                                           | SSH Brute Force                                                            |
| TA0001-T1078;TA0007-T1083;TA0010-T1041              | Initial Access - Valid Accounts; Discovery - File and Directory Discovery; Exfiltration - Exfiltration Over C2 Channel    | Initial Access to network and commands for searching and exfiltrating data |
| TA0001-T1078;TA0007-T1083;TA0010-T1041;TA0004-T1078 | Same as the line above; Privilege Escalation - Valid Accounts                                                             | Continuation of above attack with additional privilege escalation          |
| TA0008-T1021;TA0007-T1083;TA0010-T1041              | Lateral Movement - Remote Services; Discovery - File and Directory Discovery; Exfiltration - Exfiltration over C2 Channel | Commands for searching and exfiltrating data on remote machine             |
| TA0008-T1021                                        | Lateral Movement - Remote Services                                                                                        | Connection to machines (SSH connections and tunnels)                       |
| Outgoing-Portscan:TA0007-T1046-T1018                | Discovery - Network Service Discovery - Remote System Discovery                                                           | Port scan executed on this machine                                         |
| Incoming-Portscan:TA0007-T1046-T1018                | Discovery - Network Service Discovery - Remote System Discovery                                                           | Port scan targeting this machine                                           |
| Portscan-Tool-Install:TA0042-T1608                  | Resource Development - Stage Capabilities                                                                                 | Installation of port scan tool                                             |
| Brute-Force-Tool-Install:TA0042-T1608               | Resource Development - Stage Capabilities                                                                                 | Installation of brute force tool                                           |
| DoS-Tool-Install:TA0042-T1608                       | Resource Development - Stage Capabilities                                                                                 | Installation of Denial of Service tool                                     |
| TCP-Syn-Flood:TA0040-T1498                          | Impact - Network Denial of Service                                                                                        | TCP SYN Flood DoS attack                                                   |
| ICMP-Flood:TA0040-T1498                             | Impact - Network Denial of Service                                                                                        | ICMP Flood DoS attack                                                      |

As each packet can contain multiple labels, it is recommended to split the labels by 
tactic-technique (at the semicolons). Additionally, different labels are used for the
same attacks, as the labels provide additional context to the attack. The following 
labels/tactic-technique-pairs should be grouped. 

- Group 1:
  - TA0043-T1595 
  - Incoming-Portscan:TA0007-T1046-T1018
    - Both labels are an incoming portscan. The first label is just used for reconnaissance
- Group 2:
  - TA0001-T1078
  - TA0008-T1021
    - Both are SSH connections. The first is just the initial connection instead of a following one
- Group 3:
  - Portscan-Tool-Install:TA0042-T1608
  - Brute-Force-Tool-Install:TA0042-T1608
  - DoS-Tool-Install:TA0042-T1608
    - These already use the same tactic-technique pair. The traffic is mostly identical and can be considered the same attack

Apart from the attacks port scan, SSH brute force, TCP SYN flood DoS, and ICMP Flood DoS,
most attack traffic uses SSH. The following table shows every attack in the dataset. All
times are from the 22nd of July 2024 in CEST timezone.

| Timestamp    | Description                                                                                                                                              |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| 02:18:28.045 | Port scan of 10.1.1.0/24 from infected machine                                                                                                           |
| 03:04:21.449 | SSH Brute Force attack targeting Host-2 from infected machine                                                                                            |
| 06:37:34.370 | Initial Access to Host-2 using SSH from infected machine. Execution of File and Directory Discovery attack.                                              |
| 06:38:46.570 | Execution of Exfiltration and Privilege Escalation attacks on Host-2                                                                                     |
| 07:04:06.157 | SSH connection to Host-2 from infected machine                                                                                                           |
| 07:04:23.289 | Installation of port scan tool on Host-2                                                                                                                 |
| 07:07:54.030 | Port scan targeting 192.168.213.0/22 from Host-2                                                                                                         |
| 07:12:01.437 | Port scan targeting 10.1.1.129/25 from Host-2                                                                                                            |
| 08:14:08.817 | SSH connection to Host-2 from infected machine                                                                                                           |
| 08:14:16.229 | Installation of brute force tool on Host-2                                                                                                               |
| 08:18:23.687 | Download of repository containing password files on Host-2                                                                                               |
| 08:31:57.365 | Unpacking of repository on Host-2                                                                                                                        |
| 08:36:04.745 | SSH Brute Force attack targeting Host-4 from Host-2                                                                                                      |
| 10:09:12.191 | SSH connection to Host-4 using SSH tunnel over Host-2 from the infected machine. Execution of File and Directory Discovery attacks and Data Exfiltration |
| 10:12:26.063 | Port scan targeting 10.1.1.129/25 from Host-4                                                                                                            |
| 10:15:32.876 | Port scan targeting 192.168.213.0/22 from Host-4                                                                                                         |
| 11:58:09.680 | SSH connection to Host-6 using SSH Tunnel over Host-4 and SSH Tunnel over Host-2 from the infected machine                                               |
| 11:58:31.192 | Port scan targeting 192.168.213.0/22 and 10.1.1.129/25 from Host-6                                                                                       |
| 12:01:52.706 | Execution of Persistence attack on Host-6                                                                                                                |
| 14:07:37.220 | SSH connection to Host-3 from infected machine                                                                                                           |
| 14:07:51.361 | Installation of Denial of Service tool on Host-3                                                                                                         |
| 14:10:55.141 | TCP SYN Flood DoS attack from Host-3 targeting Host-6                                                                                                    |
| 16:47:42.489 | SSH connection to Host-5 from intected machine                                                                                                           |
| 16:48:09.940 | Installation of Denial of Service tool on Host-5                                                                                                         |
| 16:50:38.078 | ICMP Flood DoS attack from Host-5 targeting Host-4                                                                                                       |

Host-1, Host-7, and Host-8 were never targeted by any attack other than the port scans.

## Licensing

This dataset is licensed under the Creative commons Attribution International 
Version 4.0 [(CC BY 4.0)](https://github.com/daisy-field/datasets/blob/main/LICENSE.txt)