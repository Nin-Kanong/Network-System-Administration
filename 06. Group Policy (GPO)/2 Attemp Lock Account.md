<h1 align="center"> 2 Ateemp Lock Account </h1>



---


## On Windows Server 


First in this open **Active Directory Administrative Centre**:


<img width="1912" height="866" alt="image" src="https://github.com/user-attachments/assets/b8a4b868-8566-4e0d-bace-60d78f426035" />



Then navigate to:
````
Active Directory Administrative Center
└── netlab (local)
    └── System
        └── Password Settings Container
````

<img width="1918" height="875" alt="image" src="https://github.com/user-attachments/assets/5a0c06e2-3050-4d00-9513-128950df5d4c" />




Now it will show this:

<img width="1910" height="877" alt="image" src="https://github.com/user-attachments/assets/06980f55-bee9-4d1c-a90e-139ba2027fe1" />



On the righ-hand panel, click on **New** -> **Password Settings**:

<img width="1917" height="771" alt="image" src="https://github.com/user-attachments/assets/b54ed0a1-0e1d-4d10-b931-af627500324a" />



Now it will show this:

<img width="1912" height="881" alt="image" src="https://github.com/user-attachments/assets/c67129c7-405c-45e5-8407-7c67530dbc5e" />


---



### Configure Password Settings Policy


#### Policy Identification

| Field | Enter |
| :--- | :--- |
| **Name** | ``PSO_2Attempts`` |
| **Precedence** | ``10`` |
| **Description** (Optiona) | ``Account lockout after 2 wrong passwords`` |



**Then eanble 2 attemp:**

| Setting | Enter or select |
| :--- | :--- |
| **Number of failed logon attempts allowed** | 2 |
| **Reset failed logon attempts count after (mins)** | 30 |
| **Account will be locked out** | Until an administrator manually unlocks the account |


<img width="1917" height="872" alt="image" src="https://github.com/user-attachments/assets/1470ac3c-9643-4dc7-9901-b124e6cabce6" />


After config all just click **Add...**.



### Add existing GG_HR group

In this jjust click on **Add...**, then enter name:

````
GG_HR
````



<img width="600" height="306" alt="image" src="https://github.com/user-attachments/assets/5f5f052d-02a3-4af3-9e24-4ce22030f8af" />



<img width="1917" height="871" alt="image" src="https://github.com/user-attachments/assets/f53265a1-e6a5-4587-bd1e-070a988013f4" />


Now we was completed.


After we complete all jiust click **Ok**:

<img width="1907" height="867" alt="image" src="https://github.com/user-attachments/assets/1e6bd772-db9d-422e-89c3-b067330f37ee" />



----



### Verify it applies top our HR Account

Click on **netlab (Local)**:


<img width="1919" height="875" alt="image" src="https://github.com/user-attachments/assets/c21ed129-4572-49de-ae7b-e4368c4593ae" />



After completed all just click on **View Resultant Password Settings**:

<img width="1910" height="872" alt="image" src="https://github.com/user-attachments/assets/8394969c-b37c-4907-b543-075bf9cfc3e7" />



Now we see like we was config:

<img width="1916" height="875" alt="image" src="https://github.com/user-attachments/assets/730ebcb9-f24c-4331-9ea2-831926016244" />


Now we completed.


-----



## On Windows 11 (CLIENT)

### Test With User in HR group:

In this I will test with my user in HR group.

So in this in my HR Department I have 3 user:
````
HR
  ├── Pe Pe (HR Department User)
  ├── Raphael Varane
  └── Sergio Ramos
````


So in this I test with my user `pe.pe`.


### Test with user Pe Pe

First in this login into user `pe.pe`.


**In this I test login first time:**

<img width="1917" height="925" alt="image" src="https://github.com/user-attachments/assets/2e9923c7-7dfb-402f-9b14-93d859c2e7c6" />


<img width="1152" height="607" alt="image" src="https://github.com/user-attachments/assets/b1d61913-618a-410b-8e90-d566d858d691" />



**Seconds:**

<img width="1912" height="897" alt="image" src="https://github.com/user-attachments/assets/5a44e3fe-b6f9-41d2-876c-e4db7835b638" />


<img width="1671" height="805" alt="image" src="https://github.com/user-attachments/assets/14219d7c-6463-4b3d-bda6-0e8192c41979" />




**Third:**

<img width="1912" height="911" alt="image" src="https://github.com/user-attachments/assets/3253f200-b8e8-4dd7-8577-1cae3ff8ca63" />



<img width="1377" height="716" alt="image" src="https://github.com/user-attachments/assets/85e7dc1d-8bfe-40ff-a9c4-380839a2abdd" />




Now got successful.


-------




## Unlock Account

In this we got successful to lock account after 2 attempts.


Then we need to unlock like when they contact us to unlock thier account.


Om **Windows Server** -> Open **Server Manager**:

<img width="1917" height="870" alt="image" src="https://github.com/user-attachments/assets/bbcffd34-a9e6-4ddf-909c-1fce1b659c1b" />



Then find our **HR user** that locked.

In this go to the user that locked, just `Right-Click` on user `Pe Pe`:

<img width="1457" height="723" alt="image" src="https://github.com/user-attachments/assets/a26dada1-c54b-4dab-92e7-553e9593d905" />



In this on **Account** tab, and we will see **Unlock account. This account is currently locked out on this Active Directory Domain Controller**:

<img width="507" height="667" alt="image" src="https://github.com/user-attachments/assets/911c219b-5e36-48ac-a12d-a48e62f9d034" />


Check the **Unlock account checkbox**, then click **Apply** and click **Ok**:

<img width="505" height="662" alt="image" src="https://github.com/user-attachments/assets/3f3e62ed-6714-4060-9c7d-5d6c90bb837e" />


<img width="1531" height="687" alt="image" src="https://github.com/user-attachments/assets/e85169ee-1f0e-4c32-b13e-324a785b8bd2" />


Now we completed to unlocked on user `Pe Pe`.


---




### Test login again to user Pe Pe

In this after adminwas unlocked, then we need to login again.

In this we need to login with the correct password about this 2 attemp:

<img width="1917" height="922" alt="image" src="https://github.com/user-attachments/assets/80801350-e310-408a-885b-be495ff5a4c1" />


<img width="1707" height="772" alt="image" src="https://github.com/user-attachments/assets/267b4061-7590-46fd-a96b-185a1c9a4696" />


<img width="1917" height="937" alt="image" src="https://github.com/user-attachments/assets/b4085ab5-f556-413e-b232-b36b0ec50eb2" />



Now we was successful.


--------------------------
