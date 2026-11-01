<h1 align="center"> Configure Department-Specific Desktop Wallpapers </h1>


---


### Table of Contents

- [1. Prepare the wallpaper images](#1-prepare-the-wallpaper-images)

- [2. Create the central Wallpapers folder](#2-create-the-central-wallpapers-folder)
  - [Open File Explorer on DC01](#open-file-explorer-on-dc01)
  - [Create the Wallpapers folder](#create-the-wallpapers-folder)

- [3. Share the Wallpapers folder](#3-share-the-wallpapers-folder)
  - [Open the folder properties](#open-the-folder-properties)
  - [Enable folder sharing](#enable-folder-sharing)
  - [Configure NTFS permissions](#configure-ntfs-permissions)

- [4. Open Group Policy Management](#4-open-group-policy-management)

- [5. Create Wallpaper on each department](#5-create-wallpaper-on-each-department)
  - [Create the HR Wallpaper GPO](#create-the-hr-wallpaper-gpo)
  - [Create the GPO](#create-the-gpo)
  - [Edit the policy](#edit-the-policy)
  - [Navigate to the wallpaper setting](#navigate-to-the-wallpaper-setting)
  - [Configure Desktop Wallpaper](#configure-desktop-wallpaper)
  - [Create the IT Wallpaper GPO](#create-the-it-wallpaper-gpo)
  - [Upgrade](#upgrade)
  - [Then restart it](#then-restart-it)

- [6. Verify employee accounts are in the correct OUs](#6-verify-employee-accounts-are-in-the-correct-ous)

- [7. Apply the Group Policies on users each department](#7-apply-the-group-policies-on-users-each-department)
  - [Sign in as the HR user](#sign-in-as-the-hr-user)
  - [Sign in to Pe Pe](#sign-in-to-pe-pe)
  - [Sign in as the IT user](#sign-in-as-the-it-user)
  - [Signin to C.Ronaldo](#signin-to-cronaldo)
  - [Sign in to Marcelo](#sign-in-to-marcelo)

---

## 1. Prepare the wallpaper images


In this first we need to test with walkpaper.

So in this I use this for my **IT** and **HR** walkpaper:

- **HR Wallpaper**:

<img width="1672" height="941" alt="HR_Wallpaper" src="https://github.com/user-attachments/assets/09ba4e34-e678-4a3f-841c-d1d64cad744f" />



- **IT_Wallpaper**:

<img width="1671" height="941" alt="IT_Wallpaper" src="https://github.com/user-attachments/assets/235858ae-f982-4d23-a5ac-73d2ba5d4675" />



In this I move it to my **Windows Server**.


So this my image walkpaper:

<img width="1915" height="946" alt="image" src="https://github.com/user-attachments/assets/5d6c8bdb-5f11-4eae-aba8-0bb59eb1f003" />


---



## 2. Create the central Wallpapers folder

In this we will put all images in one central location so every domain user can access the correct image.



### Open File Explorer on DC01

On **Windows Server**, Open **File Explorer** and navigate to:
````
C:\Shares
````
<img width="1917" height="790" alt="image" src="https://github.com/user-attachments/assets/fb4c3bbb-614f-4fac-b847-e5e840f2441b" />


### Create the Wallpapers folder

``Right-click`` an empty area:

<img width="1355" height="810" alt="image" src="https://github.com/user-attachments/assets/c5471a75-13d6-42a8-aa6e-1a17076902ab" />


Then name it to:
````
Wallpapers
````

<img width="1141" height="771" alt="image" src="https://github.com/user-attachments/assets/3b3d58fa-c10b-4d28-a839-5eb8bfdb5212" />


Then copy our image walkpaper into our `C:\Shares\Wallpapers`:

<img width="1236" height="813" alt="image" src="https://github.com/user-attachments/assets/7457ecf1-ffd1-466e-8eac-72b25673fb8d" />


Now we was copied to our walkpaper folder.


Then change extension to `.jpg`:

<img width="1077" height="797" alt="image" src="https://github.com/user-attachments/assets/27497524-c2ec-4cf2-86ee-39a291866bbd" />


<img width="1147" height="581" alt="image" src="https://github.com/user-attachments/assets/373dfdc2-8eb3-40fa-a94f-772568c618a0" />


Then change to `.jpg`, just `Double-Click` on each -> click on `File` -> `Save as`:



---


## 3. Share the Wallpapers folder

Now we make the images accessible to domain users.


### Open the folder properties

`Right-Click` on `Wallpapers`, then select **Properties**:

<img width="1402" height="817" alt="image" src="https://github.com/user-attachments/assets/c6867784-5b35-45f4-97d0-577a89d9081f" />


<img width="482" height="591" alt="image" src="https://github.com/user-attachments/assets/3177bf3f-0e9a-46de-ae0a-6c39ac9d0ed2" />

<img width="1515" height="742" alt="image" src="https://github.com/user-attachments/assets/713c8116-b836-4a78-b053-120c6536aca1" />


<img width="937" height="592" alt="image" src="https://github.com/user-attachments/assets/6549322c-73fe-4fea-abcb-501070957ede" />


<img width="1411" height="743" alt="image" src="https://github.com/user-attachments/assets/be454f2a-532a-4d25-9c35-ce54465d8e62" />


Now we have ready changed.



---

### Enable folder sharing

Tick **Share this folder**, In Share name, enter:
````
Wallpapers
````
Then click **Permissions**:

<img width="480" height="597" alt="image" src="https://github.com/user-attachments/assets/31af8df1-8169-4291-a018-b9d618dbc2ec" />


<img width="452" height="557" alt="image" src="https://github.com/user-attachments/assets/d8fa7772-1e68-4830-a7ab-7722ab5ddfb5" />



<img width="452" height="557" alt="image" src="https://github.com/user-attachments/assets/4da7ceef-23c3-4a82-816d-039cef80f58a" />


Then enter:
````
Domain Users
````

<img width="567" height="310" alt="image" src="https://github.com/user-attachments/assets/2cc9df75-a299-41eb-b823-3d44584efbc6" />


<img width="452" height="556" alt="image" src="https://github.com/user-attachments/assets/e516315a-bc59-4833-9345-6c96b3f408ab" />


Then enter:
````
Administrators
````
<img width="566" height="475" alt="image" src="https://github.com/user-attachments/assets/d49c6ac5-a6b5-48f2-9d18-aab44b95128b" />


<img width="457" height="561" alt="image" src="https://github.com/user-attachments/assets/e346a599-1bec-48e8-9753-bbbc20746c35" />


<img width="437" height="455" alt="image" src="https://github.com/user-attachments/assets/8ac60a9f-a8f1-4f01-a20e-ad026dc18405" />


<img width="480" height="597" alt="image" src="https://github.com/user-attachments/assets/9bc8c532-8266-4217-b2b1-dbb5c7d401fe" />



---


### Configure NTFS permissions

In this we must also configure the Security permissions because Windows uses both Share and NTFS permissions.


Then click on **Security** tab:

<img width="481" height="596" alt="image" src="https://github.com/user-attachments/assets/f216d106-59e9-486c-9115-c703a5b45d12" />


<img width="487" height="595" alt="image" src="https://github.com/user-attachments/assets/3ef3d03d-c76b-4e9a-9b2e-a0f23b7968aa" />


<img width="1020" height="632" alt="image" src="https://github.com/user-attachments/assets/61d0a94e-6cbd-4e04-91f8-f9107753c94b" />



<img width="1222" height="731" alt="image" src="https://github.com/user-attachments/assets/349f1185-fde3-417e-973b-32225ed70ee9" />



Then enter:
````
Domain Users
````
<img width="605" height="307" alt="image" src="https://github.com/user-attachments/assets/1558de4c-4134-4922-b2bf-1d49050280f6" />



<img width="1217" height="726" alt="image" src="https://github.com/user-attachments/assets/a623d752-783b-48e6-b922-fa5578434df8" />


<img width="1012" height="632" alt="image" src="https://github.com/user-attachments/assets/a973ac7c-99e7-4050-98b8-a47a83d037f0" />


<img width="482" height="595" alt="image" src="https://github.com/user-attachments/assets/e1d945cd-4aca-474a-b3c0-b6f8f1c8e0d3" />


Now we completed.


---


## 4. Open Group Policy Management

Now we will configure the policies.

Open **Server Manager**:

<img width="1917" height="877" alt="image" src="https://github.com/user-attachments/assets/10217cc1-e49c-448d-8c42-82523a741a12" />



<img width="1135" height="723" alt="image" src="https://github.com/user-attachments/assets/f5e74279-a4a6-4b75-84ae-85a5ee84f6c6" />


Or in this we can use short by, just press ``Windows + R`` then type:
````
gpmc.msc
````

---


After we going to **Group Policy (GPO)**, then expand all on our domain:


<img width="967" height="612" alt="image" src="https://github.com/user-attachments/assets/ddd6e75a-02e7-41e8-a450-8f50f2cdbb61" />


---


## 5. Create Wallpaper on each department 

### Create the HR Wallpaper GPO

#### Create the GPO
Find the **HR** OU under **Staff**, ``Right-click`` on **HR** -> Select **Create a GPO in this domain, and Link it here**:

<img width="940" height="827" alt="image" src="https://github.com/user-attachments/assets/2b334956-a725-40d9-8b37-5b3eb49dabc9" />


Then enter:
````
GPO-HR-Desktop-Wallpaper
````

<img width="476" height="227" alt="image" src="https://github.com/user-attachments/assets/3347282d-1072-4b0c-83d3-208c09d9f467" />


<img width="1916" height="671" alt="image" src="https://github.com/user-attachments/assets/7b196582-090c-4c17-88f3-c93fda9ec26b" />



Now we have now created a policy linked to the HR OU.


#### Edit the policy


`Right-Click` on **GPO-HR-Desktop-Wallpaper**:

<img width="1912" height="662" alt="image" src="https://github.com/user-attachments/assets/a00070ab-7fbb-4e0a-ae89-9cc82a41faa6" />



#### Navigate to the wallpaper setting

````
User Configuration
    └── Policies
        └── Administrative Templates
            └── Desktop
                └── Desktop
````

<img width="1532" height="590" alt="image" src="https://github.com/user-attachments/assets/e07cb4f7-75ff-42a3-a7d5-8331e4e9abb3" />


In the right panel, find:
````
Desktop Wallpaper
````
This is a User Configuration policy, so it applies to users in the HR OU rather than being selected according to the computer's OU.


#### Configure Desktop Wallpaper

``Double-click`` on **Desktop Wallpaper**:

<img width="1515" height="860" alt="image" src="https://github.com/user-attachments/assets/3dce854b-beef-4337-9819-c05f3b5a42b2" />


Then input **Wallpaper Name**:
````
\\DC01\Wallpapers\HR_Wallpaper.jpg
````

<img width="854" height="795" alt="image" src="https://github.com/user-attachments/assets/112272ca-7a02-4cdc-a50f-4429a153d393" />


Now it `Enabled`:
<img width="1547" height="872" alt="image" src="https://github.com/user-attachments/assets/ee5acdcc-f5da-45ca-b6c7-20eadd6a65df" />



Now we completed to set wallpaper on **HR**.


---



### Create the IT Wallpaper GPO

Now repeat the same process for the IT department.

``Right-click`` on **IT**, then select **Create a GPO in this domain, and Link it here**:

<img width="920" height="825" alt="image" src="https://github.com/user-attachments/assets/14ed91bf-13be-41b6-abcc-b740cca30978" />


Then enter:
````
GPO-IT-Desktop-Wallpaper
````
<img width="476" height="222" alt="image" src="https://github.com/user-attachments/assets/0468dd7e-02d1-4717-af62-d54a6a88e3bd" />


<img width="1917" height="657" alt="image" src="https://github.com/user-attachments/assets/22f6923a-c419-4758-83b2-870915b9a247" />


<img width="1917" height="877" alt="image" src="https://github.com/user-attachments/assets/2daf23a0-4bf2-4cb9-aeb4-2bec0ca1dcaa" />


Then ``Double-click`` on **Desktop Wallpaper**, click on **Enable** then enter:
````
\\DC01\Wallpapers\IT_Wallpaper.jpg
````

<img width="852" height="792" alt="image" src="https://github.com/user-attachments/assets/e4b4d510-af18-4b3e-8aec-d7ba862435b0" />


<img width="1917" height="868" alt="image" src="https://github.com/user-attachments/assets/1eca1d1a-e689-4abb-b6bc-8a35a4ce95f1" />


Now we was enabled.


#### Upgrade:
open **Command Prompt** as **Administrator**, then type:
````cmd
C:\Users\Administrator> gpupdate /force
Updating policy...

Computer Policy update has completed successfully.
User Policy update has completed successfully.
````


Then restart it.
---



## 6. Verify employee accounts are in the correct OUs

On **Windows Server**, open **PowerShell** as **Administrator**, then enter:
````ps1
PS C:\WINDOWS\system32> Get-ADUser pe.pe -Properties DistinguishedName | Select-Object Name,DistinguishedName           
Name  DistinguishedName
----  -----------------
Pe Pe CN=Pe Pe,OU=HR,OU=Staff,OU=NetLab Company,DC=netlab,DC=com
````


For Cristiano:
````ps1
PS C:\WINDOWS\system32> Get-ADUser c.ronaldo -Properties DistinguishedName | Select-Object Name,DistinguishedName

Name              DistinguishedName
----              -----------------
Cristiano Ronaldo CN=Cristiano Ronaldo,OU=IT,OU=Staff,OU=NetLab Company,DC=netlab,DC=com
````


For Marcelo:
````ps1
PS C:\WINDOWS\system32> Get-ADUser v.marcelo -Properties DistinguishedName | Select-Object Name,DistinguishedName

Name           DistinguishedName
----           -----------------
Vieira Marcelo CN=Vieira Marcelo,OU=IT,OU=Staff,OU=NetLab Company,DC=netlab,DC=com
````

Now all three employee accounts are located in the correct Active Directory Organizational Units (OUs).

---



## 7. Apply the Group Policies on users each department


### Sign in as the HR user

#### Sign in to Pe Pe

So in this I sign is into user ``pe.pe``, and our `pe.pe` password:
````
@p33p33
````
<img width="1917" height="930" alt="image" src="https://github.com/user-attachments/assets/aa017226-e2fd-415c-ac85-b6b5e16b814e" />


After signed in now we got new wallpaper:

<img width="1917" height="940" alt="image" src="https://github.com/user-attachments/assets/b549ac9a-73fa-4ba4-b186-77e7eb614c4d" />



Now we got got successful to set wallpaper.

> **Note**: In this I show password of user just for lab not passowrd use real life.

---


### Sign in as the IT user

#### Signin to C.Ronaldo

In this sign in to user `c.ronaldo`, and password is:
````
@R0n41d0
````

<img width="1917" height="930" alt="image" src="https://github.com/user-attachments/assets/01a0935f-b809-447b-906a-8a6ea6ceec66" />


<img width="1917" height="937" alt="image" src="https://github.com/user-attachments/assets/023accbc-c1a0-462f-89b9-943084922574" />


Now we was successful to set wallpaper.


---


#### Sign in to Marcelo

In this we need to sign in into user ``v.marcelo``:
````
@M4rc310
````
<img width="1917" height="936" alt="image" src="https://github.com/user-attachments/assets/3f5a20ef-afba-4bec-870e-665ad9a59d4e" />


Now we got successful to set wallpaper:

<img width="1917" height="946" alt="image" src="https://github.com/user-attachments/assets/621ff30b-1581-4bf1-b616-d55fd1433ab8" />


Now we completed the lab.


-----
