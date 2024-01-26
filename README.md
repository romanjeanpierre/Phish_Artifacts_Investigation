<h1>Extracting & Investigating Phishing Email Artifacts</h1>

<h2>Response Protocol for Real Incident Handling</h2>
<p>
    This section outlines the immediate response steps an investigating analyst should take upon identifying a phishing email. It covers the entire process from detection to the completion of the investigation report.
</p>

<ol>
    <li>Retrieve an original copy of the phishing email</li>
    <li>Gather artifacts from the phishing email</li>
    <li>Inform the recipients who received the email</li>
    <li>Investigate malicious artifacts to collect indicators of compromise</li>
    <li>Implement defensive measures</li>
    <li>Complete the investigation report, documenting all the above steps</li>
</ol>

<h3>Detailed Response Steps:</h3>

<h4>1) Retrieve an Original of the Suspicious Email:</h4>
<p>
    Obtain the original version of the email via methods such as security technology at the email gateway, direct extraction from email solutions like Microsoft Exchange, or by having an employee forward the email to a security-owned mailbox.
</p>

<h4>2) Gather Artifacts From the Original Email:</h4>
<p>
    Collect important artifacts from the email for later analysis and defensive action.
</p>

<h4>3) Inform Email Recipients:</h4>
<p>
    Notify individuals who have received the phishing email to reduce the risk of interaction with it. This includes sending an email template with specific details such as the time of the email, subject line, instructions on handling the email, and contact details for further assistance.
</p>

<h4>4) Artifact Analysis and Investigation:</h4>
<p>
    Use tools like enterprise-grade sandboxing, URL2PNG, VirusTotal, IPVoid, WannaBrowser, and a virtual machine to investigate the email, web, and file-based artifacts.
</p>

<h4>5) Take Defensive Measures:</h4>
<p>
    Implement actions to mitigate risks posed by the phishing attack, such as blocking malicious URLs on a web proxy.
</p>

<h4>6) Complete Investigation Report:</h4>
<p>
    Document all steps taken during the response process in an investigation report for audit purposes.
</p>

<h2>Project Objective</h2>
<p>
    The primary goal of this project is to identify and categorize malicious emails by extracting and analyzing embedded web and file artifacts. This thorough process aims to establish a justification for the malicious nature of these artifacts, leading to informed decisions for their handling and mitigation.
</p>

<p align="center">
    <img src="https://imgur.com/WcQc9JU.png" height="80%" width="80%" alt="Project Overview Image">
</p>

<h2>Utilities Used</h2>
<ul>
    <li><b>PowerShell</b></li>
    <li><b>VirusTotal</b></li>
    <li><b>URL2PNG</b></li>
    <li><b>Wannabrowser</b></li>
    <li><b>WHOIS LOOKUP</b></li>
</ul>

<h3>Project in Progress</h3>

</body>
</html>
