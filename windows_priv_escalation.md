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
