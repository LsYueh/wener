---
title: Linux Releases
tags:
  - Version
---

# Linux Releases

:::tip

- 一般年底的最后一个版本会变成 LTS
- 一般 2-3 月 一个版本 - 一年 4 个版本
- LTS 支持 2-6 年
- SLTS kernel
  - 支持 5+ 年
  - 由 CIP 维护
- CIP kernel - 提供额外支持
  - Linux 4.4 - 支持到 2026/2036 年
  - CIP - Civil Infrastructure Platform
- RHEL 不遵循 LTS 版本 - 自己维护版本
  - RHEL 9.x - Linux 5.14

:::

| linux version | LTS |         SLTS | date       | EOL     | distro                              |
| :------------ | --: | -----------: | ---------- | ------- | ----------------------------------- |
| Linux 6.6     |  24 |              | 2023-10-30 | 2026-09 | alpine 3.20,3.19                    |
| Linux 6.1     |  23 | 4th, 2033-08 | 2022-12-31 | 2026-12 | alpine 3.18, debian 12 Brookworm    |
| [Linux 5.15]  |  22 |              | 2021-10-32 | 2023-10 | alpine 3.17,3.16,3.15, ubuntu 22.04 |
| Linux 5.14    |     |              |            |         | rhel 9                              |
| [Linux 5.10]  |  21 | 3rd, 2031-01 | 2020-12-13 | 2026-09 | alpine 3.14, debian 11 Bullseye     |
| [Linux 5.4]   |  20 |              | 2019-09-24 | 2025-09 | alpine 3.13, ubuntu 20.04           |
| [Linux 5.1]   |     |              | 2019-05-05 |         |                                     |
| [Linux 4.19]  |  19 | 2nd, 2029-01 | 2019-10-22 | 2024-12 | alpine 3.12, debian 10 Buster       |
| Linux 4.18    |     |              | 2018-08-12 | 2023-08 | rhel 8, centos 8                    |
| [Linux 4.4]   |  16 | 1st, 2027-01 | 2016-01-10 | 2022-02 | ubuntu 16.04                        |
| Linux 3.14    |     |              | 2014-03-30 |         |
| Linux 3.10    |     |              | 2013-06-30 |         | rhel 7, centos 7                    |
| Linux 2.6.32  |   3 |              | 2009-12-03 |         | rhel 6, centos 6                    |
| Linux 2.6.18  |     |              | 2006-09-20 |         | rhel 5, centos 5                    |

:::tip

- NTFS - linux 5.15
  - 在这之前 ntfs-3g
- exFAT - linux 5.4
  - 在这之前 exfat-fuse, exfat-utils
- io_uring - linux 5.1

:::

- https://kernelnewbies.org/LinuxVersions
- [Linux kernel version history](https://en.wikipedia.org/wiki/Linux_kernel_version_history)
- [Active kernel releases](https://www.kernel.org/category/releases.html)
- http://phb-crystal-ball.org/
- [cip-project](https://www.cip-project.org/)
  - CIP - Civil Infrastructure Platform - 民用基础设施平台
  - 提供 SLTS - 支持 25-50 年
  - 适用于 工业产品
  - [CIP Kernel Maintenance](https://wiki.linuxfoundation.org/civilinfrastructureplatform/cipkernelmaintenance)
- News
  - [Moving the kernel to modern C](https://lwn.net/SubscriberLink/885941/01fdc39df2ecc25f/)
    - C89 -> C99, C11
- [RHEL Reelease date](https://access.redhat.com/articles/3078)

[linux 5.15]: #linux-515
[linux 5.10]: #linux-510
[linux 5.4]: #linux-54
[linux 4.19]: #linux-519
[linux 4.4]: #linux-44

```bash
# CONFIG_IO_URING
grep io_uring_setup /proc/kallsyms
```

## Linux 6.7

- bcachefs
- Nouveau - Nvidia GSP 固件

## Linux 6.6

## Linux 6.5

- https://kernelnewbies.org/Linux_6.5

## Linux 6.1

- 支持 Rust 写内核模块

## Linux 5.15

- **NTFS**
- ksmbd - in-kernel SMB 3 server

## Linux 5.13

- 支持 zstd 压缩的模块 - `.ko.zst`
  - 之前支持 gzip 和 xz

## Linux 5.10

- EXT4
  - 支持 fast commit - fsync 和元数据操作更快 - mkfs 启用
  - 优化文件覆写
- XFS
  - 时间戳 2038 -> 2468
- Nintendo Switch Joy Cons 和 Pro 手柄控制器 - USB 和 蓝牙
- Raspberry Pi 4 VC4
- RISC-V boot EFI
- [Linux 5.10](https://kernelnewbies.org/Linux_5.10)

## Linux 5.8

- Raspberry Pi 4
- Broadcom BCM2711

## Linux 5.4

- **exFAT**
- virtio-fs
- fs-verity - 检测文件修改
  - 块级别，类似 dm-verity，支持 ext4、f2fs
- [Linux 5.10](https://kernelnewbies.org/Linux_5.4)

## Linux 4.8

- Support for using Transparent Huge Pages in the page cache
- Support for eXpress Data Path
- XFS reverse mapping
- Stricter checking of memory copies with hardened usercopy
- GCC plugin support
- virtio-vsocks for easier guest/host communication
- Support IPv6 security labeling (CALIPSO, RFC 5570)
- Add New Vegas TCP congestion control
- Documentation moved to the reStructuredText format

## Linux 4.7

- Support for Radeon RX480 GPUs
- Parallel directory lookups
- New 'schedutil" frequency governor
- Histograms of events in ftrace
- perf trace calls stack
- Allow BPF programs to attach to tracepoints
- EFI 'Capsule' firmware updates
- Support for creating virtual USB Device Controllers in USB/IP
- Android's sync_file fencing mechanism considered stable
- LoadPin, a security module to restrict the origin of kernel modules

## Linux 4.6

- USB 3.1 SuperSpeedPlus (10 Gbps) support
- Improve the reliability of the Out Of Memory task killer
- Support for Intel memory protection keys
- OrangeFS, a new distributed file system
- Kernel Connection Multiplexor, a facility for accelerating application layer protocols
- 802.1AE MAC-level encryption (MACsec)
- BATMAN V protocol
- dma-buf: new ioctl to manage cache coherency between CPU and GPU
- OCFS2 online inode checker
- Support for cgroup namespaces
- Add support for the pNFS SCSI layout

## Linux 4.5

- Copy offloading with new copy_file_range(2) system call
- Experimental PowerPlay supports brings high performance to the amdgpu driver
- Btrfs free space handling scalability improvements
- Support for GCC's Undefined Behavior Sanitizer (-fsanitize=undefined)
- Forwarded Error Correction support in the device-mapper's verity target
- Add MADV_FREE flag to madvise(2)
- Better epoll multithread scalability
- cgroup unified hierarchy is considered stable
- Performance improvements for SO_REUSEPORT UDP sockets
- Proper control of socket memory usage in the memory controller

## Linux 4.4

- https://kernelnewbies.org/Linux_4.4
- Faster and leaner loop device with Direct I/O and Asynchronous I/O support
- 3D support in virtual GPU driver
  - 3D 支持虚拟 GPU
- LightNVM adds support for Open-Channel SSDs
- TCP listener handling completely lockless, making TCP servers faster and more scalable
  - TCP 监听处理完全无锁, 使得 TCP 服务更快更高效.
  - [Commit](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=c3fc7ac9a0b978ee8538058743d21feef25f7b33)
- Journalled RAID5 MD support
- Unprivileged eBPF + persistent eBPF programs
- perf + eBPF integration
- Block polling support
- mlock2() syscall allow users to request memory to be locked on page fault

## Linux 4.3

- The Ext3 filesystem has been removed
- userfaultfd(), a system call for handling page-faults in user space
- membarrier(), a system call for issuing memory barriers on a set of threads
- New PID controller for limiting the number of PIDs in cgroups
- Ambient capabilities
- Introduce idle page tracking, a more precise way to track the memory being used by applications
- Support for IPv6 Identifier Locator Addressing
- Network light weight tunnels
- Virtual Routing and Forwarding (Lite) support
