# zcl与ccl差异

### 1.Command Frame Formats差异

- General ZCL Frame Format

|Bits: 8 | 0/16 | 8 | 8 | Variable|
| --| -- | -- | -- | -- |
|Frame control | Manufacturer code| Transaction sequence number| Command identifier|  Frame payload|
||||ZCL header | ZCL payload |

- Frame Control Field

|Bits: 0-1|  2 | 3 | 4|  5-7 |
| --| -- | -- | -- | -- |
|Frame type | Manufacturer specific|  Direction | Disable Default Response | Reserved|

- General CCL Frame Format

|D0|	D1|	D2|	D3	|D4~D7|
| --| -- | -- | -- | -- |
|Endpoint|	Cluster Id|	Frame control	|Command Id	|Frame payload|
||||CCL header | CCL payload |

- Frame Control Field

|Bits: 0-1|  2 | 3 | 4|  5-7 |
| --| -- | -- | -- | -- |
|Frame type | Manufacturer specific|  Direction | Disable Default Response | Reserved|

### 2.cluster Id 差异（zcl为2个字节，ccl为1个字节）

- 0x0000~0x000f映射为0x00-0x0f
- 0x0100~0x010f映射为0x10-0x1f
- 0x0200~0x020f映射为0x20-0x2f
- 0x0300~0x030f映射为0x30-0x3f
- 0x0400~0x040f映射为0x40-0x4f
- 0x0500~0x050f映射为0x50-0x5f

### 3.Attribute Id 差异（zcl为2个字节，ccl为1个字节）

- 原来0x0040以前的还跟原来一样，从0x4000开始的Id改为从0x40开始，自定义的属性Id从0x50开始

### 4.场景差异（去掉group Id）

Format of the Add Scene Command Payload 
----------

| Protocol | payload0 | payload1            | payload2        | payload3        | payload4                               |
| -------- | -------- | ------------------- | --------------- | --------------- | -------------------------------------- | 
| zcl      | Group ID | Scene ID            | Transition time | Scene Name      | Extension field sets,  one per cluster |
| ccl      | Scene ID | extension field set |                 |                 |                                        |

Extension field sets =  
 {{clusterId 1, length 1, {extension field set 1}}, {clusterId 2, length 2, {extension field set 2}} ...}. 
