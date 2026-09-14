# My-first-CRH-project-using-NMAP-to-scan-for-METASPLOITABLE-


1. Introduction 

Purpose of the Assessment 

The purpose of this assessment is to identify open ports, running services, service versions, and potential security weaknesses on the target system (Metasploitable 2) in a controlled laboratory environment as part of a CEH training exercise. 

Scope 

The assessment was limited to the Metasploitable 2 virtual machine (IP: 192.168.0.7) running in an isolated lab network. No production or unauthorized systems were involved. 

Authorization Statement 

This assessment was conducted strictly for educational purposes as part of a Certified Ethical Hacker (CEH) assignment. All testing was performed on authorized systems (Metasploitable 2) within an isolated laboratory environment. No unauthorized systems were scanned or assessed. 

2. Methodology 

The assessment followed a structured approach consisting of host discovery, port scanning, service and version identification, vulnerability correlation based on identified versions, and risk rating. All activities were performed in an isolated lab environment using authorized tools. 

3. Findings 

3.1 Open Ports 

The following ports were identified as open on the target system (192.168.0.7): 

Port 

Protocol 

State 

Notes 

21 

tcp 

open 

FTP 

22 

tcp 

open 

SSH 

23 

tcp 

open 

Telnet 

25 

tcp 

open 

SMTP 

53 

tcp 

open 

DNS 

80 

tcp 

open 

HTTP 

111 

tcp 

open 

RPCBind 

139 

tcp 

open 

NetBIOS / Samba 

445 

tcp 

open 

NetBIOS / Samba 

512 

tcp 

open 

Rexec 

513 

tcp 

open 

Login 

514 

tcp 

open 

Shell / tcpwrapped 

1099 

tcp 

open 

Java RMI 

1524 

tcp 

open 

Bindshell 

2049 

tcp 

open 

NFS 

2121 

tcp 

open 

FTP (ProFTPD) 

3306 

tcp 

open 

MySQL 

5432 

tcp 

open 

PostgreSQL 

5900 

tcp 

open 

VNC 

6000 

tcp 

open 

X11 

6667 

tcp 

open 

IRC 

8009 

tcp 

open 

AJP13 

8180 

tcp 

open 

HTTP (Tomcat) 

3.2 Running Services 

The following services were detected as running on the target: 

Port 

Service Name 

Description 

21 

ftp 

File Transfer Protocol 

22 

ssh 

Secure Shell 

23 

telnet 

Telnet remote access 

25 

smtp 

Simple Mail Transfer Protocol 

53 

domain 

DNS service 

80 

http 

Web server 

111 

rpcbind 

RPC port mapper 

139 / 445 

netbios-ssn 

Samba file/print sharing 

512 

exec 

Remote execution service 

1099 

java-rmi 

Java Remote Method Invocation 

1524 

bindshell 

Bind shell service 

2049 

nfs 

Network File System 

2121 

ftp 

ProFTPD FTP service 

3306 

mysql 

MySQL database 

5432 

postgresql 

PostgreSQL database 

5900 

vnc 

Virtual Network Computing 

6667 

irc 

Internet Relay Chat 

8009 

ajp13 

Apache JServ Protocol 

8180 

http 

Apache Tomcat web server 

3.3 Service Versions 

Service version information identified during the assessment: 

Port 

Service 

Version Detected 

21 

ftp 

vsftpd 2.3.4 

22 

ssh 

OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0) 

23 

telnet 

Linux telnetd 

25 

smtp 

Postfix smtpd 

53 

domain 

ISC BIND 9.4.2 

80 

http 

Apache httpd 2.2.8 ((Ubuntu) DAV/2) 

111 

rpcbind 

2 (RPC #100000) 

139/445 

netbios-ssn 

Samba smbd 3.X – 4.X (workgroup: WORKGROUP) 

512 

exec 

netkit-rsh rexecd 

1099 

java-rmi 

GNU Classpath grmiregistry 

1524 

bindshell 

Metasploitable root shell 

2049 

nfs 

2–4 (RPC #100003) 

2121 

ftp 

ProFTPD 1.3.1 

3306 

mysql 

MySQL 5.0.51a-3ubuntu5 

5432 

postgresql 

PostgreSQL DB 8.3.0 – 8.3.7 

5900 

vnc 

VNC (protocol 3.3) 

6000 

X11 

(access denied) 

6667 

irc 

UnrealIRCd 

8009 

ajp13 

Apache Jserv (Protocol v1.3) 

8180 

http 

Apache Tomcat/Coyote JSP engine 1.1 

3.4 Potential Vulnerabilities 

Based on the identified services and versions, the following potential security concerns were noted (high-level only): 

Finding ID 

Description 

Related Service/Port 

Notes 

VULN-001 

Outdated FTP server version 

21 / vsftpd 2.3.4 

Known older version 

VULN-002 

Clear-text remote access service 

23 / Telnet 

Unencrypted protocol 

VULN-003 

Outdated web server 

80 / Apache 2.2.8 

Older Apache version 

VULN-004 

Legacy Samba version 

139, 445 / Samba 

Older Samba release 

VULN-005 

Unnecessary remote services 

512, 513, 514 

Legacy r-services 

VULN-006 

Exposed database services 

3306 MySQL / 5432 PostgreSQL 

Databases reachable 

VULN-007 

Multiple outdated services 

Various ports 

Several old software versions 

3.5 Risk Level 

Each finding was assigned a risk level based on potential impact and exposure: 

Finding ID 

Risk Level 

Justification 

VULN-001 

High 

Outdated FTP service commonly associated with known issues 

VULN-002 

High 

Telnet transmits data in clear text 

VULN-003 

Medium 

Older web server version increases exposure 

VULN-004 

Medium 

Legacy Samba version may contain weaknesses 

VULN-005 

High 

Unnecessary remote execution services increase attack surface 

VULN-006 

High 

Database services exposed without apparent restriction 

VULN-007 

Medium 

Multiple outdated services increase overall risk 

Risk Rating Criteria: 

High – Significant potential impact or clear-text / unnecessary services. 

Medium – Moderate impact from outdated software versions. 

Low – Limited impact under normal conditions. 

4. Risk Summary 

The target system (Metasploitable 2) presents a high overall risk posture due to a large number of open ports, multiple outdated services, clear-text protocols, and exposed database services. This is expected for an intentionally vulnerable training system. 

Summary of Findings: 

High Risk 

Medium Risk 

Low Risk 

4 

3 

0 

5. Recommended Remediation 

The following high-level remediation actions are recommended: 

Finding ID 

Recommended Action 

Priority 

VULN-001 

Update or replace the FTP service with a current, supported version 

High 

VULN-002 

Disable Telnet and use SSH for remote access instead 

High 

VULN-003 

Upgrade Apache to a supported current version and apply security patches 

Medium 

VULN-004 

Update Samba to a current supported release and restrict access 

Medium 

VULN-005 

Disable unnecessary r-services (rexec, rlogin, etc.) 

High 

VULN-006 

Restrict database access to trusted hosts only; enforce strong authentication 

High 

VULN-007 

Perform a full system update and remove unused services 

Medium 

General Recommendations: 

Apply security patches and updates for all identified services. 

Disable or restrict unnecessary services and ports. 

Implement strong authentication and access controls. 

Configure host-based firewalls to limit exposure. 

Follow the principle of least privilege for all services and accounts. 

6. Conclusion 

The network vulnerability assessment of the Metasploitable 2 system identified a significant number of open ports and outdated services, resulting in a high overall risk rating. This outcome is consistent with the system’s design as an intentionally vulnerable training platform. Regular vulnerability assessments remain essential for identifying and addressing security weaknesses. All testing was conducted ethically and strictly within the authorized educational lab environment. 

7. Appendix 
A. Additional Notes 

Target hostname: metasploitable.localdomain | MAC: 08:00:27:3B:AA:40 (VirtualBox) 

C. References 

Nmap documentation – https://nmap.org 

 
