## can 扩展帧格式 ##

![](https://i.imgur.com/vYNuhfY.png)

## can 29位ID分配 ##

    Protocol Version：2bit
    Profile ID：1bit，0：Can Device Profile；1：Can Cluster Library
    Destination Address Field：8bit[广播0xff
    网关默认地址0x00
    设备可用地址：1~254]
    Source Address Field：8bit
    Transaction sequence number：4bit
    Fragmentation ：2bit
    	00：Transmission is not fragmented.
    	01：Frame is first fragment of a fragmented transmission.(分包传输的第一包)
    	10：Frame is part of a fragmented transmission but not the first part.（分包，非第一包）
    	11：预留	
    Block Number：2bit
    	If the fragmentation sub-field is set to 01, then the block number sub-field indicate the number of blocks in the fragmented transmission. If the fragmentation sub-field is set to 10, then the block number sub-field indicate which block number of the transmission the current frame represents, taking the value 0x01 for the second fragment, 0x02 for the third, etc
    预留：2bit


|bit:27~28|bit:25~26|bit:23~24|bit:19~22|bit:11~18|bit:3~10|bit:2|bit:0~1
--|--|--|--|--|--|--|--
预留|Block Number|Fragmentation|Transaction sequence number|Source Address|Destination Address|Profile ID|Protocol Version
