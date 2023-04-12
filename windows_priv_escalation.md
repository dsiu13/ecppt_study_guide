# Windows

### Accounts
- User Accounts: A collection of settings or preferences bound to a unique id.
- "Admin" Account is created by default.
- Other default accounts may exist. e.g Network and Local service
- Service Accounts: Used to run services. Cannot use Service accounts to sign into Windows.
- System Accounts: Has the highest level priv of any local account.

### Groups
- User accounts can belong to a group and can be in more than one group.
- Groups can be apart of other groups.
- Groups allow for easier access control.
- Regular Groups have set list of Users
- Pseudo Groups have a dynamic list of members based on interactions.

### Resources (Objects)
- Files/Directories
- Registry Entries
- Services
- Resource access is dependent on it's ACL.

### Access Control List (ACL)
- Permissions are controlled by the ACL.
- The ACL is made up of Access Control Entries (ACE).
- Each ACE defines access rights of Users, Groups, etc...


# Spawning Admin Shells

## msfvenom
- Reverse shells can be spawned if admin privileges have been obtained.
- msfvenom can spawn the reverse shell, which is caught using Netcat or Metasploits own handler.
- Netcat Listener Command: "nc -nvlp {Port #}"

## RDP
- RDP can be used by adding a low privileged user to the admin group and then spawn an admin command prompt using the GUI.
- "net localgroup administrators <Username> /add"

## PSexec
- Can escalate an admin user to full System privileges.

# Prvilige Escalation Tools
- PowerUp(Powershell Based) and SharpUp(C# Based) both look for specific common misconfigurations.
- SharpUp needs to be compiled or use an already compiled binary.
- [SharpUp Github](https://github.com/GhostPack/SharpUp)
- [PowerUp](https://github.com/badamczewski/PowerUp)

# Seatbelt
- An enumeration tool that provides related info for escalation.
- Does not search for misconfigurations.
- [SeatBelt](https://github.com/GhostPack/Seatbelt)

# Kernal Exploits
- Kernals have control over the OS.
- Kernal Exploits can result in execution at the System User level.
- [Windows Exploit Suggester](https://github.com/bitsadmin/wesng)
- [Windows Kernal Exploits](https://github.com/SecWiki/windows-kernel-exploits)
- [Watson](https://github.com/rasta-mouse/Watson)

### Find Kernal Exploits
1. Enumeration Windows Version/ Patch Level (System Info)
2. Find an exploit that works.
3. Compile at run.
- Kernal Exploits are unstable and may be single use only or cause system crashes. Last Resort for priv escalation.

# Service Exploits
- Services are programs that run in the background, which accept input or perform regular tasks.
- Services that run with System Privileges with misconfigurations can lead to executions at the System level.
- "sc.exe qc <name>" queries service configurations
- "sc.exe query <name>" queries status of a service
- "sc.exe config <name> <option>= <value>"
- "net start/stop <name>" starts or stops a service

### Service Misconfigurations
- Methods to exploit misconfigurations.
1. Insecure Service Properties
2. Unquoted Service Path
3. Weak Registry Permissions
4. Insecure Service Executables
5. DLL Hijacking

#### Insecure Service Permissions
- Each service has an ACL for service-specific permissions.
- Not permissions are dangerous. e.g SERVICE_QUERY_CONFIG, SERVICE_QUERY_STATUS.
- SERVICE_STOP, SERVICE_START, SERVICE_CHANGE_CONFIG, and SERVICE_ALL_ACCESS may be useful and/or dangerous.
- If the User has the ability to change the configurations of a service that runs with System Privileges, the executable the service uses can be changed to one of our own.
- Just because a service configuration can be changed, but you cannot stop or start the service then you may not be able to gain privilege escalation. If services cannot be stopped then a restart is your only option, which may not be possible.

#### Unquoted Service Path
- Executables can be run without extensions. eg "whoami.exe" can be "whoami"
- Executables can take arguments.
- "C:\\Program Files\\Dir\\Program.exe" Windows may interpret this as an executable with args. Windows resolves this by checking each of the possibilities.
- Exploitable by writing to a location Windows checks before the actual executable. This will cause the service to executable what we wrote at that location.

#### Weak Registry Permissions
- Windows stores entries for each service.
- Misconfigurations with a Registry's ACL means it is possible to modify a service's configuration even if we cannot modify the service directly.

#### Insecure Service Executables
- If an Original Service Executable is modifiable then a reverse shell can replace that executable. **Create a Backup if it's a real system for restore"**

### DLL Hijacking
- Services may make use of Dynamic-Link Libraries for functionality. The DLL used will have the same level of privilege.
- DLLs loaded with an absolute path may allow for privilege escalation if the User has writable permission for that DLL.
- Most common way for Privilege Escalation using DLL is if the DLL called is missing, and the User can write to a directory within the path windows searches in

# Registry
- AutoRuns: Windows can be setup to run commands at startup with assigned privilege levels.
- AutoRuns are configured in the Registry.
- Writing to an AutoRun executable allows for privilege escalation if restarting is possible. Difficult method due to the requirements that are needed.

# Passwords
- Passwords that are stored insecurely, or stored in readable locations can be utilized for escalation.
- Windows may store passwords in plaintext in the Registry.
- "reg query HKLM /f password /t REG_SZ /s" or "reg query HKCU /f password /t REG_SZ /s" are commands that searches known locations where a Registry might store passwords.
- Passwords may be left on configuration files themselves.
- Manual searches can be performed using "dir /s \*pass\* == *.config" 
