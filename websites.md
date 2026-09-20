# https://gtfobins.org/

# What is GTFOBins? 

### GTFObins is primarily used by penetration testers, red teamers, cybersecurity students (such as those playing Capture The Flag / CTF challenges), and system administrators for the following reasons:  

* **Privilege Escalation:** If a user finds a binary that they are allowed to run via sudo, or one that has the SUID bit set, they can look it up on GTFOBins. The site provides copy-and-paste commands that instantly exploit that binary to spawn a root shell.  

* **Bypassing Restrictions:** It shows how legitimate, everyday programs can be manipulated to break out of restricted shells or sandboxed environments.  

* **Post-Exploitation Tasks:** Beyond just getting root access, the site details how binaries can be leveraged for reading/writing sensitive files, transferring files, or executing system commands.  

### Defensive Auditing: Security professionals and system administrators use GTFOBins in reverse. By checking which programs are listed on the site, they can determine which binaries are dangerous to leave with elevated permissions (SUID or sudo) and lock down their systems accordingly.  

# https://roadmap.sh/cyber-security

# What is roadmap.sh?

### 1. The Visual Career Path
* **Structured Learning:** Breaks the vast field of cybersecurity into chronological, logical steps.
* **Core Fundamentals:** Starts with basics like networking, operating systems (Linux/Windows), and basic programming.
* **Specialized Branches:** Guides you through offensive security (red teaming), defensive security (blue teaming), cloud security, and more.

### 2. Interactive Tracking
* **Progress Checkboxes:** Allows users to click on individual skills or topics to track what they have learned.
* **Customizability:** You can save your progress (often via local storage or an account) as you move through your studies.

### 3. Curated Resources
* **Recommended Learning Material:** Clicking on a node on the map often reveals links to articles, tutorials, documentation, and video courses.
* **Practice Platforms:** Suggests real-world training grounds like *TryHackMe*, *HackTheBox*, and CTF (Capture the Flag) events.

### 4. Certification Roadmaps
* Highlights recognized industry certifications (e.g., CompTIA Security+, CEH, OSCP) that align with different stages of the roadmap.

## Why Use It?
* **Prevents "Tutorial Hell":** Gives you a clear direction instead of wandering aimlessly through random tutorials.
* **Free and Open Source:** Entirely community-driven and updated regularly to keep pace with industry standards.
* **Comprehensive:** Covers both offensive (hacking) and defensive (protecting) aspects of security.

# https://www.wappalyzer.com/

## Wappalyzer(opens in new tab) is a browser extension and online tool that identifies the technologies a website uses, frameworks, CMS platforms, CDNs, analytics tools, payment processors, and more. It can often detect version numbers, which helps when searching for known vulnerabilities. Install it from your browser's extension store and visit any site to see the tech stack immediately.

# https://github.com/OJ/gobuster

[Gobuster] is an open-source enumeration tool written in Go. It supports multiple modes: directory/file enumeration (`dir`), DNS subdomain enumeration (`dns`), and virtual host enumeration (`vhost`). It's pre-installed on the AttackBox and included by default in Kali Linux.

Run `gobuster --help` to see the available commands and global flags:

| Flag | Description |
| :--- | :--- |
| `-t` / `--threads` | Number of concurrent threads (default: 10). Increase for faster scans. |
| `-w` / `--wordlist` | Path to the wordlist file. Required for all modes. |
| `-o` / `--output` | Write results to a file instead of stdout. |
| `--delay` | Wait time between requests: useful against rate-limited servers. |

## Wordlists

A good wordlist is critical. [SecLists](https://github.com/danielmiessler/SecLists) is the most widely used collection and is pre-installed on the AttackBox at `/usr/share/wordlists/SecLists/`. For directory enumeration, `Discovery/Web-Content/common.txt` and `Discovery/Web-Content/directory-list-2.3-medium.txt` cover most scenarios.

## dir Mode

The `dir` mode brute-forces directories and files on a web server. The basic syntax is:

    ```bash
    gobuster dir -u "[http://10.48.140.140](http://10.48.140.140)" -w /path/to/wordlist
