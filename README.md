<h1>Collection of AD GPO projects, focusing on various administrative and security configurations using Group Policy Objects (GPOs)</h1>

 ### [YouTube Demonstration](https)

<h2> <a href="https://github.com/K-ING-TECH/Active_Directory_GPO_Labs/blob/main/Password_GPO">Password GPO</a></h2> 
This project provides a step-by-step guide to setting up a Group Policy Object (GPO) for enforcing password complexity requirements in Active Directory, along with best practices recommended by security professionals.


<h3>Step-by-Step Guide to Enforce Password Complexity via GPO</h3>
<ol>
    <li><strong>Open Group Policy Management Console (GPMC)</strong>
        <p>On your domain controller, press <code>Win + R</code>, type <code>gpmc.msc</code>, and press Enter.</p>
    </li>
    <li><strong>Navigate to the Default Domain Policy</strong>
        <p>In the left pane of the GPMC, expand your domain. The path would typically be Forest -> Domains -> YourDomain. Right-click on "Default Domain Policy" and select "Edit." This will open the Group Policy Management Editor.</p>
    </li>
    <li><strong>Edit the Password Policy</strong>
        <p>In the Group Policy Management Editor, navigate to Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Account Policies -> Password Policy.</p>
    </li>
    <li><strong>Configure Password Complexity Requirements</strong>
        <p>Double-click on "Password must meet complexity requirements." Set the policy to "Enabled." Click "OK."</p>
        <p>Complexity requirements typically include:</p>
        <ul>
            <li>Passwords must be at least six characters long.</li>
            <li>Passwords cannot contain the user’s account name or parts of the user’s full name that exceed two consecutive characters.</li>
            <li>Passwords must contain characters from three of the following four categories:</li>
            <ul>
                <li>Uppercase letters (A-Z)</li>
                <li>Lowercase letters (a-z)</li>
                <li>Digits (0-9)</li>
                <li>Special characters (e.g., !, $, #, %)</li>
            </ul>
        </ul>
    </li>
    <li><strong>Configure Additional Password Policies</strong>
        <p>Security professionals recommend configuring the following additional policies to enhance security:</p>
        <ul>
            <li>Minimum password length: Set to at least 12 characters to enhance security.</li>
            <li>Maximum password age: Set to 90 days to ensure regular password updates.</li>
            <li>Minimum password age: Set to 1 day to prevent users from cycling through passwords too quickly.</li>
            <li>Enforce password history: Set to remember at least 24 previous passwords to prevent reuse.</li>
        </ul>
    </li>
    <li><strong>Implement Account Lockout Policies</strong>
        <p>Additionally, configure account lockout policies to protect against brute-force attacks:</p>
        <ul>
            <li>Account lockout threshold: Set to 5 invalid logon attempts.</li>
            <li>Account lockout duration: Set to 30 minutes.</li>
            <li>Reset account lockout counter after: Set to 30 minutes.</li>
        </ul>
    </li>
    <li><strong>Close the Editor</strong>
        <p>Close the Group Policy Management Editor. The changes are automatically saved.</p>
    </li>
    <li><strong>Force Group Policy Update (Optional)</strong>
        <p>To apply the changes immediately, you can force an update on the target machines by running <code>gpupdate /force</code> in the command prompt.</p>
    </li>
</ol>

<h3>Best Practices</h3>
<ul>
    <li><strong>Regular Audits:</strong> Conduct regular audits of password policies and compliance to ensure adherence to security standards.</li>
    <li><strong>User Education:</strong> Educate users about creating strong passwords and the importance of not sharing them.</li>
    <li><strong>Multi-Factor Authentication (MFA):</strong> Implement MFA to add an additional layer of security beyond just passwords.</li>
    <li><strong>Use of Password Managers:</strong> Encourage the use of password managers to help users manage complex passwords securely.</li>
</ul>

<br />

<br />

<h2> <a href="https://github.com/K-ING-TECH/Active_Directory_GPO_Labs/blob/main/WALLPAPER_GPO">Wallpaper GPO</a></h2> 
This project provides a step-by-step guide to setting up a Group Policy Object (GPO) for enforcing password complexity requirements in Active Directory, along with best practices recommended by security professionals.


<br />

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
