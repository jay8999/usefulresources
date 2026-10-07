# The LOLBAS Project (Living Off The Land Binaries, Scripts, and Libraries) is an open-source cybersecurity project and community-driven knowledge base.

# https://lolbas-project.github.io/

Its main purpose is to document legitimate, pre-installed binaries, scripts, and libraries native to operating systems (most notably Windows) that can be misused by threat actors, penetration testers, and red teams to execute malicious actions.

## Key aspects of the project include:

  "Living off the Land" (LotL): This technique involves utilizing tools already built into the OS (such as certutil.exe, msbuild.exe, or rundll32.exe) rather than downloading custom malware. This helps attackers blend in with normal system activity and evade security controls like antivirus or application allowlisting (AWL).

  MITRE ATT&CK Mapping: Each documented binary or script details its specific functions (e.g., download, execute, bypass UAC, dump credentials) and maps them directly to corresponding techniques in the MITRE ATT&CK framework.

  Sister Projects: The project has inspired related knowledge bases for other ecosystems, such as GTFOBins (for Unix/Linux binaries) and LOLDrivers (for vulnerable or malicious Windows drivers).
