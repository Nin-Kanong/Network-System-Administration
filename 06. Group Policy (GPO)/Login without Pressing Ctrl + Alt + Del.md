<h1 align="center"> Login without Pressing Ctrl + Alt + Del </h1>


---




## Configure using Active Directory Group Policy


### Create the IT Group Policy

On **Windows Server**, then open **Server Manager**:

<img width="1915" height="862" alt="image" src="https://github.com/user-attachments/assets/e9df0ddd-9df6-4ee0-adab-60c18c5a9e21" />


In this navigate to group **IT**, then `Right-Click` on **IT** , then select `Create a GPO in this domain, and Link it here...`:


<img width="1911" height="847" alt="image" src="https://github.com/user-attachments/assets/28f3f139-89a3-461f-b9a3-bde28deb293a" />



Then enter name:
````
GPO_IT_Disable_CtrlAltDel
````

<img width="477" height="226" alt="image" src="https://github.com/user-attachments/assets/1abeecc3-9661-4d5b-8f71-4fc54294745a" />



<img width="1916" height="701" alt="image" src="https://github.com/user-attachments/assets/5c6f2900-6246-4cea-9445-f3df54b4d4fa" />


---


### Edit the IT group Policy:

``Right-click`` on ``GPO_IT_Disable_CtrlAltDel``, then select **Edit**:


<img width="1917" height="747" alt="image" src="https://github.com/user-attachments/assets/6ae58a75-faad-4da8-95c0-96add62388ac" />




Then navigate to:

````
Computer Configuration
  └── Policies
      └── Windows Settings
          └── Security Settings
              └── Local Policies
                  └── Security Options
````


Then we will see **Interactive logon: Do not require CTRL+ALT+DEL**:

<img width="1346" height="852" alt="image" src="https://github.com/user-attachments/assets/70b93b82-4852-4119-bca4-aca347c7e7a4" />


Then `Double-Click` on **Interactive logon: Do not require CTRL+ALT+DEL**:


<img width="520" height="627" alt="image" src="https://github.com/user-attachments/assets/c06f45a4-adc7-4e22-905b-d3ef27cf0d70" />



<img width="515" height="622" alt="image" src="https://github.com/user-attachments/assets/fdd06165-d1dc-4829-bedc-ee98025cbf9d" />


<img width="1208" height="846" alt="image" src="https://github.com/user-attachments/assets/ce0d3f0a-bb77-4a62-8892-dcbd3bfd3594" />


Now we was **Enabled**.



Then apply GPO:
````cmd
gpupdate /force
````

<img width="640" height="225" alt="image" src="https://github.com/user-attachments/assets/7445c41d-cb44-4327-978d-4ae76bc802a8" />





----




### Test Wuith user IT


#### Test with user C.Ronaldo


In this on my IT department have:
````
IT
├── Cristiano Ronaldo (User)
├── Gareth Bale (User)
├── Vieira Marcelo (User)
````


Then in this I login to my user ``c.ronaldo``:

| Field | Value |
| :--- | :--- |
| **Username** | ``c.ronaldo@netlab.com`` |
| **Password** | ``@R0n41d0`` |

<img width="1912" height="927" alt="image" src="https://github.com/user-attachments/assets/a01b91f2-34e2-4ed1-83fe-8964aedb3737" />




In this I **Power Off** my machine first then **Power On** it again:



<img width="1910" height="982" alt="image" src="https://github.com/user-attachments/assets/7746fc85-25da-4b41-a26c-95592e1d6637" />




After I start it again in this now it don't need me to epressing `Ctrl + Alt + Del` again:


<img width="1917" height="965" alt="image" src="https://github.com/user-attachments/assets/fd781561-961f-4810-bc53-92e3e3d70a04" />



So in this it can open with need to press `Ctrl + Alt + Del`.


In this Just ``double-click`` on it it will show to login again:


<img width="1917" height="957" alt="image" src="https://github.com/user-attachments/assets/0a9b863f-2994-4c8f-ab7c-f837dbffbdbc" />


Now wwe got successful.

---


### Test with HR department that not enable GPO


In this I want to test with **HR Department** that we are not yet to enable it.


Just `Signout` from user IT then login with user on HR team:


<img width="1917" height="947" alt="image" src="https://github.com/user-attachments/assets/8b9876b6-474c-4d7b-8001-3a78dcbc0ba3" />



Then power off and power on it again:








































































