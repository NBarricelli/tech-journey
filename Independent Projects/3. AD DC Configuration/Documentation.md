# **AD DC Configuration**

## **Introduction**
Now that I have my DC created, a test account created, and a PC joined to the domain, I can start configuring group policies and add a print server.

## **Group Policies**
I first create three Organizational Units to keep everything separated and clean: Lab Users, Lab Computers, and Lab SVC Accounts. Within the Lab Users OU are two more OUs: Standard User and Limited User. As we can see, there are not very many Group Policy Objects in this domain yet.

<img width="165" height="300" alt="Screenshot of Active Directory Users and Computers" src="https://github.com/user-attachments/assets/31f5ef0c-641c-4257-903f-2fb9de94ef18" />
<img width="580" height="300" alt="Screenshot of Group Policy Management" src="https://github.com/user-attachments/assets/3c58b309-8cf5-4e9e-8817-f05fb67b02ba" />

I made two policies to start: C_SEC_SCREENTIMEOUT and C_SEC_LOGONMESSAGE. The naming scheme reads as C (Computer Policy), SEC (Security Policy), and a description of the policy. I linked these GPOs to the Lab COmputers OU and after restarting vm-WIN11, it immediately worked.

<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/01057baf-d95c-4db6-a35b-93e51f4de22c" />
<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/54dd210e-5643-49e0-b521-b5c2df79e2fb" />
<img width="548" height="302" alt="image" src="https://github.com/user-attachments/assets/c11a9c42-d026-449f-938e-d89cd29265af" />
