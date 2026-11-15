# Sublist3r Summary Guide🔍 
## OverviewSublist3r is a fast, open-source Python tool designed to enumerate subdomains of target websites using Open Source Intelligence (OSINT). 
It helps ethical hackers, penetration testers, and security researchers map out the external attack surface of an organization by discovering hidden or less obvious subdomains.
## Key Features
Passive Reconnaissance: Gathers subdomain information quickly without directly pinging the target infrastructure loudly.
Multiple Data Sources: Integrates with several public search engines and security databases (such as Google, Yahoo, Bing, VirusTotal, Netcraft, ThreatCrowd, and DNSdumpster).
Brute-Force Integration: Includes Subbrute to find additional subdomains via brute-force enumeration using an improved wordlist.
Port Filtering: Allows users to check found subdomains against specific TCP ports.
Python Module Support: Can be imported and used directly within custom Python scripts.

## Installation:
On Kali LinuxSublist3r is often pre-installed on security distributions like Kali Linux. 
If not, you can install it via apt:Bashsudo apt update

    sudo apt install sublist3r

## 2. Manual Installation via GitHub (Python)
If you prefer to install it manually from the source repository.
## Clone the repository
git clone https://github.com/aboul3la/Sublist3r.git

# Navigate into the directory
cd Sublist3r

# Install dependencies
pip install -r requirements.txt

## Common Command-Line Options
Here is the Markdown table detailing Sublist3r's common command-line options:

| Short Flag | Long Flag | Description |
| --- | --- | --- |
| `-d` | `--domain` | Target domain name to enumerate subdomains for |
| `-b` | `--bruteforce` | Enable the Subbrute brute-force module |
| `-p` | `--ports` | Scan found subdomains against specific TCP ports (e.g., `80,443`) |
| `-v` | `--verbose` | Enable verbose mode to display findings in real-time |
| `-t` | `--threads` | Number of threads to use for brute-forcing |
| `-e` | `--engines` | Specify a comma-separated list of search engines to use |
| `-o` | `--output` | Save the results to a text file |
| `-h` | `--help` | Show the help message and exit |

For a practical demonstration of these flags in action, you can check out this [Sublist3r Full Guide and Enumeration Tutorial](https://www.youtube.com/watch?v=6b8pKBwuc20).
This video is relevant because it provides a visual, step-by-step walkthrough of how to install Sublist3r and apply these exact command-line flags during security assessments.

## Using Sublist3r as a Python Module
You can integrate Sublist3r into your own automation scripts:

    import sublist3r

# Call the main function to fetch subdomains

    subdomains = sublist3r.main(
        domain='example.com', 
        threads=40, 
        savefile='subdomains.txt', 
        ports=None, 
        silent=False, 
        verbose=False, 
        enable_bruteforce=False, 
        engines=None
    )

for subdomain in subdomains:
    print(subdomain)
