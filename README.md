Web Application Penetration Test: DVWA (Metasploitable2)

A web application penetration testing report completed as part of [Course Name] by [Jerusalem District Electricity Company (JDECO) BY eng.Ahmad barhoum]. The target was Damn Vulnerable Web Application (DVWA) running on Metasploitable2, tested with Burp Suite in an isolated lab.

Educational use only. All testing was done against an intentionally vulnerable application in an isolated, non-production lab (host-only network). Do not use these techniques against systems you do not own or have explicit permission to test.

📄 Report

Full report: Doaa_Badwan_DVWA_Pentest_Report.pdf

Scope & Environment
Item	Detail
Target application	DVWA v1.0.7
Target host	Metasploitable2 (192.168.1.3)
Attacker host	Kali Linux (192.168.1.4)
Testing platform	Burp Suite Community Edition (Proxy, Repeater, Intruder)
Network	Isolated host-only / internal network
DVWA security level	Low
Methodology
Environment preparation and connectivity check
Reconnaissance of each DVWA module
Traffic interception with Burp Proxy
Exploitation with Burp Repeater / Intruder
Evidence collection (screenshots, request/response pairs)
Root cause analysis
Remediation recommendations
Summary of Findings
ID	Vulnerability	Severity	Impact
WEB-01	SQL Injection	High	Full disclosure of user table and password hashes
WEB-02	OS Command Injection	Critical	Remote command execution as www-data
WEB-03	Reflected XSS	Medium	Script execution in the victim's browser
WEB-04	Stored XSS	High	Persistent script execution for every visitor
WEB-05	CSRF	Medium	Forced password change without consent
WEB-06	Local File Inclusion	High	Arbitrary read of files accessible to www-data
WEB-07	Unrestricted File Upload	Critical	Web shell upload leading to RCE

Note on impact: the LFI test could read /etc/passwd but not /etc/shadow, because the web server runs as the low-privileged www-data user. The report scopes risk accordingly instead of labeling every finding "critical" without context.

Key Takeaways
Validate and sanitize all input server-side; use parameterized queries and output encoding.
Never pass user input to system commands; use allow-lists for file paths and upload types.
Use anti-CSRF tokens, run the web server with least privilege, and disable script execution in upload directories.
Tools

Kali Linux · Burp Suite Community · Firefox · Metasploitable2 · DVWA

Author

Doaa Badwan LinkedIn · [https://www.linkedin.com/in/doaa-badwan-a4a522304/]

License

Documentation shared for educational purposes. Feel free to read and learn from it; please credit the author if you reuse any part.
