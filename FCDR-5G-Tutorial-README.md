
# FCDR-5G-Tutorial

## 🎯 Purpose

This tutorial aims to help participants set up a **basic 5G standalone network** using emulated components:
- **OAI Core**
- **OAI gNB**
- **OAI UE**

All components are containerized using **Docker**, and **Wireshark** is used to monitor network traffic.

By the end of the tutorial, participants will be able to:
- Launch a standalone 5G core network.
- Simulate gNB and UE behavior.
- Capture and analyze traffic using Wireshark.

---

## 🖥️ Minimum System Requirements

| Component         | Requirement           |
|------------------|------------------------|
| RAM              | 4 GB (8 GB recommended) |
| Disk Space       | 20 GB (free space)     |
| CPU              | x86_64, Virtualization enabled |
| OS               | Windows 10+, Ubuntu 22.04 |
| Hypervisor       | VMware Workstation 17 or VirtualBox |
| Internet         | Required for download and cloning repos |

---

## 🧰 Required Software

### ✅ **For Windows Users**

1. **Download VMware Workstation Player 17**  
   [Download Here](https://www.techspot.com/downloads/1969-vmware-player.html)

2. **Download the 5G Project Image (Preconfigured)**  
   [Download Image](https://drive.google.com/file/d/1XSxpMAzb3CWF2XE2kC_qO2JteYWWUlGR/view?usp=sharing)

3. **Steps:**
   - Unzip the downloaded `.zip` file.
   - Open VMware, click on open a virtual machine and attach the unzipped folder
   - Login details:
      - Username: fcdr_tutorial
      - Password: fcdr

---

### ✅ **For Linux Users**

1. **Clone the training repository**:
   ```bash
   git clone https://gitlab.eurecom.fr/oai/trainings/oai-workshops.git
   ```

2. **Install Wireshark**:
   ```bash
   sudo apt update
   sudo apt install wireshark -y
   ```

3. **Ensure Docker and Docker Compose are installed**:
   ```bash
   sudo apt install docker.io docker-compose -y
   ```

4. **Run the Docker-based 5G Network**:
   ```bash
   cd oai-workshops/cn/
   check container status:
   sudo docker compose -f docker-compose.yml ps -a
5. AMF logs
   ```bash
   sudo docker logs oai-amf -f
   
6. Run the gNB
   ```bash
    Sudo docker compose -f docker-compose-ran.yml up -d oai-gnb
AMF logs
    sudo docker logs oai-amf -f
gNB logs
    sudo docker logs oai-gnb -f
    
8.   Run the UE
    '''bash
      sudo docker compose -f docker-compose-ran.yml up -d oai-nr-ue
AMF logs
10. IP  address allocation check
     '''bash
        docker exec oai-nr-ue ifconfig
12. Traffic test
    '''bash
      docker exec -it oai-nr-ue bash
      ping -I oaitun_ue1 8.8.8.8 -c10
    

---

## 🔧 Key Components Overview

| Component | Description |
|----------|-------------|
| **OAI Core** | Implements the 5G Core Network functions (AMF, SMF, UPF, etc.) |
| **OAI gNB** | Emulates the 5G base station |
| **OAI UE**  | Simulates a 5G User Equipment (UE) |
| **Wireshark** | Captures and analyzes packet traffic |

---

## 🧪 What You'll Learn

- How to spin up a 5G network with emulated devices.
- Packet flows between UE, gNB, and Core.
- Basics of 5G architecture and its components.
- Using Wireshark to analyze signaling and data traffic.

---

## ⚠️ Troubleshooting

- **Docker command errors?**  
  Ensure Docker is installed and the user is in the `docker` group.

- **Wireshark can't capture?**  
  Run it with `sudo` or give capture permissions.

- **VM won’t boot?**  
  Ensure virtualization is enabled in BIOS/UEFI.

- **Not enough RAM?**  
  Close other applications or use a machine with at least 8GB RAM.

---

## 📌 Additional Notes

- The tutorial is best experienced with **VMware Workstation** due to compatibility and performance.
- Pre-workshop setup is **mandatory**. Make sure your environment is running before the session.
