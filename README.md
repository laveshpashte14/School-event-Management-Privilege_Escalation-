# School-Event-Management( Privilege_Escalation )
PoC for Privilege Escalation in School-Event-Management Software

Steps to Reproduce
1.) Login to the application as **Admin:Admin** and navigate to http://localhost/sems/user/index.php?view=edit&id=1

2.) Observe that the admin user has the access to change the role.
![image](https://github.com/laveshpashte14/School-event-Management-Privilege_Escalation-/assets/106723835/bda48808-b575-437b-a8c3-c3bc50988631)

3.) Also observe that the **User:Test** has role:SSG.
![image](https://github.com/laveshpashte14/School-event-Management-Privilege_Escalation-/assets/106723835/29974d47-a2f6-4c77-94c3-50fda9728c4b)

4.) Now logout and login with another user which is not an admin in our case **Test:Password@1234** (Low priv User) and naviagte to http://localhost/sems/user/index.php?view=edit&id=9.

5.) Enter the Password and click on save, intercept the update request in Burp Proxy.
![image](https://github.com/laveshpashte14/School-event-Management-Privilege_Escalation-/assets/106723835/ccf6b8bc-1c7a-4d4f-b626-2a69e3095e00)
![image](https://github.com/laveshpashte14/School-event-Management-Privilege_Escalation-/assets/106723835/8a2e442a-76f4-40a1-98f5-f906d3b29541)
6.) In the request body add the following parameter **U_ROLE=Administrator** and forward the request.
![image](https://github.com/laveshpashte14/School-event-Management-Privilege_Escalation-/assets/106723835/2f15871b-33a3-466c-8e13-9eed16847e3b)

7.) Refresh or logout and login again as **Test:Password@1234** observe that the **user:Test** is now an administrator.
![image](https://github.com/laveshpashte14/School-event-Management-Privilege_Escalation-/assets/106723835/49437604-fdc2-4191-860b-024cf41348b0)



