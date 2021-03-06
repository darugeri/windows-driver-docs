---
title: NVMe Features Supported by StorNVMe
description: NVMe Features Supported by StorNVMe
ms.assetid: 96b62fbb-bcf3-402d-ba29-0a61dc95c92c
ms.date: 05/12/2020
ms.localizationpriority: medium
---

# NVMe Features Supported by StorNVMe

The following matrix lists NVME features and indicates the support provided by **StorNVMe** on Windows 10 version 1903 and later versions.

See [Working with NVMe drives](https://docs.microsoft.com/windows/win32/fileio/working-with-nvme-devices#protocol-specific-queries) for additional information.

| Feature  | Supported | Comments |
| :------- | :-------: | :------- |
| Firmware Update Process                                        | X |  Supports Slot 1 READ-ONLY, multiple slots for Commit/Download. Aligns to controller reported FW Update Granularity. |
| Firmware Activation without Reset                              | X | |
| Metadata Handling                                              |   | |
| End-to-End Data Protection                                     |   | |
| Power Management                                               | X | Supports non-operational power states. Autonomous power state transitions are disabled by default. Runtime D3 transitions are enabled by default for selected platforms in Modern Stand-by. Host controlled thermal management Get and Set features supported through IOCTL_STORAGE_QUERY_PROPERTY and IOCTL_STORAGE_SET_PROPERTY, respectively. |
| Virtualization Enhancements                                    |   | |
| Doorbell Stride for Software Emulation                         |   | |
| Standard Vendor Specific Command Format                        |   | |
| Reservations                                                   |   | |
| Host Memory Buffer                                             | X | |
| Replay Protected Memory Block                                  |   | |
| Device Self-test Operations                                    | X | No native support; feature available through IOCTL_STORAGE_PROTOCOL_COMMAND.|
| Namespace Management                                           | X | No native support; feature available through IOCTL_STORAGE_PROTOCOL_COMMAND in WinPE mode. |
| Boot Partitions                                                |   | |
| Telemetry                                                      | X | Supported through IOCTL_SCSI_PASS_THROUGH using command SCSIOP_READ_DATA_BUFF16 with buffer mode as READ_BUFFER_MODE_ERROR_HISTORY. Also available through StorageAdapterProtocolSpecificProperty/StorageDeviceProtocolSpecificProperty from IOCTL_STORAGE_QUERY_PROPERTY. For host telemetry, this is also available through IOCTL_STORAGE_GET_DEVICE_INTERNAL_LOG starting with Windows 10, version 2004. |
| Sanitize Operations                                            | X | Supported through IOCTL_STORAGE_PROTOCOL_COMMAND in WinPE mode. |
| Read Recovery Level                                            |   | |
| Endurance Groups                                               | X | Information can be retrieved through IOCTL_STORAGE_QUERY_PROPERTY |
| Predictable Latency Mode                                       |   | |
| Namespace Write Protection                                     |   | |
| Asymmetric Namespace Access Reporting                          |   | |
| Get LBA Status                                                 |   | |
| SQ Associations                                                |   | |
| UUIDs for Vendor Specific Information                          |   | |
| Improving Performance through I/O Size and Alignment Adherence | X | Supports Namespace Optimal IO Boundary (NOIOB). Currently doesn't support NPWG, NPWA, NPDG, NPDA, and NOWS |

## Reference Links

- [Working with NVMe Devices](https://docs.microsoft.com/windows/win32/fileio/working-with-nvme-devices)
- [NVMe Storage Protocol Data Type](https://docs.microsoft.com/windows/win32/api/winioctl/ne-winioctl-storage_protocol_nvme_data_type)
