# Router SSH Configuration with Explanations

This document provides the SSH configuration for each router in the topology. The configuration secures remote access using SSH version 2, generates RSA encryption keys, and sets connection timeouts and retries to enhance security. A user with full administrative privileges is created on each router to allow secure management.

### Command Explanations:

- **`conf t`**: Enters global configuration mode, enabling changes to the router's settings.
- **`ip domain-name [domain-name]`**: Sets a domain name, necessary for RSA key generation.
- **`crypto key generate rsa modulus 1024`**: Generates RSA encryption keys with a modulus size of 1024 bits to secure SSH communication.
- **`ip ssh version 2`**: Configures SSH version 2, the more secure version, for remote access.
- **`ip ssh time-out 60`**: Sets the SSH session timeout to 60 seconds, closing inactive sessions to prevent unauthorized access.
- **`ip ssh authentication-retries 2`**: Limits SSH login attempts to 2, reducing the risk of brute-force attacks.
- **`username [name] privilege 15 password [password]`**: Creates a local user with full administrative privileges (privilege level 15) and sets a password for secure access.
- **`line vty 0 4`**: Enters VTY line configuration mode, which manages remote access via SSH.
- **`login local`**: Configures local authentication, ensuring only local database users can access the router.
- **`transport input ssh`**: Restricts access to SSH only, disabling other less secure protocols such as Telnet.

---

### Router1 SSH Configuration

```bash
conf t
ip domain-name cisco1.com
crypto key generate rsa modulus 1024
ip ssh version 2
ip ssh time-out 60
ip ssh authentication-retries 2
username mouad privilege 15 password mouad
line vty 0 4
 login local
 transport input ssh
```

### Router2 SSH Configuration

```bash
conf t
ip domain-name cisco2.com
crypto key generate rsa modulus 1024
ip ssh version 2
ip ssh time-out 60
ip ssh authentication-retries 2
username mouad privilege 15 password mouad
line vty 0 4
 login local
 transport input ssh
```

### Router3 SSH Configuration

```bash
conf t
ip domain-name cisco3.com
crypto key generate rsa modulus 1024
ip ssh version 2
ip ssh time-out 60
ip ssh authentication-retries 2
username mouad privilege 15 password mouad
line vty 0 4
 login local
 transport input ssh
```

---

This configuration ensures secure access to each router using SSH with RSA encryption, along with optimized security settings for session timeouts and retries. All routers have a consistent setup with domain names adjusted for each specific router (Router1, Router2, Router3).
