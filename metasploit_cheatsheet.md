# MSFconsole
- start msf with "msfconsole"
- "armitage" launches a gui version of metasploit


### MSFpayload
- Generates shellcode, executables, etc..
- Shellcode can be in the form of C, Ruby, JS, VBA
- Shellcode generated contains null characters, which may cause the code to terminate before completion.
- Plain text shellcode is more likely to be detected by IDS, and anti-virus

### MSFencode
- MSFencode is used to avoid bad chars, and evade IDS and anti-virus using encoding.
- Multiple encoders for use.

### Nasm Shell
- Used for assembly. Helps determine the opcodes for an assembly command.


# Passive Info Gathering
- Passive and indirect info gathering discovers info without touch the targets system.

### whois Lookups
- See names of target's domain servers

### netcraft
- web-based tool used to find IP address of a server hosting a specific website.

### Working with databases
- nmap -Pn -sS -oX subnets.xml 192.168.1.0/24: writes scan to a xml file.
- "db_import subnets.xml" View using hosts -c address.
- "db_status", then db_nmap -sS -A {IP}

# Metasploit Port Scans

### Targeted
- Looks for a specific OS, services or program versions
- smb_version, ssh_version, ftp_version
- mssql_ping: Uses UDP, which makes it slow. MS SQL Server is installed by default and may be a prereq for some software.


### SNMP Sweeping
- Reports info on bandwidth utilization, collision rates, OS, etc..
- "snmp_enum" Read (RO) and Write (RW) community strings will affect the information that can extracted.
- RO and TW community strings can be used to determine patch levels, running services, usernames, uptime, routes, etc...
- Community String are passwords used to query a device for information or to write configuration info to the device.
- Make use of "snmp_login" if any community strings are guessed to exploit.
