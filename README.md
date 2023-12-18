  <h2>Utilization of Active Directory</h2>


  
  - Load up Server Manager from the start menu at the bottom left corner
  - Once in Server Manager, select "Tools" from the top right
  - Under Tools, select "Active Directory Users and Computers"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d4a2459d-5ea6-4e3d-b5ae-bb86179e6d83)
- We can now create organization units by right clicking "www.mydomain.com", hovering over new, and selecting "organizational unit"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/fac3b8bf-054f-4690-9d72-501f96c715d5)
- We can now create our first user by clicking our organization unit "_EMPLOYEES"
- Right-clicking anywhere in the blank space
- Hovering over new and selecting "user"
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/eb316b28-e1b5-4121-8ad6-5ec7cb6d607f)
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/22f5479d-72a1-4823-9f86-a9781d7f0da6)
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d6e31ff2-0b88-4301-867d-2eaa6b1b01a2)
- We can now create a security group for the Accounting department and add Jane Doe to the group
- Select "Users"
- Right-click in the blank space and hover over "New"
- Select "Group"
- We will name the group "Accounting" and make sure it is a security group
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/2c6e60c4-d11d-452c-92e4-8979be9c7997)
- Now, we can add Jane Doe to the Accounting Security Group
- Select "Employees"
- Right-clik on Jane Doe
- Select "Add to Group" and we will type in Accounting
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d0055219-bc48-4f0d-b272-44626e52b05b)
- We will now add 1,000 users into an OU called "_EMPLOYEES_FROM_PS"
  - Be sure to open Powershell ISE from the start menu
  - Select the white paper logo under "File"
  - Copy and paste the script into Powershell
  - Press the green arrow to run the script
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/b1478b27-7cd7-45ea-a2a3-e3533d8525ac)
- We can now select the "_EMPLOYEES_FROM_PS" OU
- Right-click on any random user created and select "Reset Password"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/ce7d1766-28e9-4ade-a2b5-61339688dc0e)
- If we want to ensure that their password must be rest upon login, we can double-click on any random user
- Select the "Account" tab
- Make sure that "User must change password at next logon" is checked
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/a5a1cc7a-6459-4d57-9490-8c76c6af0de5)
- We can also disable accounts by right-clicking on the user and selecting "disable account"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/2ec234d4-6c1b-4bd9-9c82-9dba824fd5ae)
- We can also unlock a user's account by double-clicking on their name, selecting the "Account" tab, and checking "Unlock Account"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/fd8ce371-d28f-4f43-a16e-293cd6ebf6fd)

- Step 8
  - We will now connect our VM2 (Client) to our Domain (VM1)
  - First, we need to change the DNS server to match the private IP address of VM1, rather than the virtual network DNS
    - The DNS must match the domain controller's private IP address to connect to the domain
  - In Azure, go to the client VM and select the "Networking" tab on the left 
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/854d3f2a-f222-421c-a15d-48a08a6de574)
- Select DC-1-vnet/default, which is to the right of "Virtual network/subnet:"
- From there, select "DNS Servers" tab on the left, and choose "custom" under DNS servers
  - Input the private IP Address of VM1 (Domain Controller) and select "save"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/c2a32a4e-bdd6-44ab-9782-06210c03a9e5)
- Be sure to restart the client VM
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/3713ed54-7419-49c0-853c-405bf0bfdf3f)
- Remote into the Client VM
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/937f6abd-5a7e-4b22-a7a3-8f20f8f5872c)
- Right-click on the Windows logo in the bottom left corner and select "System"
- Under "Related Settings", select "Rename this PC (Advanced)"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/db974659-d0a8-47c7-99ae-6a6c3a2ba13e)
- Below Network ID, select the "Change" button and input your domain name
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d60030e2-601c-4fe1-9972-59071ea9bbb7)
- Since we created 1,000 accounts on the DC, we will use one of those accounts to connect the Client to the Domain
  
 ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/028b8ea0-164a-4b79-b59d-8385ab237b2b)
- We can now see that our Client-VM is connect to our Domain Controller
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/e42753a7-3a6a-4374-8b34-a277378850af)
- Log out of the session and sign-on using one of the accounts made in AD

- Step 9
   - We will now allow users to remotely access the domain
   - Go to system settings, under Related Settings, select "Remote Desktop"
   - Select at the bottom - "Select users who can remotely access this PC"
   - Be sure to add "Domain Users"
     ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/42870c26-fd05-453a-ad06-c9763283a28f)
- We can now log in with the bat.juko account from VM2 and access the Active Directory Domain 
