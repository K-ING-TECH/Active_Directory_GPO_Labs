<h1>Collection of AD GPO projects, focusing on various administrative and security configurations using Group Policy Objects (GPOs)</h1>

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


<h2><a href="https://github.com/K-ING-TECH/Active_Directory_GPO_Labs/blob/main/WALLPAPER_GPO">Wallpaper GPO</a></h2>
This project provides a detailed guide on how to set up a Group Policy Object (GPO) to enforce a desktop wallpaper for users in a specific Organizational Unit (OU) in Active Directory. 
The wallpaper file is stored on the domain controller (DC) and shared with users.

<h3>Step-by-Step Guide to Set a Desktop Wallpaper via GPO</h3>
<ol>
    <li><strong>Storing the Wallpaper on the Domain Controller</strong>
        <ul>
            <li><strong>Upload the Wallpaper File to the Domain Controller</strong>
                <p>Copy the wallpaper image file to a directory on the domain controller. For example, you could place it in a folder called <code>C:\Wallpapers</code>.</p>
            </li>
            <li><strong>Share the Folder</strong>
                <p>Share the folder containing the wallpaper so that all users have read access.</p>
                <ul>
                    <li>Right-click the folder (<code>C:\Wallpapers</code>), select "Properties," then go to the "Sharing" tab.</li>
                    <li>Click "Share," add "Authenticated Users" or a similar group, and set the permission level to "Read." Click "Share" and then "Done."</li>
                </ul>
            </li>
        </ul>
    </li>
    <li><strong>Setting the GPO to Use the Wallpaper</strong>
        <ul>
            <li><strong>Open Group Policy Management Console (GPMC)</strong>
                <p>On your domain controller, open the Group Policy Management Console by pressing <code>Win + R</code>, typing <code>gpmc.msc</code>, and pressing Enter.</p>
            </li>
            <li><strong>Navigate to the Sales OU</strong>
                <p>In the left pane of the GPMC, navigate to the Sales OU where you want to create and link the GPO.</p>
            </li>
            <li><strong>Create a New GPO</strong>
                <p>Right-click on the Sales OU and select "Create a GPO in this domain, and Link it here..."</p>
                <p>Name the GPO something like "Sales Wallpaper GPO" and click "OK."</p>
            </li>
            <li><strong>Edit the GPO</strong>
                <p>Right-click on the newly created GPO and select "Edit" to open the Group Policy Management Editor.</p>
            </li>
            <li><strong>Configure Wallpaper Settings</strong>
                <p>In the Group Policy Management Editor, navigate to User Configuration -> Policies -> Administrative Templates -> Desktop -> Desktop.</p>
                <p>Double-click on the "Desktop Wallpaper" setting.</p>
            </li>
            <li><strong>Set the Wallpaper</strong>
                <p>In the "Desktop Wallpaper" window, set the following options:</p>
                <ul>
                    <li>Wallpaper Name: Enter the full UNC path to the wallpaper image file. For example, <code>\\DCName\Wallpapers\wallpaper.jpg</code> (replace DCName with the actual name of your domain controller).</li>
                    <li>Wallpaper Style: Select the appropriate style (e.g., Fill, Fit, Stretch, Tile, Center). For example, select "Fill."</li>
                </ul>
                <p>Click "Enabled" to enforce the setting, then click "OK."</p>
            </li>
            <li><strong>Close the Editor</strong>
                <p>Close the Group Policy Management Editor. The changes are automatically saved.</p>
            </li>
            <li><strong>Link the GPO to the Sales OU</strong>
                <p>Ensure the GPO is linked to the Sales OU where it should be applied.</p>
            </li>
        </ul>
    </li>
    <li><strong>Force Group Policy Update (Optional)</strong>
        <p>To apply the changes immediately, you can force an update on the target machines by running <code>gpupdate /force</code> in the command prompt.</p>
    </li>
    <li><strong>Verify and Troubleshoot</strong>
        <ul>
            <li><strong>Verify</strong>
                <p>Log on to a user account within the Sales OU and check if the wallpaper has been applied.</p>
            </li>
            <li><strong>Troubleshoot</strong>
                <p>If the wallpaper is not applied, verify the network path to the wallpaper, ensure the users have read access to the shared folder, and check for any conflicting policies.</p>
            </li>
        </ul>
    </li>
</ol>

<h3>Best Practices</h3>
<ul>
    <li><strong>Consistent Naming:</strong> Ensure all shared resources follow a consistent naming convention for easy identification.</li>
    <li><strong>Permissions Management:</strong> Regularly review and update the shared folder permissions to maintain security.</li>
    <li><strong>User Education:</strong> Inform users about the new policy and how it will affect their desktop environment.</li>
    <li><strong>Documentation:</strong> Maintain detailed documentation of all GPO settings and changes for future reference.</li>
</ul>

<br />




<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
