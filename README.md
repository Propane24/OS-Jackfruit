# OS Jackfruit – Mini Container Runtime

## 1. Overview

This project implements a lightweight container runtime in C, inspired by Docker. It demonstrates core Operating System concepts such as process isolation, memory management, and inter-process communication using Linux system calls and kernel modules.

The system consists of:

* A user-space container engine (`engine.c`)
* A kernel-space memory monitor (`monitor.c`)

---

## 2. Features

### 2.1 Container Runtime

* Create and manage multiple containers
* Process isolation using:

  * Namespaces
  * `chroot()` filesystem isolation
* Supports independent root filesystems

---

### 2.2 CLI Interface

Commands implemented:

* `start` → Start a container
* `stop` → Stop a container
* `ps` → List running containers
* `logs` → View container logs

---

### 2.3 Logging System

* Captures container output
* Uses pipes and buffering
* Stores logs for each container

---

### 2.4 Memory Monitoring (Kernel Module)

* Tracks memory usage of containers
* Enforces:

  * Soft limit → Warning message
  * Hard limit → Terminates container

---

## 3. Tech Stack

* Language: C
* Platform: Linux (Ubuntu recommended)
* Concepts Used:

  * Process Management (`fork`, `clone`)
  * Namespaces
  * Signals
  * Kernel Modules
  * Inter-Process Communication (IPC)

---

## 4. Setup Instructions

### 4.1 Clone the repository

```bash
git clone https://github.com/<your-username>/OS-Jackfruit.git
cd OS-Jackfruit
```

### 4.2 Install dependencies

```bash
sudo apt update
sudo apt install build-essential linux-headers-$(uname -r)
```

### 4.3 Build the project

```bash
make
```

### 4.4 Load kernel module

```bash
sudo insmod monitor.ko
```

---

## 5. Usage

### 5.1 Start supervisor

```bash
sudo ./engine supervisor ./rootfs-base
```

### 5.2 Start a container

```bash
sudo ./engine start alpha ./rootfs-alpha /bin/sh
```

### 5.3 List containers

```bash
sudo ./engine ps
```

### 5.4 View logs

```bash
sudo ./engine logs alpha
```

### 5.5 Stop container

```bash
sudo ./engine stop alpha
```

---

## 6. Test Cases

### 6.1 Multiple Containers

* Started 2 containers simultaneously
* Result: Both executed independently

### 6.2 Soft Memory Limit

* Exceeded soft limit
* Result: Warning logged

### 6.3 Hard Memory Limit

* Exceeded hard limit
* Result: Container terminated

### 6.4 Logging

* Verified container output stored correctly

### 6.5 CLI Commands

* `ps`, `logs`, `stop` executed successfully

---

## 7. Demonstration

The project demonstration includes:

* Starting the supervisor
* Running multiple containers
* Viewing logs
* Demonstrating memory limit enforcement
* Stopping containers

---

## 8. Team Members

* Student 1: Pravith Mohandas
*      SRN: PES1UG24AM202
* Student 2: Vishnu Patruni
*      SRN: PES1UG24AM187

---

## 9. Conclusion

This project provides a hands-on understanding of containerization and OS internals, including process isolation, scheduling, and memory control. It simulates the core functionality of modern container systems like Docker in a simplified environment.

