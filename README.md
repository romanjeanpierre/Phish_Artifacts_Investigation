<h1> Phishing Email Analysis & Response Framework </h1>

 <h2>Response Protocol for Real Incident Handling</h2>
    <p>This section outlines the immediate response steps an investigating analyst should take upon identifying a phishing email, covering the process from detection to the completion of the investigation report.</p>

<ol>
        <li>Retrieve an original copy of the phishing email.</li>
        <li>Gather artifacts from the phishing email.</li>
        <li>Inform the recipients who received the email.</li>
        <li>Investigate malicious artifacts to collect indicators of compromise.</li>
        <li>Implement defensive measures.</li>
        <li>Complete the investigation report, documenting all the above steps.</li>
    </ol>

<h2>Detailed Response Steps</h2>
    
 <h3>1) Retrieve an Original of the Suspicious Email</h3>
    <p>Obtain the original version of the email via methods such as security technology at the email gateway, direct extraction from email solutions like Microsoft Exchange, or by having an employee forward the email to a security-owned mailbox.</p>

<h3>2) Gather Artifacts From the Original Email</h3>
    <p>Collect important artifacts from the email for later analysis and defensive action.</p>

<h3>3) Inform Email Recipients</h3>
    <p>Notify individuals who have received the phishing email to reduce the risk of interaction with it. This includes sending an email template with specific details such as the time of the email, subject line, instructions on handling the email, and contact details for further assistance.</p>

<h3>4) Artifact Analysis and Investigation</h3>
    <p>Use tools like enterprise-grade sandboxing, URL2PNG, VirusTotal, IPVoid, WannaBrowser, and a virtual machine to investigate email, web, and file-based artifacts.</p>

<h3>5) Take Defensive Measures</h3>
    <p>Implement actions to mitigate risks posed by the phishing attack, such as blocking malicious URLs on a web proxy.</p>

 <h3>6) Complete Investigation Report</h3>
    <p>Document all steps taken during the response process in an investigation report for audit purposes.</p>

<h2>Project Objective</h2>
    <p>The primary goal of this project is to identify and categorize malicious emails by extracting and analyzing embedded web and file artifacts. This thorough process aims to establish a justification for the malicious nature of these artifacts, leading to informed decisions for their handling and mitigation.</p>

<p align="center">
        <img src="https://imgur.com/WcQc9JU.png" alt="Project Overview Image" style="width:80%; height:80%;">
    </p>

 <h2>Utilities Used</h2>
    <ul>
        <li><strong>PowerShell</strong></li>
        <li><strong>VirusTotal</strong></li>
        <li><strong>URL2PNG</strong></li>
        <li><strong>Wannabrowser</strong></li>
        <li><strong>WHOIS LOOKUP</strong></li>
    </ul>

<h2>Project Walk Through</h2>
    <h3>Email Artifacts Analysis</h3>
    <ul>
        <li><strong>Email Appearance and Intent</strong>: Describe the email's appearance and its apparent objective.</li>
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
                <li>Analysis Conducted: Specify which analyses were performed (e.g., URL2PNG, WannaBrowser, VirusTotal, URLScan.io).</li>
            </ul>
        </li>
    </ul>

<h3>Defensive Measures</h3>
    <ul>
        <li><strong>Email Artifact Mitigation</strong>: Detail the defensive measures you propose for handling email artifacts.</li>
        <li><strong>File Artifact Mitigation</strong>: Describe the defensive measures you suggest for dealing with file artifacts.</li>
    </ul>

<h3>Analysis on Credential Harvester Email Example</h3>
    <img src="https://imgur.com/LuF4xmI.png" alt="FTK Imager Memory Capture" style="width:80%; height:80%;">

<h3>First Impressions</h3>
    <ul>
        <li>Domain 'auto-confirm.info-amazon.co.uk' (where 'info-amazon.co.uk' is the domain, not 'amazon.co.uk'), but it's sent from 'QPE77756@mun.ca' - this is not Amazon.</li>
        <li>Inconsistent formatting and styling - varying fonts.</li>
        <li>Email is addressed to a generic recipient 'Amazon User'.</li>
        <li>Contains an obvious call to action button 'Help Page - Refund Form'.</li>
    </ul>

<h3>Further Analysis on Credential Harvester</h3>
    <p>Drag & Drop .eml file to Sublime Text for detailed artifact extraction.</p>

<h3>Identify Mail Artifacts</h3>
    <p>Use (CTRL + F) with the 'from' string to find the sending address containing the &lt;&gt; symbol.</p>
    <p>Identify Sending address, Subject Line, Recipients, Reply-to address, Date, Sending Server IP Address.</p>
    <img src="https://imgur.com/nbKjVBR.png" alt="Email Analysis Screenshot" style="width:80%; height:80%;">
    <img src="https://imgur.com/HiBtREj.png" alt="Email Analysis Screenshot" style="width:80%; height:80%;">

<h3>Reverse DNS Search</h3>
    <p>Input sending server IP address to whois.domaintools.com. No hostname found, states that the IP is owned by ‘United States Ashburn Charter Communications’. It seems that an individual company no longer owns this IP, so we can't get the hostname from here. While IP ownership can change, we'll always have the original information preserved within the email file.</p>
    <img src="https://imgur.com/syeKVMm.png" alt="Reverse DNS Search Screenshot" style="width:80%; height:80%;">

<h3>Analyze Web Artifacts</h3>
    <p>Right-click and copy the hyperlink, input results to VirusTotal and URL2PNG.</p>
    <img src="https://imgur.com/U6dSmf9.png" alt="Web Analysis Screenshot" style="width:80%; height:80%;">
    <p>Results show that security vendors have flagged the link and it may potentially be malicious.</p>
    <img src="https://imgur.com/3OOXafk.png" alt="Web Analysis Screenshot" style="width:80%; height:80%;">
    <p>Snapshot image of the landing page appears to be broken.</p>

<h3>Suggested Defensive Measures</h3>
<p> Blocking Mail Artifacts: </p>
    <p>As the sender is using a domain address, the most appropriate action would be to block this specific mailbox to prevent any more incoming malicious emails from this sender. Requesting an email gateway block for the sending address "QPE77756@mun[.]ca" and sender IP address: 68[.]114[.]190[.]29. </p>
    
<p> Blocking Web Artifacts: </p>    
 <p>The domain has been recognized as malicious, and there is no business justification for any employees needing to access this site. As it has a malicious reputation on VirusTotal, and analysis has shown that it is hosting a credential harvester, the entire domain can be blocked on the web proxy, preventing employees from connecting to the site. This will also make future phishing attacks using this same domain ineffective. Requesting a web proxy block for the domain "hxxp[://]id820update[.]refundsys59[.]co[.]uk/invoice103amz/index[.]php?email=jack[.]tractive@abcindustries[.]co[.]uk".
</p>
