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
    Use tools like enterprise-grade sandboxing, URL2PNG, VirusTotal, IPVoid, WannaBrowser, and a virtual machine to investigate email, web, and file-based artifacts.
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

<h2>Project Walk Through</h2>
<h3>Email Artifacts Analysis</h3>
<ul>
    <li><strong>Email Appearance and Intent</strong>: Describe how the email looks and its apparent objective.</li>
    <li><strong>Sender Information</strong>:
        <ul>
            <li>Sending Address: Identify the email's sending address.</li>
            <li>Subject Line: Note the email's subject line.</li>
            <li>Recipients: List who the email was sent to.</li>
            <li>Reply-To Address: Specify the reply-to address, if present.</li>
            <li>Timestamp: Record the date and time the email was sent, converted to UTC.</li>
            <li>Sending Server IP: Identify the IP address of the sending server.</li>
            <li>Reverse DNS of IP: Provide the reverse DNS result of the sending server's IP.</li>
        </ul>
    </li>
</ul>

<h3>File Artifacts Analysis</h3>
<ul>
    <li><strong>File Details</strong>:
        <ul>
            <li>File Name and Type: Specify the full file name, including its file type.</li>
            <li>SHA256 Hash: Note the SHA256 hash value of the file.</li>
        </ul>
    </li>
</ul>

<h3>Web Artifacts Analysis</h3>
<ul>
    <li><strong>Web Elements</strong>:
        <ul>
            <li>Full URL: Detail the full URL found in the email.</li>
            <li>Root Domain: Identify the root domain of the URL.</li>
            <li>Analysis Conducted: Specify which analyses were performed (e.g., URLZPNG, WannaBrowser, VirusTotal, URLScan.io).</li>
        </ul>
    </li>
</ul>

<h3>Defensive Measures</h3>
<ul>
    <li><strong>Email Artifact Mitigation</strong>: Detail the defensive measures you propose for handling email artifacts.</li>
    <li><strong>File Artifact Mitigation</strong>: Describe the defensive measures you suggest for dealing with file artifacts.</li>
</ul>

<h3> Analysis on Credential Harvester email example </h3>
<img src="https://imgur.com/LuF4xmI.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<h3> First Impressions: </h3>
<p> - ‘auto-confirm.info-amazon.co.uk' (where info-amazon.co.uk is the domain, not amazon.co.uk), but we can see it’s coming from QPE77756@mun.ca - this definitely isn't Amazon. </p>
<p> - Formating/styling is inconsistent - Varying fonts </p>
<p> - Email is addressed to generic recipient 'Amazon User' </p>
<p> - Has an obvious call to action button 'Help Page - Refund Form'</p>

<h3> Further Analysis on Credential Harvester: </h3>
<p> Drag & Drop .eml file to Sublime Text for detailed artifact extraction </p>
<h3> Identify Mail Artifacts </h3>
<p> (CTRL + F) 'from' string  to find the sending address containing the <> symbol</p>
<p> Identify Sending address, Subject Line, Recipients, Reply-to address, Date, Sending Server IP Address </p>
<img src="https://imgur.com/nbKjVBR.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/HiBtREj.png" height="80%" width="80%" alt="FTK Imager Memory Capture">

<h3> Reverse DNS Search </h3>
<p> Input sending server IP address to whois.domaintools.com, no hostname found, states that the IP is owned by ‘United States Ashburn Charter Communications’. It seems that an individual company no longer owns this IP, so we won't be able to get the hostname from here. While IP ownership can change, we'll always have the original information preserved within the email file. </p>
<img src="https://imgur.com/syeKVMm.png" height="80%" width="80%" alt="FTK Imager Memory Capture">

<h3> Analyze Web Artifacts </h3>
<p> Right-click and copy the hyperlink, input results to VirusTotal and URL2PNG </p>
<img src="https://imgur.com/U6dSmf9.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<p> Results show that security vendors have flagged the link and may potentially be malicious. </p>
<img src="https://imgur.com/3OOXafk.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<p> Snapshot image of the landing page appears to be broken</p>

<h3> Suggested Defensive Measures </h3>
As the sender is using a domain address, the most appropriate action would be to block this specific mailbox to prevent any more incoming malicious emails from this sender.

Requesting an email gateway block for the sending address “QPE77756@mun.ca" and sender IP address: 68[.]114[.]190[.]29

The domain has been recognized as malicious, and there is no business justification for any employees needing to access this site. As it has a malicious reputation on VirusTotal, and analysis has shown that it is hosting a credential harvester, the entire domain can be blocked on the web proxy, preventing employees from connecting to the site. This will also make future phishing attacks using this same domain ineffective.

Requesting a web proxy block for the domain “hxxp[://]id820update[.]refundsys59[.]co[.]uk/invoice103amz/index[.]php?email=jack[.]tractive@abcindustries[.]co[.]uk“.


