# Network-Analysis
**Capturing login credentials using Wireshark**


Launch Metasploitable and log in using the credentials you created. For example, mine are _msfadmin_ for both the username and password.

Use the command ifconfig to determine the IP address of the Metasploitable virtual machine. Mine is _192.168.1.170_
<img width="721" height="402" alt="ifconfig" src="https://github.com/user-attachments/assets/05f94b88-d511-4bed-bcb7-6ffb1cc063b8" />

Open a web browser and enter the IP address in the URL bar to access the Metasploitable web interface.
<img width="795" height="590" alt="dvwa page " src="https://github.com/user-attachments/assets/2ee675f2-daff-4adb-9f0f-4913539a6b2d" />

Click on the DVWA link to open the login page for the Damn Vulnerable Web Application.
<img width="795" height="589" alt="Screenshot 2025-07-22 094646" src="https://github.com/user-attachments/assets/1cd8a5b5-29a7-4a17-b7ba-c250dc8a6c8b" />

**Note: This project is intended to illustrate the risks of using insecure websites. In this scenario, credentials are transmitted in plain text, unlike the encrypted transmission provided by the HTTPS protocol (TLS).**

Open Wireshark and begin capturing network traffic. Select the network interface you are using and start capturing.
<img width="1055" height="651" alt="Screenshot 2025-07-22 094802" src="https://github.com/user-attachments/assets/f3d4750c-6d42-401a-915e-c4e16c160182" />

Return to the DVWA login page and attempt to log in using any credentials. It doesn’t need to be valid. For example, use _kali_ as the username and _giveaccess_ as the password.
<img width="696" height="411" alt="Screenshot 2025-07-22 095106" src="https://github.com/user-attachments/assets/f6dc25f5-caa2-4a65-8faa-520cfda4b509" />

The login will fail, but our goal is to observe what happens in the background.

Stop the packet capture in Wireshark and apply a filter using the command: _ip.addr == <Metasploitable_IP>.
_<img width="1865" height="483" alt="APPLY FILTER" src="https://github.com/user-attachments/assets/6e03dfeb-8376-4708-99f1-f4f5a185fa30" />

Look specifically for HTTP POST requests. Set the filter to view HTTP traffic.
<img width="1860" height="452" alt="HTTP POST" src="https://github.com/user-attachments/assets/8f78c7ae-f91d-4c93-b1ce-1eddb5e24d84" />

Locate the HTTP POST request related to the login attempt, and inspect the packet to view the credentials transmitted in clear text.
<img width="1561" height="443" alt="CAPTURED CREDE" src="https://github.com/user-attachments/assets/3788619a-e7da-469e-9928-6e5d61396e4c" />
