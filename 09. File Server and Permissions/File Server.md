<h1 align="center"> File Server </h1>


---



## 1. verify the File Server role using Server Manager

In **Winndows Server** -> Open **Server Manager**:

<img width="1917" height="782" alt="image" src="https://github.com/user-attachments/assets/623b40ad-b0f2-4711-804c-60b4f582d840" />


<img width="1919" height="737" alt="image" src="https://github.com/user-attachments/assets/c0a43652-db43-4b9d-8331-a2a9c6f008c1" />


> Now we saw now see the Shares management page.

---




## 2. Create the folder for sharing

Before sharing folders, we need to create the actual folders on the server.

In this we will use **File Explorer**.

In this first open **File Explorer**, by just press `Windows + E` or Click on normal:

<img width="930" height="647" alt="image" src="https://github.com/user-attachments/assets/5a5001bd-dd18-431f-9228-cdac2f634047" />


### Create a parent folder

Inside **C:**, ``Right-Click`` an empty area:

<img width="1007" height="672" alt="image" src="https://github.com/user-attachments/assets/4252b670-c1a2-4ec5-81fb-b6e8a6a408fd" />


Then name is:
````
Shares
````
<img width="980" height="667" alt="image" src="https://github.com/user-attachments/assets/51e8178a-7237-4bf1-a2c9-1337d5df0eba" />


Now we see our folder `Shares`.

---

### Create the company folder

Open `C:\Shares`, then create another folder named, by just press `Ctrl + Shift + N`:
````
NetLab Company
````
<img width="945" height="637" alt="image" src="https://github.com/user-attachments/assets/87bcf0b6-edb2-452b-82aa-a0e9a1d13ed7" />


---


### Create the four department folders

Open ``NetLab Company``, then create these four folders individually:

| Folder name | Purpose                                             |
| ----------- | --------------------------------------------------- |
| HR          | Human Resources department                          |
| IT          | Information Technology department                   |
| General     | Shared resources for all employees                  |
| Management  | Management documents                                |

<img width="927" height="641" alt="image" src="https://github.com/user-attachments/assets/69adc2f9-8d1a-442b-93d3-8c8ceeb7db73" />


---



## 3. Create the Active Directory security groups manually

In this we need security groups so that access can be managed centrally.

Instead of adding our user that we was create directly to every folder's permissions, we will put them into groups.

This is more manageable and follows the Global-to-Domain-Local group nesting approach.


### Create the Groups Organizational Unit

On **Windows Server**, open **Server Manager**: 

<img width="1917" height="767" alt="image" src="https://github.com/user-attachments/assets/e9d64d83-3830-4523-8d1c-d459750d0f26" />

Or we can press `Windows + R`, then enter:
````
dsa.msc
````

Then ``Right-click`` on **NetLab Company**:

<img width="895" height="592" alt="image" src="https://github.com/user-attachments/assets/d3c8b6d8-830e-4f86-aafc-d649a468cd3c" />


Then enter `Groups`:

<img width="435" height="382" alt="image" src="https://github.com/user-attachments/assets/253c4232-dc87-4f94-8cf9-347b9ee07be7" />


---


### Understand Global and Domain Local groups

In this we will create two types of security groups:

| Group type                  | Purpose                                             |
| --------------------------- | --------------------------------------------------- |
| Global Security Group       | Contains department employees                       |
| Domain Local Security Group | Receives permissions to a folder or shared resource |

> In this this allows us to change HR membership without editing the folder permissions every time.



### Create four Global Security Groups


``Right-click`` on **Groups** → **New** → **Group**:

<img width="750" height="722" alt="image" src="https://github.com/user-attachments/assets/98b85aeb-a9ae-4877-8677-6ffbb7dd3e03" />

The input it:
````
GG_HR
````
<img width="436" height="377" alt="image" src="https://github.com/user-attachments/assets/037fd036-f15e-4dbf-ba5e-11e97ba34b66" />


<img width="952" height="431" alt="image" src="https://github.com/user-attachments/assets/795fa8db-a4de-4760-a379-56b4bd5c3bc1" />


Now we got group `GG_HR`.


Then repeat it and creat all following this:

**Global Security groups**:

| Group name      | Members              |
| --------------- | -------------------- |
| `GG_HR`         | HR employees         |
| `GG_IT`         | IT employees         |
| `GG_Finance`    | Finance employees    |
| `GG_Compliance` | Compliance employees |
| `GG_Marketing`  | Marketing employees  |
| `GG_Sales`      | Sales employees      |
| `GG_General`  | All employees        |
| `GG_Management` | Managers             |

<img width="962" height="452" alt="image" src="https://github.com/user-attachments/assets/0376a0b2-7f93-4b6a-b694-c54bf90602bd" />



**Domain Local Security groups**:

| Group name             | Nest this GG group | Folder     |
| ---------------------- | ------------------ | ---------- |
| `DL_HR_Modify`         | `GG_HR`            | HR         |
| `DL_IT_Modify`        | `GG_IT`             | IT         |
| `DL_General_Modify`    | `GG_General`       | General    |
| `DL_Management_Modify` | `GG_Management`    | Management |

<img width="437" height="377" alt="image" src="https://github.com/user-attachments/assets/6aef0c92-7b2c-4111-8bdc-a4d3772963ac" />


Then repeat it all like this all group.

Now we completed to create all group:

<img width="940" height="432" alt="image" src="https://github.com/user-attachments/assets/1b95a2dd-4e21-462a-9758-f947c77f65bb" />



----


## 4. Add employees to each groups

In this after we ready created groups, then assign it to our departments.


### Add employees to the Global Security Groups

#### Add Pe Pe to GG_HR

`Double-Click` on **GG_HR**, then select **Member** -> click on **Add**:

<img width="965" height="431" alt="image" src="https://github.com/user-attachments/assets/2e9eb282-f984-4fc3-9824-85af8f2b93b5" />


<img width="397" height="457" alt="image" src="https://github.com/user-attachments/assets/5c210e85-1cf8-4825-99c2-7465d0902a71" />


then enter:
````
pe.pe
````
<img width="457" height="251" alt="image" src="https://github.com/user-attachments/assets/d9242a4f-558f-4c8f-93c4-5c19cbeebaf6" />


<img width="460" height="252" alt="image" src="https://github.com/user-attachments/assets/08076dce-e5da-4741-877d-33cdb9c656e0" />


<img width="400" height="457" alt="image" src="https://github.com/user-attachments/assets/ea8ac2b9-f7ef-47d6-a62d-28290e583d34" />


Now we completed.


---


#### Add Vieira Marcelo to GG_IT

`Double-Click` on **GGG_IT**, click on **Member**:

<img width="1102" height="442" alt="image" src="https://github.com/user-attachments/assets/7addd6f7-4e89-4e93-b0da-96d5c660c818" />



<img width="397" height="457" alt="image" src="https://github.com/user-attachments/assets/fa58e11c-4ccc-4f5f-b0c9-34ae568467de" />


Then enter:
````
c.ronaldo
````
<img width="457" height="246" alt="image" src="https://github.com/user-attachments/assets/14987158-e65d-4973-9128-86c2ff967c29" />


<img width="457" height="255" alt="image" src="https://github.com/user-attachments/assets/b0fae12a-ce08-4bef-8eba-2ecf19408ea8" />


Then add user **Marcelo**:

<img width="402" height="462" alt="image" src="https://github.com/user-attachments/assets/15799f6a-e574-4969-a5c8-a877ec4819b0" />



<img width="457" height="252" alt="image" src="https://github.com/user-attachments/assets/6c337c2d-f559-438a-8e14-ac70b119406b" />


<img width="447" height="257" alt="image" src="https://github.com/user-attachments/assets/e6472be5-dd96-4a43-b870-c5e6417709e6" />


<img width="400" height="455" alt="image" src="https://github.com/user-attachments/assets/2df235aa-13ee-4341-9f1a-307f432324d9" />


Now we completed to add member.

---


#### Add Vieira to GG_Management

`Double-Click` on **GG_Management**, then select **Members** -> click **Add**:

<img width="1122" height="422" alt="image" src="https://github.com/user-attachments/assets/bbe5d0d3-27da-43d1-a432-5f95155ed3e0" />


<img width="397" height="451" alt="image" src="https://github.com/user-attachments/assets/fffcea29-a191-4797-b098-9194f15d5eb3" />


<img width="457" height="247" alt="image" src="https://github.com/user-attachments/assets/33b68ebd-88ef-4c92-bb35-7cdc4f4ac181" />


<img width="452" height="251" alt="image" src="https://github.com/user-attachments/assets/7cb754f3-3742-43e9-8ce6-3ba8430b2031" />


<img width="400" height="456" alt="image" src="https://github.com/user-attachments/assets/d181747d-cc8c-48a9-a22b-3f3eeab51a87" />



Now Vieira is a member of both ``GG_IT`` and ``GG_Management``.

---


### Add department groups to GG_General

Instead of adding every employee individually to ``GG_General``, we will nest the six department Global Security Groups inside it.

That way, when we add a new user to **GG_General**, that employee automatically becomes a member of GG_All_Staff through group nesting.


Open **GG_General**

``Double-click`` on **GG_General**, then Select **Members** -> Click **Add**

<img width="1086" height="427" alt="image" src="https://github.com/user-attachments/assets/c8be162a-6050-4cda-a32d-eeb1a925235c" />


<img width="395" height="452" alt="image" src="https://github.com/user-attachments/assets/a53fc1d0-0abb-4576-8391-5a1cca4d1eac" />



#### Add GG_HR

After step above then enter:
````
GG_HR
````
<img width="455" height="247" alt="image" src="https://github.com/user-attachments/assets/3f16b2c0-eca0-44f8-b1db-aaaa78869ebf" />


<img width="455" height="252" alt="image" src="https://github.com/user-attachments/assets/2b694753-65b1-4424-858b-a5a5e3334c14" />


<img width="393" height="456" alt="image" src="https://github.com/user-attachments/assets/54251b22-cc59-4402-8b2d-e867b12736f0" />


Now we finished.

#### Add the remaining department groups

Repeat for each:
````
GG_IT
````
````
GG_Finance
````
````
GG_Compliance
````
````
GG_Marketing
````
````
GG_Sales
````

<img width="402" height="455" alt="image" src="https://github.com/user-attachments/assets/7dde13f9-4fe4-4f1e-a4c5-6798644aa27c" />



> Make sure all six Global groups appear in the **Members** tab.


#### Verify GG_General

``Double-click`` on **GG_General** → **Members**:

<img width="1340" height="560" alt="image" src="https://github.com/user-attachments/assets/34c9e26c-0197-4133-ad3d-d13a0c887500" />


Now we see all departments.


---


### Nest Global Groups into Domain Local Groups

Now in this we will connect the Global groups to the resource groups.

This is how a user's department membership eventually gives the user folder access.



#### Configure DL_HR_Modify
``Double-click`` on **DL_HR_Modify**, then Select **Members** -> Click **Add**:

<img width="1116" height="435" alt="image" src="https://github.com/user-attachments/assets/408b5ae4-afc0-4b92-b50e-e4cab2a1935e" />


<img width="397" height="455" alt="image" src="https://github.com/user-attachments/assets/480c4030-70ed-4e63-9a7e-31ba312624a6" />


Enter:
````
GG_HR
````
<img width="451" height="250" alt="image" src="https://github.com/user-attachments/assets/096f40f8-0aad-4039-ba88-e6b6c8b96f00" />


<img width="452" height="247" alt="image" src="https://github.com/user-attachments/assets/3ee66bbf-355d-490d-86a9-68f96f2c5d59" />


<img width="400" height="457" alt="image" src="https://github.com/user-attachments/assets/d196bb42-87dc-4ca7-8990-635c674a433a" />


---

#### Configure DL_IT_Modify

`Double-Click` on **DL_IT_Modify** → **Members** → **Add**:

<img width="397" height="452" alt="image" src="https://github.com/user-attachments/assets/b0338fd6-ad70-447c-99ae-83b7ec19da2f" />


Then enter:
````
GG_IT
````
<img width="457" height="252" alt="image" src="https://github.com/user-attachments/assets/571f1931-7a53-4a89-a70d-2f9f8e3f35e0" />


<img width="397" height="455" alt="image" src="https://github.com/user-attachments/assets/198574c1-a5db-4a4e-b372-7569a86e4c04" />


---


#### Configure DL_General_Modify

``Double-Click`` on **DL_General_Modify** → **Members** → **Add**:

Then enter:
````
GG_General
````
<img width="886" height="460" alt="image" src="https://github.com/user-attachments/assets/5c9531dc-5375-4e87-8b46-7f634ef3d34a" />


<img width="395" height="452" alt="image" src="https://github.com/user-attachments/assets/3c9e7676-6535-4650-876c-c752662b7cff" />



Now all department employees will inherit General folder access through nested group membership.

---


#### Configure DL_Management_Modify

`Double-Click` on **DL_Management_Modify** → **Members** → **Add**:

Then enter:
````
GG_Management
````
<img width="861" height="457" alt="image" src="https://github.com/user-attachments/assets/49f12e11-4ba7-4d12-919d-c84e8bef6c06" />


<img width="392" height="450" alt="image" src="https://github.com/user-attachments/assets/c2985894-a064-4271-8f03-26ac36e6c992" />


> Only managers in **GG_Management** will inherit access to the Management folder.


---


## 5. Configure NTFS folder permissions

Now that security groups are ready, create the folders on our Windows Server.


Open **File Explorer**, then press `Windows + E`:

Then go to folder that we was create:
````
C:\Shares\NetLab Company
````

<img width="905" height="622" alt="image" src="https://github.com/user-attachments/assets/91f8fbe8-6835-4c39-970a-d221e32a629c" />



In this we restrict each folder to its correct Domain Local group.


**NTFS permissions:**
| Permission   | Function                                              |
| ------------ | ----------------------------------------------------- |
| Read         | Open and read files                                   |
| Write        | Create or write files                                 |
| Modify       | Read, create, edit, rename, and delete files          |
| Full Control | Modify plus change security permissions and ownership |

---


### Configure the HR folder

Open `C:\Shares\NetLab Company`, then ``Right-click`` on **HR**:

<img width="1082" height="630" alt="image" src="https://github.com/user-attachments/assets/3b35a41a-234b-4d99-9ede-2ef613349340" />


Select **Security**, click **Advanced**:

<img width="360" height="482" alt="image" src="https://github.com/user-attachments/assets/efbc62ea-2dea-48fc-86b6-d675abbf5f8e" />


Then click on **Disable inheritance**:

<img width="757" height="517" alt="image" src="https://github.com/user-attachments/assets/83db0d16-8a34-446e-8129-1fe674f88f4c" />


Then select ``Convert inherited permissions into explicit permissions``:

<img width="517" height="282" alt="image" src="https://github.com/user-attachments/assets/f6d01de9-6311-4238-9791-b43b9b78290a" />


Then remove this user:

<img width="762" height="517" alt="image" src="https://github.com/user-attachments/assets/a604e661-e121-4524-9c7f-c9eaf7c60ab3" />


Then click on **Add**:

<img width="765" height="517" alt="image" src="https://github.com/user-attachments/assets/68c2ecd1-8157-43cf-852d-ba34c8294d69" />



<img width="917" height="595" alt="image" src="https://github.com/user-attachments/assets/cc0895a4-db81-4634-9ec6-714e6f324e66" />


Then enter:
````
DL_HR_Modify
````
<img width="455" height="252" alt="image" src="https://github.com/user-attachments/assets/ec08bea9-3acb-4358-b9f3-5f93bb650d8c" />


<img width="917" height="592" alt="image" src="https://github.com/user-attachments/assets/64d83934-d31a-42ec-981f-1789e414d90f" />


<img width="762" height="517" alt="image" src="https://github.com/user-attachments/assets/258c666e-b9ea-45bc-a438-15dd860cdc9b" />


<img width="356" height="481" alt="image" src="https://github.com/user-attachments/assets/422c1b1e-2023-43af-beb0-e0c40ea19754" />


Now we completed.

---



### Configure the ICT folder


Open **File Explorer**, then go to:
````
C:\Shares\NetLab Company
````
``Right-Click`` on **IT**:
<img width="1110" height="637" alt="image" src="https://github.com/user-attachments/assets/c64f9c19-2482-4802-bf6b-9aa165372987" />


<img width="362" height="482" alt="image" src="https://github.com/user-attachments/assets/087e2812-b1e0-41c8-9ee5-1447eccb3f0d" />


Then click `Disable inheritance`:

<img width="762" height="520" alt="image" src="https://github.com/user-attachments/assets/abdfd84b-6136-4a83-a870-0674ee39fd39" />


<img width="517" height="276" alt="image" src="https://github.com/user-attachments/assets/0eaf9c1c-b6b4-49fe-8a8c-e846eb4f5293" />


Then delete this user:

<img width="761" height="520" alt="image" src="https://github.com/user-attachments/assets/1ac51d84-1471-446b-b44f-7c4489a00c96" />


Just click on it then click on **Remove**:

<img width="762" height="517" alt="image" src="https://github.com/user-attachments/assets/810f83db-7b70-45f3-aa0b-a4dd83ac965f" />


Then click on **Add**:

<img width="762" height="516" alt="image" src="https://github.com/user-attachments/assets/8998535b-22cb-43ed-b0d4-1d1292d57e3e" />


<img width="912" height="595" alt="image" src="https://github.com/user-attachments/assets/b3e4355a-5485-4df0-bb6b-aef989a5beb3" />



Then enter:
````
DL_IT_Modify
````
<img width="457" height="250" alt="image" src="https://github.com/user-attachments/assets/08de0920-8620-41b5-9519-0105b2793c0f" />


<img width="907" height="590" alt="image" src="https://github.com/user-attachments/assets/54445245-bd57-416f-9dd4-d7e975d9ec32" />


<img width="767" height="517" alt="image" src="https://github.com/user-attachments/assets/39541e68-b1e4-4b64-8071-0273fc71aa3d" />


<img width="356" height="482" alt="image" src="https://github.com/user-attachments/assets/99f18280-3617-40a0-8e69-6b7bb8fd77c5" />


Now we completed.

---


### Configure the General folder

In this we do it the same above.

`Right-Click` on **General**:

<img width="1120" height="647" alt="image" src="https://github.com/user-attachments/assets/9e1cfef1-7439-4389-be38-af093083529e" />


<img width="362" height="482" alt="image" src="https://github.com/user-attachments/assets/f45d0416-5f62-470b-9b5f-ba8386bc6619" />


<img width="762" height="522" alt="image" src="https://github.com/user-attachments/assets/e3033c96-c3d3-4800-999f-0e45cf2c69fa" />


<img width="522" height="281" alt="image" src="https://github.com/user-attachments/assets/a6594f78-9fb4-46f8-9c93-42edc498e2b0" />


Then remove all this user:

<img width="770" height="521" alt="image" src="https://github.com/user-attachments/assets/52297e93-025a-4da2-9ef4-cf0f4804a5aa" />


<img width="762" height="517" alt="image" src="https://github.com/user-attachments/assets/caa04439-9b2a-4225-82e2-64100bcf295b" />


<img width="915" height="590" alt="image" src="https://github.com/user-attachments/assets/e298ecb9-21ef-4258-8660-61d624987f4f" />


Then enter:
````
DL_General_Modify
````
<img width="457" height="252" alt="image" src="https://github.com/user-attachments/assets/de7af546-f5ee-4866-b87e-6ce518d4f40f" />


<img width="916" height="595" alt="image" src="https://github.com/user-attachments/assets/bd6d7281-d255-44ed-91ce-ede620db9d63" />


<img width="770" height="515" alt="image" src="https://github.com/user-attachments/assets/15c3956f-2368-42b1-b6cc-16664a674845" />


<img width="362" height="477" alt="image" src="https://github.com/user-attachments/assets/740e2a8c-dc92-4e39-bf05-7f6d4e42fe42" />


Now we completed.

---


### Configure the Management folder

<img width="1117" height="666" alt="image" src="https://github.com/user-attachments/assets/977210ca-7265-4929-a497-bf7b910a8d3a" />



<img width="448" height="480" alt="image" src="https://github.com/user-attachments/assets/71a1a112-fe53-4d1f-8e68-d439ae134be4" />


<img width="765" height="517" alt="image" src="https://github.com/user-attachments/assets/a1b13181-0eb9-43d7-b686-fc8d719583c2" />


<img width="516" height="267" alt="image" src="https://github.com/user-attachments/assets/97556409-8672-414c-a839-bbd80f8dc77e" />


Then remove this user:

<img width="762" height="512" alt="image" src="https://github.com/user-attachments/assets/bea05510-f51f-4583-8f84-b167e3f82227" />


Then click on **Add**:

<img width="762" height="516" alt="image" src="https://github.com/user-attachments/assets/39bd92f7-7411-4adc-b5bb-6f0cc433daec" />


<img width="912" height="587" alt="image" src="https://github.com/user-attachments/assets/b638379e-94f8-4ae9-aa89-80c19d48b931" />



Then enter:
````
DL_Management_Modify
````
<img width="447" height="247" alt="image" src="https://github.com/user-attachments/assets/ca430ce1-3213-418b-928c-0156889e7cd5" />


<img width="912" height="585" alt="image" src="https://github.com/user-attachments/assets/434cf792-ca0f-4316-87ae-1d01574fc437" />


<img width="762" height="517" alt="image" src="https://github.com/user-attachments/assets/31d94fe0-7df5-45d4-9cb0-e46d03491d4a" />



<img width="365" height="475" alt="image" src="https://github.com/user-attachments/assets/08871b12-0c87-463f-b485-bbc3f856e320" />


Now we completed.

---


## 6. Verify all four NTFS permissions

In this after finished the four folders, then open **PowerShell** as **Administrator** onn server:


Then type:
````ps1
PS C:\WINDOWS\system32> icacls "C:\Shares\NetLab Company"
C:\Shares\NetLab Company BUILTIN\Administrators:(F)
                         NT AUTHORITY\SYSTEM:(I)(OI)(CI)(F)
                         BUILTIN\Administrators:(I)(OI)(CI)(F)
                         BUILTIN\Users:(I)(OI)(CI)(RX)
                         BUILTIN\Users:(I)(CI)(AD)
                         BUILTIN\Users:(I)(CI)(WD)
                         CREATOR OWNER:(I)(OI)(CI)(IO)(F)

Successfully processed 1 files; Failed processing 0 files
````


Then in this I want to check it in one command:
````ps1
PS C:\WINDOWS\system32> icacls "C:\Shares\NetLab Company\HR"; icacls "C:\Shares\NetLab Company\ICT"; icacls "C:\Shares\NetLab Company\General"; icacls "C:\Shares\NetLab Company\Management"
C:\Shares\NetLab Company\HR BUILTIN\Administrators:(OI)(CI)(F)
                            NT AUTHORITY\SYSTEM:(OI)(CI)(F)
                            NETLAB\DL_HR_Modify:(OI)(CI)(M)

Successfully processed 1 files; Failed processing 0 files
C:\Shares\NetLab Company\ICT: The system cannot find the file specified.
Successfully processed 0 files; Failed processing 1 files
C:\Shares\NetLab Company\General BUILTIN\Administrators:(OI)(CI)(F)
                                 NT AUTHORITY\SYSTEM:(OI)(CI)(F)
                                 NETLAB\DL_General_Modify:(OI)(CI)(M)

Successfully processed 1 files; Failed processing 0 files
C:\Shares\NetLab Company\Management BUILTIN\Administrators:(OI)(CI)(F)
                                    NT AUTHORITY\SYSTEM:(OI)(CI)(F)
                                    NETLAB\DL_Management_Modify:(OI)(CI)(M)

Successfully processed 1 files; Failed processing 0 files
````

---



## 7. Create the four network shares

Now we will make the folders accessible over the network.

We will create four separate SMB shares, not share the entire parent folder.


Open **Server Manager**:

<img width="1917" height="772" alt="image" src="https://github.com/user-attachments/assets/ffa116fb-c1ad-441f-9ddb-cd2350af215f" />


### Create share folder for HR department:

<img width="1911" height="736" alt="image" src="https://github.com/user-attachments/assets/71640b21-0527-41fa-b802-e797891f6866" />


<img width="757" height="557" alt="image" src="https://github.com/user-attachments/assets/007cdf4e-046f-4c34-9990-837854cb3914" />


<img width="1232" height="892" alt="image" src="https://github.com/user-attachments/assets/e9825580-32bb-4b2f-a22b-f1199dbc7699" />


Then go to:
````
C:\shares\NetLab Company\hr
````
<img width="762" height="560" alt="image" src="https://github.com/user-attachments/assets/2dc23171-e591-4699-a46f-d59496b514b0" />


<img width="755" height="555" alt="image" src="https://github.com/user-attachments/assets/917d4221-fece-4743-a425-39214d2ef6f8" />


<img width="761" height="562" alt="image" src="https://github.com/user-attachments/assets/81ecbdba-77c2-400a-b1ff-c7cc765d81bc" />


<img width="757" height="557" alt="image" src="https://github.com/user-attachments/assets/2f4c301e-5037-4f65-a603-b91091d14b08" />


<img width="757" height="562" alt="image" src="https://github.com/user-attachments/assets/2d4556b1-a010-4ed2-b8ff-8ee6264dc76e" />


<img width="767" height="522" alt="image" src="https://github.com/user-attachments/assets/d9d7c733-7971-4a3a-b472-c81eb2966c44" />


<img width="762" height="512" alt="image" src="https://github.com/user-attachments/assets/31d325a0-da46-40d2-8107-c41aafdee122" />


<img width="912" height="590" alt="image" src="https://github.com/user-attachments/assets/5092e28b-b241-47ab-8fb0-096c1743a634" />


Then enter:
````
Administrators
````
<img width="451" height="255" alt="image" src="https://github.com/user-attachments/assets/ad434b1d-40dd-46c9-b7dc-d7a201a0e47b" />


<img width="912" height="591" alt="image" src="https://github.com/user-attachments/assets/f15061d7-daf8-49a4-a58c-3cf07e536559" />


Then click **Add** again:

<img width="766" height="521" alt="image" src="https://github.com/user-attachments/assets/1a961ae3-2850-437e-a1c5-671ee045570c" />


<img width="916" height="591" alt="image" src="https://github.com/user-attachments/assets/03a0bb96-e1bd-46cc-a33f-265b0580cddf" />


Then enter:
````
DL_HR_Modify
````
<img width="455" height="251" alt="image" src="https://github.com/user-attachments/assets/6193b2d6-538b-4d1f-8cda-5da61e5bd3c1" />


<img width="912" height="582" alt="image" src="https://github.com/user-attachments/assets/1dcdc0dc-29a6-4c99-b914-0985873a10d0" />


Then click **Apply** and click **Ok**.


<img width="756" height="560" alt="image" src="https://github.com/user-attachments/assets/5b67c827-eb0e-4359-9519-88f0096097d5" />


<img width="762" height="561" alt="image" src="https://github.com/user-attachments/assets/1a13f07f-88bf-4f01-843f-444625a26820" />


<img width="757" height="552" alt="image" src="https://github.com/user-attachments/assets/305dc830-6fa0-4f5b-96a3-d7ab67448f4e" />


Now we got new share folder:

<img width="1896" height="861" alt="image" src="https://github.com/user-attachments/assets/03147f51-7050-4325-a7c6-d2f53ae24cc6" />



Now we completed.

---


### Create share folder for IT Department

Click on **TASKS** -> **New Share...**

<img width="1900" height="747" alt="image" src="https://github.com/user-attachments/assets/3bf1ac93-f568-4f69-90cd-366d422aebc0" />


<img width="752" height="557" alt="image" src="https://github.com/user-attachments/assets/a252daa3-72d1-4c7f-9d28-32fb6571fba5" />



<img width="757" height="565" alt="image" src="https://github.com/user-attachments/assets/f103426b-df10-433f-bee2-2e3d5137e2e0" />



<img width="724" height="487" alt="image" src="https://github.com/user-attachments/assets/23c8f558-1f5e-455c-9489-b735e7aa37a6" />


<img width="756" height="552" alt="image" src="https://github.com/user-attachments/assets/aab7b234-4239-4235-a865-49ab86bd198d" />


<img width="761" height="561" alt="image" src="https://github.com/user-attachments/assets/6d50631b-f4a4-4663-b90e-e37a83ea2a82" />


<img width="757" height="552" alt="image" src="https://github.com/user-attachments/assets/0e8c6f6a-69fb-48f3-931e-193bcd3121c1" />


<img width="757" height="562" alt="image" src="https://github.com/user-attachments/assets/fd09f8e2-cdc0-42fe-934d-4cbb913ada77" />


<img width="762" height="515" alt="image" src="https://github.com/user-attachments/assets/0b15d0e9-fb3c-4f08-8c63-57616745a40f" />


<img width="767" height="520" alt="image" src="https://github.com/user-attachments/assets/4f25e09a-19cc-4e82-8696-b106b3bf4971" />


<img width="907" height="587" alt="image" src="https://github.com/user-attachments/assets/49012876-6e61-432d-a9b5-42a962348145" />


Then enter:
````
Administrators
````
<img width="452" height="252" alt="image" src="https://github.com/user-attachments/assets/81341e48-9eea-4044-b47d-d610e6cc3365" />


<img width="911" height="592" alt="image" src="https://github.com/user-attachments/assets/a7eb8a83-fa44-42fb-9d16-d3bbaa38706c" />


<img width="762" height="516" alt="image" src="https://github.com/user-attachments/assets/3036d52e-03d6-4c1c-9256-0aac84bd2ead" />


<img width="915" height="590" alt="image" src="https://github.com/user-attachments/assets/6f49c838-8aee-4d75-b05b-8a83c8f4b439" />


Then enter:
````
DL_IT_Modify
````

<img width="461" height="247" alt="image" src="https://github.com/user-attachments/assets/fee21be9-1de8-4290-a5aa-bca1073a8639" />


<img width="912" height="592" alt="image" src="https://github.com/user-attachments/assets/bcca1283-9e18-44a0-935a-276e1c234211" />


<img width="770" height="522" alt="image" src="https://github.com/user-attachments/assets/a7879f1c-98ae-41b9-8726-c22e37c69b10" />


<img width="757" height="557" alt="image" src="https://github.com/user-attachments/assets/c4c39e14-530b-4bf1-b59a-6041352bd77c" />


<img width="760" height="557" alt="image" src="https://github.com/user-attachments/assets/78c810f8-052c-4b8f-8376-198917d3c5af" />


<img width="757" height="561" alt="image" src="https://github.com/user-attachments/assets/3da4f38e-02d5-41ab-a20b-a91140adfd87" />


Now we got new share folder for **IT**:
<img width="1917" height="872" alt="image" src="https://github.com/user-attachments/assets/20093e99-1489-48ea-829e-76a5474988b4" />


Now we completed.

---



### Create share folder for General


<img width="1906" height="731" alt="image" src="https://github.com/user-attachments/assets/a4d5854c-3e02-4a4e-8f2c-04245ef5a0cf" />


<img width="757" height="551" alt="image" src="https://github.com/user-attachments/assets/dfcf7399-b4d6-4e34-b133-7bc306c90728" />


<img width="747" height="552" alt="image" src="https://github.com/user-attachments/assets/28c41526-a910-4ad7-bbaf-049e0ab15bb6" />


<img width="720" height="490" alt="image" src="https://github.com/user-attachments/assets/29c7cb51-6216-4cbd-b03c-4c7ee22e57d4" />


<img width="755" height="562" alt="image" src="https://github.com/user-attachments/assets/d6b6c5ee-7019-4fdd-81c2-062a3e8ad32f" />


<img width="760" height="557" alt="image" src="https://github.com/user-attachments/assets/f3d30c50-9cb8-4962-96e1-6fcf0b9d1896" />


<img width="765" height="562" alt="image" src="https://github.com/user-attachments/assets/1582cc04-af48-438a-a0cf-a927b5a79222" />


<img width="757" height="561" alt="image" src="https://github.com/user-attachments/assets/5c298f1c-431c-4e7e-afb9-23f21cf57559" />


<img width="762" height="517" alt="image" src="https://github.com/user-attachments/assets/f98a12bd-9e6e-4521-a389-dfd7e91e5697" />


<img width="952" height="642" alt="image" src="https://github.com/user-attachments/assets/af9feb4a-8ce0-4a79-881c-77f72df2bdd0" />


<img width="1140" height="731" alt="image" src="https://github.com/user-attachments/assets/bc4501f5-2c74-496a-ada0-d2713d42eb2d" />



Then enter:
````
Administrators
````
<img width="567" height="317" alt="image" src="https://github.com/user-attachments/assets/8c2ee58b-7fd9-46da-80fd-c73fcab3113c" />



<img width="1142" height="740" alt="image" src="https://github.com/user-attachments/assets/6c97055a-7154-4cdc-9131-64cb945f6322" />



Then click **Add** again:

<img width="951" height="646" alt="image" src="https://github.com/user-attachments/assets/ab297e82-571a-4109-8598-d28c3eada661" />


<img width="1145" height="740" alt="image" src="https://github.com/user-attachments/assets/1eda6095-b767-468f-8fe5-2787474a9bb6" />


Then enter:
````
DL_General_Modify
````

<img width="575" height="312" alt="image" src="https://github.com/user-attachments/assets/2193424b-4f87-4cbc-96b0-4d8d18a34d60" />


<img width="1145" height="737" alt="image" src="https://github.com/user-attachments/assets/86a7bf21-1bf2-4e37-9a67-4484725afd9e" />


<img width="957" height="647" alt="image" src="https://github.com/user-attachments/assets/84b2c4b3-92ad-4cb5-84b2-2ace911359b1" />


<img width="951" height="702" alt="image" src="https://github.com/user-attachments/assets/22f3083a-5b57-41a0-9945-c5c5502d3700" />


<img width="950" height="692" alt="image" src="https://github.com/user-attachments/assets/60313bf4-af76-4397-ac60-e13d3e648e9e" />


<img width="937" height="690" alt="image" src="https://github.com/user-attachments/assets/1a279f62-1feb-4015-85f1-101eb22be685" />


Now we got new folder share for general:

<img width="1917" height="877" alt="image" src="https://github.com/user-attachments/assets/77653b76-16d6-46c8-acab-36b43b8fb016" />



---


### Create share folder for Management

<img width="1905" height="867" alt="image" src="https://github.com/user-attachments/assets/cba59fc7-21b7-4a2d-844e-c7074628e286" />


<img width="942" height="695" alt="image" src="https://github.com/user-attachments/assets/43367bb4-d4e5-49a9-92bf-7ffb8684de42" />


<img width="947" height="696" alt="image" src="https://github.com/user-attachments/assets/d586216c-f65d-4132-aa9d-d4e89f43a198" />


<img width="902" height="605" alt="image" src="https://github.com/user-attachments/assets/7e0a269f-ca33-4ba2-a716-b738ae60f8d2" />



<img width="950" height="695" alt="image" src="https://github.com/user-attachments/assets/302ee798-a377-4095-b318-a7b9a0632acc" />


<img width="945" height="692" alt="image" src="https://github.com/user-attachments/assets/bd4a3583-11a0-4834-9cca-05b765f4d4df" />


<img width="940" height="700" alt="image" src="https://github.com/user-attachments/assets/0f2bac74-3e07-4e9f-a4db-0225f695183a" />


<img width="942" height="696" alt="image" src="https://github.com/user-attachments/assets/926088cc-8a85-4e16-8bf5-770c541c8dde" />


<img width="962" height="642" alt="image" src="https://github.com/user-attachments/assets/91a4de26-5b95-45c2-bf1e-894d4db6f702" />


<img width="957" height="647" alt="image" src="https://github.com/user-attachments/assets/f1a2155a-9a95-4629-8394-478ba4804ba3" />


<img width="1147" height="732" alt="image" src="https://github.com/user-attachments/assets/7b637a07-e39d-4b78-b0d7-72225046ca3e" />


Then enter:
````
Administrators
````
<img width="571" height="311" alt="image" src="https://github.com/user-attachments/assets/18ad97c7-88ed-4d35-8c66-a345342baeb6" />


<img width="1142" height="737" alt="image" src="https://github.com/user-attachments/assets/9f2f6c09-e90d-4ca6-b61e-968b366dc02b" />


<img width="962" height="642" alt="image" src="https://github.com/user-attachments/assets/3c9bb1ca-b2cb-48f4-9248-01d127f1a164" />


<img width="1147" height="737" alt="image" src="https://github.com/user-attachments/assets/c959d4d8-1554-4bca-828e-de5b46f93d3b" />


<img width="572" height="311" alt="image" src="https://github.com/user-attachments/assets/bca2e052-c6e0-4838-bd91-56b039692230" />


<img width="1142" height="737" alt="image" src="https://github.com/user-attachments/assets/1fb0a5f9-b4de-40eb-89c8-c87676dee906" />


<img width="947" height="647" alt="image" src="https://github.com/user-attachments/assets/5855e163-84be-47af-bba5-1664f67e5364" />



<img width="947" height="692" alt="image" src="https://github.com/user-attachments/assets/caa50d01-8f7d-4157-a490-6c68a05d11ac" />


<img width="932" height="687" alt="image" src="https://github.com/user-attachments/assets/517818d7-73e6-4fd3-b252-31a57adb2d02" />


<img width="947" height="695" alt="image" src="https://github.com/user-attachments/assets/d08d4612-3674-448e-8829-7f39ad8fb785" />


<img width="1912" height="865" alt="image" src="https://github.com/user-attachments/assets/10e88d96-bff4-41a8-aef1-c4c220abd5ec" />


Now we completed all share folder.

---


## 8. Verrify share folder:

In this we can verify by command and manual.


After creating the HR share, open **PowerShell** as **Administrator** on ``DC01`` and run:

````ps1
PS C:\WINDOWS\system32> Get-SmbShareAccess -Name "hr"

Name ScopeName AccountName            AccessControlType AccessRight
---- --------- -----------            ----------------- -----------
hr   *         BUILTIN\Administrators Allow             Full
hr   *         NETLAB\DL_HR_Modify    Allow             Change

PS C:\WINDOWS\system32> Get-SmbShareAccess -Name "IT"

Name ScopeName AccountName            AccessControlType AccessRight
---- --------- -----------            ----------------- -----------
it   *         BUILTIN\Administrators Allow             Full
it   *         NETLAB\DL_IT_Modify    Allow             Change


PS C:\WINDOWS\system32> Get-SmbShareAccess -Name "General"

Name    ScopeName AccountName              AccessControlType AccessRight
----    --------- -----------              ----------------- -----------
general *         BUILTIN\Administrators   Allow             Full
general *         NETLAB\DL_General_Modify Allow             Change


PS C:\WINDOWS\system32> Get-SmbShareAccess -Name "Management"

Name       ScopeName AccountName                 AccessControlType AccessRight
----       --------- -----------                 ----------------- -----------
Management *         BUILTIN\Administrators      Allow             Full
Management *         NETLAB\DL_Management_Modify Allow             Change
````



---


Verify in **File Explorer**:

Now we see our folder share:
````
\\DC01\general
````
<img width="452" height="595" alt="image" src="https://github.com/user-attachments/assets/75fcbe90-8e52-4aa9-8e94-42f84f510a8e" />


----


## 9. Test share folder:

### Test with user c.ronaldo

In this after I login in into user ``c.ronald``, then open **File Explorer**:

Then enter this:
````
\\dc01
````

<img width="1917" height="626" alt="image" src="https://github.com/user-attachments/assets/1bb3e264-b5a8-43e3-ab6d-ad600102e121" />


Now we see our share folder.


In this I test to open in each folder and what happen?

#### Test open general:

Open **General** folder, just `Double-Click` on **`general**:

<img width="1392" height="607" alt="image" src="https://github.com/user-attachments/assets/df64bc14-d3ef-4273-977f-42369a2a94c1" />


Now in this we can open this folder.

Then I test to create file:

Just `Right-Click` on empty area then click **New** -> **Folder**:

<img width="950" height="610" alt="image" src="https://github.com/user-attachments/assets/b1f00e91-1cb4-44a3-ae65-5f53b4932f3c" />



#### Test open hr:

just `Double-Click` on **hr**:

<img width="1687" height="647" alt="image" src="https://github.com/user-attachments/assets/6c6392f0-fd62-4c31-ac77-87b9e43094d3" />


So in this we don't have permission to access this folder.


#### Test open IT folder

Open It folder:
<img width="1696" height="706" alt="image" src="https://github.com/user-attachments/assets/cdc3eaf6-1af7-4dac-a288-a3e1d8a2c7bf" />


Now in this I can access to IT folder.


#### Test open Management folder

<img width="1917" height="731" alt="image" src="https://github.com/user-attachments/assets/65cfb74a-6ae5-4fda-8bec-ddfbcc395fe4" />


So in this I don't have permission to open this folder.


----



### Test with manager role v.marcelo

First login into user marcelo, then open **File Explorer**:

then search for:
````
//dc01
````

Then we can test all in each folder.

<img width="1917" height="718" alt="image" src="https://github.com/user-attachments/assets/eb769423-b999-44a8-9a99-7bb07816cf91" />



In this the user ``v.marcelo`` can access to only `general`, `it` and ``Management`` of this four folder.


-----



Now we completed filr server.

----
