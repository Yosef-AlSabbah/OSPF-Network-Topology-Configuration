# OSPF Configuration Assignment

**Student Name:** Yousef Mohammed Yousef Al-Sabbah  
**Student ID:** 120212265  
**Instructor Name:** Malak Ghabayen  

This repository contains the configurations and verification outputs for enabling OSPF routing across a pre-configured network topology. Screenshots of the OSPF commands and their outputs are included in the repository. Additionally, you can find the `.pkt` file for the network topology [here](#).

---

## Assignment Overview

The goal of this assignment is to configure OSPF routing for full network connectivity using a given topology with pre-configured IP addressing and interfaces. Below is the step-by-step explanation of how each router was configured.

---

## Router Configurations

### Common Steps

Some steps are repeated across multiple routers. They are explained here once for simplicity:

- **Enable Privileged EXEC Mode:**
  Activates privileged EXEC mode.
  ```plaintext
  Router>enable
  ```
  

- **Enter Global Configuration Mode:**
  Allows access to global configuration mode.
  ```plaintext
  Router#configure terminal
  ```

- **Start OSPF Process:**
  Starts OSPF process 1.
  ```plaintext
  Router(config)#router ospf 1
  ```
  
- **Save Configuration:**
  Saves the current router configuration.
  ```plaintext
  Router#wr
  ```
  

### **Router R0: Configure Router ID Automatically (Highest Physical Interface IP)**

```plaintext
Router(config-router)#network 10.0.13.0 0.0.0.3 area 0
Router(config-router)#network 10.0.12.0 0.0.0.3 area 0
```
Includes the 10.0.12.0/30 and 10.0.13.0/30 networks in OSPF area 0.

---

### **Router R1: Manually Configure Router ID**

```plaintext
Router(config-router)#router-id 1.1.1.1
```
Manually sets the Router ID to 1.1.1.1.

```plaintext
Router(config-router)#network 10.0.12.0 0.0.0.3 area 0
Router(config-router)#network 10.0.24.0 0.0.0.3 area 0
```
Includes the 10.0.24.0/30 and 10.0.12.0/30 networks in OSPF area 0.

---

### **Router R2: Configure Router ID Automatically (Highest Loopback Interface IP)**

```plaintext
Router(config)#interface Loopback0
Router(config-if)#ip address 11.0.0.1 255.255.255.255
```
Creates a loopback interface and assigns the highest loopback IP address, 11.0.0.1/32.

```plaintext
Router(config-router)#network 11.0.0.1 0.0.0.0 area 0
Router(config-router)#network 10.0.13.0 0.0.0.3 area 0
Router(config-router)#network 10.0.34.0 0.0.0.3 area 0
```
Includes the 11.0.0.1/32, 10.0.34.0/30, and 10.0.13.0/30 networks in OSPF area 0.

---

### **Router R3: Configure OSPF Networks**

```plaintext
Router(config-router)#network 10.0.24.0 0.0.0.3 area 0
Router(config-router)#network 10.0.34.0 0.0.0.3 area 0
Router(config-router)#network 192.168.4.0 0.0.0.255 area 0
```
Includes the 10.0.24.0/30, 192.168.4.0/24, and 10.0.34.0/30 networks in OSPF area 0.

---

## Verification Commands

Run these commands on each router to verify the OSPF configuration:

- `show ip route`  
  Verify that OSPF routes are present in the routing table.

- `show ip ospf neighbor`  
  Confirm OSPF neighbor relationships are established.

---

## Repository Contents

- `.pkt` file for the network topology.
- Screenshots of OSPF configuration commands and their verification outputs.

---

Thank you for reviewing this assignment!
