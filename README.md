EXECUTIVE SUMMARY
This lab was a final security test of 2 vulnerable apps: DVWA and OWASP Mutillidae II. The test was done on 06 Sep 2026 in a safe Kali Linux virtual machine at 127.0.0.1. No real systems were touched. 
METHODOLOGY:
I used Firefox, curl, and OWASP ZAP to test the apps. ZAP was set to "Protected Mode" so it only tested DVWA and Mutillidae and skipped logout pages. First I browsed the sites to map them. Then I ran a small, safe scan. I did not run any attacks that could break or delete data.
TOOLS AND RESOURCES USED:
I made use of the following tools and resources:
Laptop: Served as the primary device for conducting the challenge.
Kali Linux: Provided a robust operating system for penetration testing and vulnerability assessment.
Zap: It is a free, open-source security testing tool used to find vulnerabilities in web applications.
FINDINGS:
Reflected XSS in DVWA: I was able to make a green box LAB5-XSS-MARKER-BENIGN appear on the page. This proves code can be injected, but I did not steal any cookies.SQL Injection in Mutillidae: When I typed admin' AND '1'='1 I got results. When I typed admin' AND '1'='2 I got no results. This proves the database can be influenced, but I did not dump any data.Security Misconfiguration in DVWA: The session cookie PHPSESSID was missing important protections like Secure, HttpOnly, and SameSite when set to Low security.
Impact:The app was running as www-data, not as root. I did not try to hack the whole system. I fixed the issues by setting DVWA to High/Impossible and Mutillidae to Security Level 5. After fixing: XSS code was blocked, SQL Injection was blocked by prepared statements, and cookies now had Secure; HttpOnly; SameSite=Strict.Priority:XSS - Highest risk because it can affect other usersSQL Injection - Medium riskCookie Flags - Lowest riskAfter all fixes, the remaining risk is Low as long as secure settings are kept.
Cleanup: All test files were deleted, I logged out, reset the databases, and restored a clean VM snapshot.

SCREENSHOTS AND EVIDENCES:
All relevant screenshots and evidence collected during the completion of this lab task have been meticulously documented and incorporated into the analysis above, providing a thorough and comprehensive overview of the findings.


CONCLUSION:
This capstone lab successfully tested DVWA and OWASP Mutillidae II for common web vulnerabilities in a safe, isolated environment. During the assessment, 3 key issues were found and proven with minimal-impact tests: Reflected XSS in DVWA SQL Injection Boolean Logic in Mutillidae Missing Cookie Security Flags in DVWAAll findings were documented with request/response evidence and screenshots as required. This lab showed how important it is to use secure coding practices, proper input validation, and correct server configurations. It also showed how tools like Firefox, curl, and OWASP ZAP can be used to find and prove vulnerabilities safely without causing damage.No real systems were harmed, and all test data was cleaned up after the assessment.
