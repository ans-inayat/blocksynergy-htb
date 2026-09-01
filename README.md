# blocksynergy-htb

Complete exploit and quick usage notes for blocksynergy.htb

## Add to /etc/hosts

Add the target to your /etc/hosts so the name resolves locally:

```text
10.10.x.x  blocksynergy.htb
```

Replace `10.10.x.x` with the actual IP address of the target in your lab environment.

## Quick workflow

1. First enumerate the machine to discover open ports and services:

```bash
# basic host discovery / service scan
nmap blocksynergy.htb

# targeted full scan for common services, NSE scripts, version and OS detection
nmap -p22,8080 -sC -sV -O -oA complete-scan.txt blocksynergy.htb
```

2. Continue manual enumeration of discovered services (web, SSH, etc.) based on the scan results.

3. If an exploit is available that requires a particular profile/rank or configuration, run it. If you do not have the required profile, continue intended/manual enumeration to obtain appropriate access.

4. To run the bundled exploit script and read the flags:

```bash
python complete-exploit.py -t blocksynergy.htb
```

## Notes

- Use sudo when running some nmap options (for OS detection and certain NSE scripts).
- Only run exploits against machines you own or have explicit permission to test.
- Adjust IPs, paths, and filenames to match your environment.
