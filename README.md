# 🐳 OS Jackfruit – Mini Container Runtime

## 📌 Overview

This project implements a **lightweight container runtime in C**, inspired by Docker. It demonstrates core **Operating System concepts** such as process isolation, memory management, and inter-process communication using Linux system calls and kernel modules.

The system consists of:

* A **user-space container engine (`engine.c`)**
* A **kernel-space memory monitor (`monitor.c`)**

---

## 🚀 Features

### 🔹 Container Runtime

* Create and manage multiple containers
* Process isolation using:

  * Namespaces
  * `chroot()` filesystem isolation
* Supports running independent root filesystems

### 🔹 CLI Interface

Commands implemented:

* `start` → Start a container
* `stop` → Stop a container
* `ps` → List running containers
* `logs` → View container logs

---

### 🔹 Logging System

* Captures container output
* Uses pipes and buffering
* Stores logs for each container

---

### 🔹 Memory Monitoring (Kernel Module)

* Tracks memory usage of containers
* Enforces:

  * **Soft limit** → Warning message
  * **Hard limit** → Terminates container

---

## 🛠️ Tech Stack

* **Language:** C
* **Platform:** Linux (Ubuntu recommended)
* **Concepts Used:**

  * Process Management (`fork`, `clone`)
  * Namespaces
  * Signals
  * Kernel Modules
  * Inter-Process Communication (IPC)

---

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/OS-Jackfruit.git
cd OS-Jackfruit
```

### 2. Install dependencies

```bash
sudo apt update
sudo apt install build-essential linux-headers-$(uname -r)
```

### 3. Build the project

```bash
make
```

### 4. Load kernel module

```bash
sudo insmod monitor.ko
```

---

## ▶️ Usage

### Start supervisor

```bash
sudo ./engine supervisor ./rootfs-base
```

### Start a container

```bash
sudo ./engine start alpha ./rootfs-alpha /bin/sh
```

### List containers

```bash
sudo ./engine ps
```

### View logs

```bash
sudo ./engine logs alpha
```

### Stop container

```bash
sudo ./engine stop alpha
```

---

## 🧪 Test Cases

### ✅ Test 1: Multiple Containers

* Started 2 containers simultaneously
* Result: Both executed independently

### ✅ Test 2: Soft Memory Limit

* Exceeded soft limit
* Result: Warning logged

### ✅ Test 3: Hard Memory Limit

* Exceeded hard limit
* Result: Container terminated

### ✅ Test 4: Logging

* Verified container output stored correctly

### ✅ Test 5: CLI Commands

* `ps`, `logs`, `stop` executed successfully

---

## 📽️ Demonstration

The project demonstration includes:

* Starting the supervisor
* Running multiple containers
* Viewing logs
* Demonstrating memory limit enforcement
* Stopping containers

---

## 👥 Team Members

* Student 1: [Your Name]
* Student 2: [Teammate Name]

---

## 📚 Conclusion

This project provides a hands-on understanding of **containerization and OS internals**, including process isolation, scheduling, and memory control. It simulates the core functionality of modern container systems like Docker in a simplified environment.


