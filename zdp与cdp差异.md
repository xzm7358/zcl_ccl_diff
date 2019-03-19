# zdp与cdp差异

## 2.4  The ZigBee Device Profile

### 2.4.3  Client Services  #

2.4.3.1  Device and Service Discovery Client Services 
----------

- Active_EP_req

Protocol|payload
--|--
zcl|NWKAddr(2)
ccl|无


----------
- Simple_Desc_req

Protocol|payload0|payload1
--|--|--
zcl|NWKAddr(2)|EndPoint(1)
ccl|EndPoint(1)

2.4.3.2  End Device Bind, Bind, Unbind, and Bind Management Client Services Primitives
----------
- Bind_req

Protocol|payload0|payload1|payload2|payload3|payload4|payload5
--|--|--|--|--|--|--
zcl|SrcAddress(8)| SrcEndp(1) | ClusterID(2)  |DstAddrMode(1)  |DstAddress(2/8)  |DstEndp(1)
ccl|SrcAddress(1) | SrcEndp(1) | ClusterID(1)| DstAddress(1) | DstEndp(1)

- UnBind_req

Protocol|payload0|payload1|payload2|payload3|payload4|payload5
--|--|--|--|--|--|--
zcl|SrcAddress(8)| SrcEndp(1) | ClusterID(2)  |DstAddrMode(1)  |DstAddress(2/8)  |DstEndp(1)
ccl|SrcAddress(1) | SrcEndp(1) | ClusterID(1)| DstAddress(1) | DstEndp(1)

----------
- Device_annce

Protocol|payload0|payload1|payload2
--|--|--|--
zcl|NWKAddr(2) | IEEEAddr(8) | Capability(1) 
ccl|NWKAddr(1) | IEEEAddr(6)

2.4.3.3  Network Management Client Services
----------
- Mgmt_Leave_req

Protocol|payload0|payload1|payload2|payload3
--|--|--|--|--
zcl|IEEEAddr(Bits: 64)| Reserved(Bits: 6) | Remove_Children(Bits: 1) | Rejoin(Bits: 1)
ccl|NWKAddr(1) | IEEEAddr(6)




# 2.4.4  Server Services  #

2.4.4.2  Device and Service Discovery Server 
----------
- Active_EP_rsp

Protocol|payload0|payload1|payload2|payload3
--|--|--|--|--
zcl|Status(1)|  NWKAddr(2) | ActiveEPCount(1) | ActiveEPList[]
ccl|ActiveEPCount(1)|  File_Version(1) |Image_type(2)


----------
- Simple_Desc_rsp

Protocol|payload0|payload1|payload2|payload3
--|--|--|--|--
zcl|Status(1)|  NWKAddr(2) | Length(1) | Simple_Descriptor 
ccl|Status(1)  |EndPoint(1)|  DeviceID(2)


2.4.4.3  End Device Bind, Bind, Unbind Bind Management Server Services
----------
- Bind_rsp

Protocol|payload0
--|--
zcl|Status(1)
ccl|Status(1)

- UnBind_rsp

Protocol|payload0
--|--
zcl|Status(1)
ccl|Status(1)

2.4.4.4  Network Management Server Services
----------
- Mgmt_Leave_rsp

Protocol|payload0
--|--
zcl|Status(1)
ccl|Status(1)
