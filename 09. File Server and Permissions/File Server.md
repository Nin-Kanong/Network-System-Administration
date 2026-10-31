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


### Add employees to the Global Security Groups

In this after we ready created groups, then assign it to our departments.


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


#### Verify GG_All_Staff

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


### Configure NTFS folder permissions

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


#### Configure the HR folder

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



#### Configure the ICT folder





















