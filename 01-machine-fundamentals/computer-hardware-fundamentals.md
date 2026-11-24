# Computer Hardware Fundamentals

## 1. Introduction

A computer is an electronic system that processes data, stores information, and communicates with other devices.

Its major operations are:

- **Processing:** Executing instructions and performing calculations.
- **Memory:** Temporarily holding data and instructions currently in use.
- **Storage:** Retaining data even when the computer is powered off.
- **Communication:** Transferring data between devices.
- **Power management:** Supplying and regulating electrical power.

## 2. Central Processing Unit (CPU)

The CPU is the primary processing unit of a computer. It executes instructions and coordinates operations between different hardware components.

### 2.1 Main CPU Components

| Component | Responsibility |
|---|---|
| Control Unit (CU) | Coordinates instruction execution and controls data movement within the CPU. |
| Arithmetic Logic Unit (ALU) | Performs arithmetic and logical operations. |
| Registers | Very small, high-speed storage locations inside the CPU that hold data and instructions currently being processed. |
| Cache | Stores frequently accessed data and instructions to reduce the time required to access them. |
| Memory Management Unit (MMU) | Manages memory address translation and memory access permissions. |

### 2.2 CPU Cache

Cache is a small, high-speed memory located inside or close to the CPU. It stores frequently used data and instructions so the CPU does not need to access RAM for every operation.

Cache levels:

- **L1 Cache:** Smallest and fastest cache, usually dedicated to individual CPU cores.
- **L2 Cache:** Larger than L1 but generally slower.
- **L3 Cache:** Usually larger than L1 and L2 and often shared among multiple CPU cores.

### 2.3 Memory Management Unit (MMU)

The MMU is a hardware component responsible for managing memory address translation and access permissions.

Applications use virtual addresses rather than directly working with physical RAM addresses.

The MMU translates virtual addresses into physical memory addresses using page tables maintained by the operating system.

Its responsibilities include:

- Translating virtual addresses into physical addresses.
- Enforcing memory access permissions.
- Isolating the memory spaces of different processes.
- Supporting virtual memory.

**Virtual Address (VA):** An address used by a process to refer to a location in its virtual memory space.

**Physical Address (PA):** The actual address of a location in physical RAM.

The operating system manages virtual memory, while the MMU performs the hardware-level address translation.

## 3. Binary, Bits and Bytes

Computers represent and process information using binary values.

- **Bit:** The smallest unit of data, represented by either `0` or `1`.
- **Byte:** A group of 8 bits.

Common storage units:

| Unit | Size |
|---|---:|
| 1 Byte | 8 bits |
| 1 KB | 1,024 Bytes |
| 1 MB | 1,024 KB |
| 1 GB | 1,024 MB |
| 1 TB | 1,024 GB |

## 4. Motherboard

The motherboard is the main circuit board that connects the computer's hardware components and allows them to communicate.

### 4.1 Important Motherboard Components

**CPU Socket**

The physical connection where the CPU is installed.

**RAM Slots**

Slots used to install RAM modules.

**Chipset**

A collection of motherboard controllers that manages communication between the CPU and certain peripheral devices. Its responsibilities depend on the motherboard architecture.

**PCIe (Peripheral Component Interconnect Express)**

A high-speed interface used to connect expansion devices such as:

- Graphics cards.
- Network cards.
- Storage controllers.
- Other expansion cards.

**BIOS / UEFI**

Firmware responsible for initializing hardware during startup and selecting a bootable device or bootloader to continue the boot process.

- BIOS is the older firmware interface.
- UEFI is its modern replacement and supports additional features such as Secure Boot and GPT booting.

**CMOS Battery**

A small battery that helps maintain the real-time clock and certain firmware settings when the computer is powered off.

## 5. Primary Memory (RAM)

RAM (Random Access Memory) is temporary memory used by the computer to store data and instructions that are actively being used.

Characteristics:

- Volatile memory: Its contents are lost when power is removed.
- Faster than persistent storage devices.
- Directly accessible by the CPU through the memory subsystem.
- Used by running applications and the operating system.

Example:

When an application is launched, its executable code and required data are loaded into memory so the CPU can execute its instructions.

## 6. Secondary Storage

Secondary storage retains data even when the computer is powered off.

Common storage devices include:

**HDD (Hard Disk Drive)**

- Uses rotating magnetic disks to store data.
- Contains mechanical components.
- Generally slower than SSDs.
- Often provides large storage capacity at a lower cost.

**SSD (Solid State Drive)**

- Uses flash memory to store data.
- Has no moving mechanical parts.
- Generally faster than HDDs.
- Commonly used for operating systems and applications.

### RAM vs Storage

| Feature | RAM | SSD / HDD |
|---|---|---|
| Purpose | Temporary working memory | Persistent data storage |
| Volatility | Volatile | Non-volatile |
| Speed | Faster | Slower than RAM |
| Data retention | Lost when power is removed | Retained without power |
| Usage | Running applications and processes | OS, applications and files |

## 7. Other Important Hardware Components

**GPU (Graphics Processing Unit)**

A processor specialized in graphics operations and parallel processing. It is commonly used for rendering images, video processing, and computational workloads.

**PSU (Power Supply Unit)**

Converts electrical power from the wall outlet into regulated power required by computer components.

**NIC (Network Interface Card)**

A hardware component that allows a computer to connect to a network through wired or wireless communication.

Examples:

- Ethernet network adapter.
- Wi-Fi adapter.

## 8. High-Level Computer Startup Overview

When a computer is powered on, several components work together to start the operating system.

A simplified overview:

1. The power supply provides power to the hardware.
2. BIOS/UEFI firmware initializes essential hardware.
3. Firmware identifies a bootable device and starts the bootloader.
4. The bootloader loads the Linux kernel into memory.
5. The kernel initializes hardware, memory management, and other essential subsystems.
6. The kernel starts the initial user-space process, commonly `systemd` on modern Linux distributions.

This is only a high-level overview. The complete Linux boot process involves additional stages and will be covered separately.

## 9. Practical Hardware Inspection Commands

Linux provides commands to inspect hardware and system information.

| Command | Purpose |
|---|---|
| `cat /etc/os-release` | Displays Linux distribution information. |
| `uname -r` | Displays the running kernel version. |
| `lscpu` | Displays CPU architecture and processor information. |
| `free -h` | Displays RAM and swap memory usage. |
| `lsblk` | Lists block storage devices and partitions. |

Example:

```bash
lscpu
free -h
lsblk
```

## 10. Key Concepts to Remember

- The CPU executes instructions and performs calculations.
- Registers and cache provide fast access to data needed by the CPU.
- The MMU translates virtual addresses into physical memory addresses and enforces memory access permissions.
- The motherboard connects and coordinates hardware components.
- BIOS/UEFI firmware initializes hardware and begins the boot process.
- RAM provides temporary working memory.
- SSDs and HDDs provide persistent storage.
- The GPU handles graphics and parallel-processing workloads.
- The PSU supplies electrical power.
- The NIC enables network communication.

## 11. Learning Progress

| Topic | Status |
|---|---|
| Computer hardware fundamentals | Studied |
| CPU and its components | Studied |
| RAM and secondary storage | Studied |
| Motherboard and its components | Studied |
| MMU and virtual memory concepts | Introduced and studied at a basic level |
| High-level startup overview | Introduced only |
| Complete Linux boot process | Not yet studied |

**Next topic:** Linux Boot Process.