# Simple test of Wazuh active response ability

## Objective

we are going to stage an attack on our Ubuntu device on a less that secure user account we will then created a rule with that Wazuh active response guide to disable a user account when a it detached a SSH connection  

### Skills Learned

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- advantage knowledge of bad actor attack vectors 
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Network analysis tools (such as Wireshark) for capturing and examining network traffic.
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps

Ref 1: To start this project off we are going to created a new user account on our Ubuntu machine. We are going to set this user up with simple password and name it Misty. 

[not-working](https://github.com/Th3miggy/Simple-test-of-Wazuh-active-response-ability/blob/main/creating%20new%20user%20misty.png?raw=true)

[not-working](https://github.com/Th3miggy/Simple-test-of-Wazuh-active-response-ability/blob/main/wazuh%20alert%20of%20new%20user.png?raw=true)

Ref 2: We are going into this lab assume that our attacker though a different means of attack as gain the knowledge of our new user password and now they are looking for a way into the system. so are attacker runs a nmap scan looking for open port and finds SSH on port 22 now he has a way in. Using the credential they already obtained we are able to make a remote connection.

[not-working](https://github.com/Th3miggy/Simple-test-of-Wazuh-active-response-ability/blob/main/nmap%20scan%20on%20port%2022.png?raw=true)

[not-working](https://github.com/Th3miggy/Simple-test-of-Wazuh-active-response-ability/blob/main/opening%20a%20SSH%20connection%20on%20attacker%20machine.png?raw=true)

Ref 3: Now let find a way to stop this form happening. The good news is we can already see that Wazuh saw the connection and a alert pop, but because it was done with the correct credential it doesn't really see it as an issue. 

[not-working](https://github.com/Th3miggy/Simple-test-of-Wazuh-active-response-ability/blob/main/wazuh%20alert%20of%20sucessful%20ssh%20connection%20to%20user%20misty.png?raw=true)

Ref 4: The news is we know that this user should never be connecting to her workstation remotely so we can sent specific rules in Wazuh ossec.conf file to disable the account when it detects a SSH connection.

[not-working](https://github.com/Th3miggy/Simple-test-of-Wazuh-active-response-ability/blob/main/command%20in%20ossec.conf%20file.png?raw=true)

Ref 5: After completing the updates to the ossec.conf file we wait for the next remote connection attempt and let Wazuh do the work. and in the following image we can see that it was successful when the attacker tried again to connect to the user Wazuh saw the connection and disable the again before anything worse could happened.

[not-working](https://github.com/Th3miggy/Simple-test-of-Wazuh-active-response-ability/blob/main/wazuh%20alerts%20of%20several%20failure%20after%20rule%20is%20immeint.png?raw=true)

[not-working](https://github.com/Th3miggy/Simple-test-of-Wazuh-active-response-ability/blob/main/attacker%20unable%20to%20connect%20to%20new%20user%20after%20rule%20implemented.png?raw=true)

##Concluison

With this simple lab we can see first hand how effective Wazuh active response can be and this is quiet literately the tip of the ice berg when it comes to the active response capabilities.

