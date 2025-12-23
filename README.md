# mini-soc-ssh-log-analysis
Mini SOC Lab - SSH Brute Force Detection using journalctl

## Objective
Detect and analyze SSH brute-force login attempts using systemd journal logs on Linux.

## Tools Used
- Kali Linux
- SSH
- journalctl
- UFW (for mitigation demo)

## Project Description
In this project, I simulated SSH failed login attempts and analyzed authentication logs using `journalctl`. 
Since modern Linux systems use systemd, traditional log files like auth.log were not available.

## Steps Performed

### 1. Navigate to log directory
```bash
cd /var/log
ls
2. Analyze SSH logs

sudo journalctl | grep ssh
sudo journalctl | grep "authentication failure"
3. Count failed login attempts

sudo journalctl | grep "Failed" | wc -l
4. Identify failed SSH attempts

sudo journalctl | grep "Failed password"
5. Attack simulation

ssh wronguser@<target_ip>
6. Extract attacker IP

sudo journalctl | grep "Failed password" | awk '{print $11}'
7. Mitigation (Optional)

sudo ufw enable
sudo ufw deny from <attacker_ip>
sudo ufw disable

Outcome:
Detected SSH brute-force attempts
Identified attacker IP address
Understood systemd-based log analysis
Learned basic mitigation awareness

Key Learning:
Modern Linux systems use journalctl instead of traditional log files
SOC detection focuses on monitoring and analysis
Mitigation can be automated or handled at later stages

Author:
Sumithra Ezhilmaran
