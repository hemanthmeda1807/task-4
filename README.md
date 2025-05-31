# Cyber Security Internship Task 4
# UFW Firewall Setup  

## 🎯 Objective
Configure and test basic firewall rules using UFW (Uncomplicated Firewall) on Linux or Windows Firewall to allow/block network traffic.

---

## 🧰 Tools Required
- Ubuntu (Target Machine)
- Kali Linux (Attacker/Tester Machine)
- UFW Firewall
- vsftpd FTP server
- nmap (network scanner)

---

## 🛠️ Setup Instructions

### 📍 On Ubuntu (Target Machine)
1. **Install FTP server**
   ```bash
   sudo apt install vsftpd
   ```

2. **Edit FTP Configuration**
   ```bash
   sudo nano /etc/vsftpd.conf
   ```
   - Set:
     ```
     local_enable=YES
     write_enable=YES
     ```

3. **Start FTP Service**
   ```bash
   sudo systemctl start vsftpd
   ```

---

### 📍 On Kali (Tester Machine)
1. **Scan Port 21 on Ubuntu**
   ```bash
   nmap -sV -p 21 <Ubuntu-IP>
   ```
![image](https://github.com/user-attachments/assets/cac822cb-6895-4540-bf0f-b243b9199e88)

2. **Try Remote FTP Login**
   ```bash
   ftp <Ubuntu-IP>
   ```
   ![image](https://github.com/user-attachments/assets/09fb6e7d-2e45-4dbe-b43a-a5f1a075823c)

---

## 🔥 Working with UFW Firewall

### 1. Enable and Start Firewall
```bash
sudo systemctl start ufw
```
or
```bash
sudo ufw enable
```
![image](https://github.com/user-attachments/assets/f3ff8314-1f5c-4a03-a591-506703abf105)

### 2. Disable Firewall
```bash
sudo systemctl stop ufw
```
or
```bash
sudo ufw disable
```
![image](https://github.com/user-attachments/assets/4bfd6c96-77b1-40f7-9f68-e6f009a3d963)
### 3. List current firewall rules.
```bash
ufw status
```
![image](https://github.com/user-attachments/assets/44322705-caac-41fd-a619-e699cde12d70)

### 4. Set Default Policies
- Block all incoming:
  ```bash
  sudo ufw default deny incoming
  ```
  ![image](https://github.com/user-attachments/assets/c8684a19-766b-42b1-8835-c03895392662)

- Allow all outgoing:
  ```bash
  sudo ufw default allow outgoing
  ```
  ![image](https://github.com/user-attachments/assets/4dd38323-3ddf-47d4-8c97-02486a706bbe)

### 5. Add rule to allow SSH (port 22)
```bash
ufw allow 22
```
![Screenshot From 2025-05-31 17-21-07](https://github.com/user-attachments/assets/29264066-813a-48a6-aa65-bbdea1c73bba)

### 6. Remove the test block rule to restore original state.
```bash
ufw reset
```
![image](https://github.com/user-attachments/assets/836c28b5-fac9-4d87-ab18-0eb0dfa93caa)

### 7. Allow/Deny Specific Ports
```bash
sudo ufw deny 21
```
![image](https://github.com/user-attachments/assets/158048ec-2c6b-470e-9a7c-ebacd2eebb88)
![image](https://github.com/user-attachments/assets/0b65a858-0268-4537-a6d2-14f7cf04de2e)

```bash
sudo ufw allow 21
```
![image](https://github.com/user-attachments/assets/a7ac088f-0e4e-4434-9282-8bdef32ca881)
![image](https://github.com/user-attachments/assets/47efd738-6b92-487e-865d-acc140c5cdf5)

### 8. Allow From Specific IP
```bash
sudo ufw allow from <ip-address> to any port 21
```
![image](https://github.com/user-attachments/assets/e2442257-6537-4f21-a4d7-51f5e932cfd9)
![image](https://github.com/user-attachments/assets/ef0a61fa-9ee9-48d9-8a2b-12ef9a44f55c)

### 9. View Firewall Status
```bash
sudo ufw status
```
![image](https://github.com/user-attachments/assets/16d04cc1-48b8-4161-9384-757fc90c19c6)
```bash
sudo ufw status numbered
```
![image](https://github.com/user-attachments/assets/4dc5909c-4dd3-41d9-b9c6-f5cff1b65dea)

### 10. Delete a Specific Rule
```bash
sudo ufw delete <rule-number>
```
![image](https://github.com/user-attachments/assets/533351e1-9a59-48bd-a725-35bbfe5a0f37)

### 11. Reset Firewall Rules
```bash
sudo ufw reset
```
![image](https://github.com/user-attachments/assets/715bb747-6100-452f-a2c3-3bb4ba5d5355)

### 12. Summarize how firewall filters traffic
- Firewalls monitor and control network traffic using rules.
- They can permit or block traffic based on IP, port, and protocol.

---

