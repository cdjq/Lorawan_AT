# AT指令表


所有AT指令都以\r\n结尾



## 基础AT指令 

-----------------

### 1. 测试指令AT

<table>
    <tr>
        <td rowspan="2">AT</td>    
    	 <td>返回OK, 已经进入AT模式</td> 
    </tr>
    <tr>
        <td>无返回值，当前不是AT模式</td> 
    </tr>
</table>




举例

```
AT
OK
```

-------------------

### 2. 退出AT模式

<table>
    <tr>
        <td rowspan="2">AT+EXIT</td>    
    	 <td>返回OK, 已经退出AT模式</td> 
    </tr>
    <tr>
        <td>无返回值，当前不是AT模式</td> 
    </tr>
</table>


举例

```
AT+EXIT
+EXIT=OK
```



## 产品相关AT指令 

-------------------

### 1. 厂商
只可查询，不可写入

<table>
    <tr>
        <td>AT+MANUFACTURER</td>    
    	 <td>AT+MANUFACTURER? 查询厂商<br>+MANUFACTURER=DFROBOT 厂商为DFROBOT</td> 
    </tr>
</table>


举例

```
AT+MANUFACTURER？
+MANUFACTURER=DFROBOT
```

-------------------

### 2. 产品
只可查询，不可写入

<table>
    <tr>
        <td>AT+PRODUCT</td>    
    	 <td>AT+PRODUCT? 查询产品名称<br>+PRODUCT=DF-LORA-470 产品名称为DF-LORA-470</td> 
    </tr>
</table>


举例

```
AT+MANUFACTURER？
+MANUFACTURER=DFROBOT
```

-------------------

### 3. 硬件版本
只可查询，不可写入

<table>
    <tr>
        <td>AT+HWVERSION</td>    
    	 <td>AT+HWVERSION? 查询产品名称<br>+HWVERSION=<version></td> 
    </tr>
</table>


举例

```
AT+HWVERSION？
+HWVERSION=V0.0.1
```

-------------------

### 4. 软件版本
只可查询，不可写入

<table>
    <tr>
        <td>AT+SWVERSION</td>    
    	 <td>AT+SWVERSION? 查询固件版本<br>+SWVERSION=<version></td> 
    </tr>
</table>


举例

```
AT+SWVERSION？
+SWVERSION=DFROBOT
```

-------------------

### 5. 序列号
只可查询，不可写入

<table>
    <tr>
        <td>AT+SN</td>    
    	 <td>AT+SN? 查询序列号<br>+SN=<sn></td> 
    </tr>
</table>


举例

```
AT+SN？
+SN=FFEE123AB455CCDD
```





## Lorawan节点配置信息AT指令 

-------------------

### 1. 入网方式

<table>
    <tr>
        <td rowspan="2">AT+JOINTYPE</td>    
    	 <td>AT+JOINTYPE? 查询当前入网方式<br>+JOINTYPE=OTAA OTAA方式入网<br>+JOINTYPE=APB APB方式入网</td> 
    </tr>
    <tr>
        <td>AT+JOINTYPE=OTAA 设置未OTAA方式入网<br>AT+JOINTYPE=APB 设置未APB方式入网</td> 
    </tr>
</table>


举例

```
AT+JOINTYPE?
+JOINTYPE=APB
AT+JOINTYPE=OTAA
AT+JOINTYPE?
+JOINTYPE=OTAA
```

--------------

### 2.  设备DEVEUI（不对用户开放）

DEVEUI作为设备的唯一ID，每个设备都不同



FEFFFFDF 01 000000 （01代表开源硬件DTU设备）
FEFFFFDF 11 000000 （11代表工业硬件DTU设备）
FEFFFFDF 12 000000 （12代表工业硬件IO设备）
FEFFFFDF 13 000000 （13代表工业硬件ADC设备）
FEFFFFDF 14 000000 （14代表工业硬件485设备）



<table>
    <tr>
        <td rowspan="2">AT+DEVEUI</td>    
    	 <td>AT+DEVEUI? 查询当前的DEVEUI<br>+DEVEUI=<8 bytes> </td> 
    </tr>
    <tr>
        <td>AT+DEVEUI=<8 bytes> 设置设备的DEVEUI</td> 
    </tr>
</table>


举例

```
AT+DEVEUI?
+DEVEUI=DFDFDFDF11223344
AT+DEVEUI=DFDFDFDF11223355
AT+DEVEUI?
+DEVEUI=DFDFDFDF11223355
```

----------------------

### 3. 设备JOINEUI

JOINEUI可以理解未分组，网关可以根据不同的分组采取不同的测量，例如拦截特定分组，放行

<table>
    <tr>
        <td rowspan="2">AT+JOINEUI</td>    
    	 <td>AT+DEVEUI? 查询当前的DEVEUI<br>+DEVEUI=<8 bytes> </td> 
    </tr>
    <tr>
        <td>AT+JOINEUI=<8 bytes> 设置设备的DEVEUI</td> 
    </tr>
</table>


举例

```
AT+JOINEUI?
+JOINEUI=DFDFDFDF00000000
AT+JOINEUI=DFDFDFDF00000055
AT+JOINEUI?
+JOINEUI=DFDFDFDF00000055
```

-----------------

### 4. 设备APPKEY
<table>
    <tr>
        <td rowspan="2">AT+APPKEY</td>    
    	 <td>AT+DEVEUI? 查询当前的APPKEY<br>+DEVEUI=<16 bytes> </td> 
    </tr>
    <tr>
        <td>AT+JOINEUI=<16 bytes> 设置设备的DEVEUI</td> 
    </tr>
</table>


举例

```
AT+APPKEY?
+APPKEY=0102030405060708090A0B0C0D0E0F10
AT+APPKEY=0102030405060708090A0B0C0D0E0F11
AT+APPKEY?
+APPKEY=0102030405060708090A0B0C0D0E0F11
```

-----------------

### 5. 设备DEVADDR

在OTAA模式下，入网后可以查询不可更改；在APB模式下，直接可查询可更改

<table>
    <tr>
        <td rowspan="2">AT+DEVADDR</td>    
    	 <td>AT+DEVEUI? 查询当前的DEVADDR<br>+DEVEUI=<16 bytes> </td> 
    </tr>
    <tr>
        <td>AT+JOINEUI=<16 bytes> 设置设备的DEVADDR</td> 
    </tr>
</table>


举例

```
#APB模式
AT+DEVADDR?
+DEVADDR=01020304
AT+DEVADDR=0B0C0D0E
OK
AT+APPKEY?
+APPKEY=0B0C0D0E

#OTAA模式入网前
AT+DEVADDR?
+DEVADDR=NULL
#OTAA模式入网后
AT+DEVADDR?
+DEVADDR=01020304
AT+DEVADDR=0B0C0D0E
FAIL
AT+APPKEY?
+APPKEY=01020304
```

-----------------

### 6. 设备NWKSKEY

在OTAA模式下，入网后可以查询不可更改；在APB模式下，直接可查询可更改

<table>
    <tr>
        <td rowspan="2">AT+NWKSKEY</td>    
    	 <td>AT+NWKSKEY? 查询当前的NWKSKEY<br>+DEVEUI=<16 bytes> </td> 
    </tr>
    <tr>
        <td>AT+NWKSKEY=<16 bytes> 设置设备的NWKSKEY</td> 
    </tr>
</table>


举例

```
#APB模式
AT+NWKSKEY?
+NWKSKEY=0102030405060708090A0B0C0D0E0F10
AT+NWKSKEY=0102030405060708090A0B0C0D0E0F11
OK
AT+NWKSKEY?
+NWKSKEY=0102030405060708090A0B0C0D0E0F11

#OTAA模式入网前
AT+NWKSKEY?
+NWKSKEY=NULL
#OTAA模式入网后
AT+NWKSKEY?
+NWKSKEY=0102030405060708090A0B0C0D0E0F10
AT+NWKSKEY=0102030405060708090A0B0C0D0E0F11
FAIL
AT+NWKSKEY?
+NWKSKEY=0102030405060708090A0B0C0D0E0F10
```

-----------------

###  7. 设备APPSKEY

在OTAA模式下，入网后可以查询不可更改；在APB模式下，直接可查询可更改

<table>
    <tr>
        <td rowspan="2">AT+APPSKEY</td>    
    	 <td>AT+APPSKEY? 查询当前的APPSKEY<br>+APPSKEY=<16 bytes> </td> 
    </tr>
    <tr>
        <td>AT+NWKSKEY=<16 bytes> 设置设备的APPSKEY</td> 
    </tr>
</table>



举例

```
#APB模式
AT+APPSKEY?
+APPSKEY=0102030405060708090A0B0C0D0E0F10
AT+APPSKEY=0102030405060708090A0B0C0D0E0F11
OK
AT+APPSKEY?
+APPSKEY=0102030405060708090A0B0C0D0E0F11

#OTAA模式入网前
AT+APPSKEY?
+APPSKEY=NULL
#OTAA模式入网后
AT+APPSKEY?
+APPSKEY=0102030405060708090A0B0C0D0E0F10
AT+APPSKEY=0102030405060708090A0B0C0D0E0F11
FAIL
AT+APPSKEY?
+APPSKEY=0102030405060708090A0B0C0D0E0F10
```

-----------------

### 8. 设备NETID

入网后可查询，APB入网如何获取NETID

<table>
    <tr>
        <td rowspan="2">AT+NETID</td>    
    	 <td>AT+NETID? 查询当前的NETID<br>+NETID=<3 bytes> </td> 
    </tr>
    <tr>
        <td>AT+NWKSKEY=<3 bytes> 设置设备的NETID</td> 
    </tr>
</table>


举例

```
AT+NETID?
+NETID=010203
AT+NETID=020304
FAIL
```

-----------------

### 9. 发起入网

在OTAA模式下

<table>
    <tr>
        <td rowspan="2">AT+JOIN</td>    
    	 <td>AT+JOIN? 查询是否入网<br>+JOIN=1 已经入网<br>+JOIN=0 没有入网</td> 
    </tr>
    <tr>
        <td>AT+JOIN 发起入网</td> 
    </tr>
</table>


举例

```
AT+JOIN
OK
AT+JOIN?
+JOIN=1  #已经入网
AT+JOIN?
+JOIN=0  #没有入网
```

-------------------------------

### 10.  通信端口

设备采集的数据将从这个端口上发到网关，范围0-255，不可使用0，224

<table>
    <tr>
        <td rowspan="2">AT+PORT</td>    
    	 <td>AT+PORT? 查询是否入网<br>+PORT=2 使用端口2</td> 
    </tr>
    <tr>
        <td>AT+PORT=<1 byte> 这只通信端口</td> 
    </tr>
</table>


举例

```
AT+PORT?
+PORT=3
AT+PORT=2
OK
AT+PORT=2000
FAIL
AT+PORT?
+PORT=2
```
-----------------------------------

### 11. 通信频点（待补充）********

设备采集的数据将从这个端口上发到网关，范围0-255，不可使用0，224

<table>
    <tr>
        <td rowspan="2">AT+PORT</td>    
    	 <td>AT+FREQS? 查询是否入网<br>+FREQS=2 使用端口2</td> 
    </tr>
    <tr>
        <td>AT+FREQS=<1 byte> 这只通信端口</td> 
    </tr>
</table>


举例

```
AT+PORT?
+PORT=3
AT+PORT=2
OK
AT+PORT=2000
FAIL
AT+PORT?
+PORT=2
```

---------------------------------

### 12. 地区（只可查询）

当前支持CN470 US915 EU868

<table>
    <tr>
        <td rowspan="2">AT+REGION</td>    
    	 <td>AT+REGION? 查询当前地区<br>+REGION=CN470 当前地区为CN470</td> 
    </tr>
    <tr>
        <td>AT+REGION=CN470 这是不允许设置的</td> 
    </tr>
</table>


举例

```
AT+REGION?
+REGION=CN470
```

---------------------------

### 13. 子频段Subband

CN470 范围1-12， 默认为2
US915 范围1-9，   默认为8
EU868没有subband
这里给出频段表****
<table>
    <tr>
        <td rowspan="2">AT+SUBBAND</td>    
    	 <td>AT+SUBBAND? 查询当前地区<br>+SUBBAND=3 当前子频段为3</td> 
    </tr>
    <tr>
        <td>AT+SUBBAND=n 设置当前地区为n</td> 
    </tr>
</table>


举例

```
AT+SUBBAND?
+SUBBAND=2
AT+SUBBAND=100
FAIL
AT+SUBBAND=5
OK
AT+SUBBAND?
+SUBBAND=5
```


----------------------------------

### 14. 天线增益

默认天线增益为2.15
<table>
    <tr>
        <td rowspan="2">AT+ANTENNAGAIN</td>    
    	 <td>AT+ANTENNAGAIN? 查询当前地区<br>+ANTENNAGAIN=3.5 当前天线增益为3.5</td> 
    </tr>
    <tr>
        <td>AT+ANTENNAGAIN=n 设置天线增益为n</td> 
    </tr>
</table>


举例

```
AT+ANTENNAGAIN?
+ANTENNAGAIN=2.15
AT+ANTENNAGAIN=3.5
OK
AT+ANTENNAGAIN?
+ANTENNAGAIN=5
```

-------------------------

### 15. 最大发射功率

CN470 范围0-19
EU868 范围0-16
US915 范围0-30

<table>
    <tr>
        <td rowspan="2">AT+EIRP</td>    
    	 <td>AT+EIRP? 查询当前地区<br>+EIRP=18 当前最大发射功率为18</td> 
    </tr>
    <tr>
        <td>AT+EIRP=n 设置最大发射功率为n</td> 
    </tr>
</table>


举例

```
AT+EIRP?
+EIRP=19
AT+EIRP=16
OK
AT+EIRP?
+EIRP=16
```

------------------------------

### 16. 通信速率
通信速率是扩频因子SF和带宽BW共同决定的一个参数
CN470 范围0-5     默认值
EU868 范围0-6  一般不使用6  默认值
US915 范围0-4  8-13     默认值

<table>
    <tr>
        <td rowspan="2">AT+DATARATE</td>    
    	 <td>AT+DATARATE? 查询通信速率<br>+DATARATE=3 当前通信速率为3</td> 
    </tr>
    <tr>
        <td>AT+DATARATE=n 设置最大发射功率为n</td> 
    </tr>
</table>


举例

```
AT+DATARATE?
+DATARATE=5
AT+DATARATE=3
OK
AT+DATARATE?
+DATARATE=3
```

---------------------

### 17. 信噪比

查询上一次接收到的数据帧的信噪比，值越大，信号质量越好
正数：信号 > 噪声
负数：信号 < 噪声

<table>
    <tr>
        <td rowspan="2">AT+SNR</td>    
    	 <td>AT+SNR? 查询信噪比<br>+SNR=3 上一帧信噪比为3</td> 
    </tr>
    <tr>
        <td>此命令不支持设置</td> 
    </tr>
</table>


举例

```
#还没接收过数据
AT+SNR?
+SNR=NULL
#已经接收过数据
AT+SNR?
+SNR=9
```

-------------------------

### 18. 信号强度
查询上一次接收到的数据帧的信号强度，为负数，值越靠近0，信号强度越好

<table>
    <tr>
        <td rowspan="2">AT+RSSI</td>    
    	 <td>AT+RSSI? 查询信号强度<br>+RSSI=-20 上一帧信号强度为-20</td> 
    </tr>
    <tr>
        <td>此命令不支持设置</td> 
    </tr>
</table>


举例

```
#还没接收过数据
AT+RSSI?
+RSSI=NULL
#已经接收过数据
AT+RSSI?
+RSSI=-20
```

------------------------

###  19. 上传包类型
CONFIRMED包，需要网关回复ACK信号，如果没有收到ACK，包会重传
UNCONFIRMED包，不需要网关回复ACK信号，传输特定包数量后，需要网关回复ACK信号

看起来 CONFIRMED包 通信效果更好，但是限于网关的通信性能。过多的 CONFIRMED包会造成网关通信负担，网关丢包率会上升，负载能力下降，对于半双工网关，负担会更明显

<table>
    <tr>
        <td rowspan="2">AT+UPLINKTYPE</td>    
    	 <td>AT+UPLINKTYPE? 查询上传包类型<br>+UPLINKTYPE=CONFIRMED 确认包<br>+UPLINKTYPE=UNCONFIRMED 非确认包</td> 
    </tr>
    <tr>
        <td>AT+UPLINKTYPE=UNCONFIRMED 设置上传包为非确认包<br>AT+UPLINKTYPE=CONFIRMED 设置上传包为确认包</td> 
    </tr>
</table>


举例

```
AT+UPLINKTYPE?
+UPLINKTYPE=CONFIRMED
AT+UPLINKTYPE=UNCONFIRMED
AT+UPLINKTYPE?
+UPLINKTYPE=UNCONFIRMED
```

---------------------------

### 20. 上发数据

<table>
    <tr>
        <td rowspan="2">AT+SEND</td>    
    	 <td>AT+SEND? 没必要查询</td> 
    </tr>
    <tr>
        <td>AT+SEND=ABCDEFG 发送数据ABCDEFG到网关</td> 
    </tr>
</table>


举例

```
AT+SEND="ABCDEFG"
+SEND:MaxLength=7
AT+SEND="3355AABB"
+SEND:MaxLength=8
```
-------------------------

### 21. 重传次数

<table>
    <tr>
        <td rowspan="2">AT+NBTRIALS</td>    
    	 <td>AT+NBTRIALS? 查询CONFIRMED包的重传次数</td> 
    </tr>
    <tr>
        <td>AT+NBTRIALS=2 设置CONFIRMED包的重传次数为2</td> 
    </tr>
</table>


举例

```
AT+NBTRIALS?
+NBTRIALS=3
AT+NBTRIALS=2
OK
AT+NBTRIALS?
+NBTRIALS=2
```

-------------------------------

### 22. 设备类型

当前支持A类设备和C类设备，不支持B类设备

<table>
    <tr>
        <td rowspan="2">AT+CLASS</td>    
    	 <td>AT+CLASS? 查询当前设备类型<br>+CLASS=A A类设备<br>+CLASS=C C类设备</td> 
    </tr>
    <tr>
        <td>AT+CLASS=A 设置设备未A类设备</td> 
    </tr>
</table>


举例

```
AT+CLASS?
+CLASS=A
AT+CLASS=C
OK
AT+CLASS=B
FAIL
AT+CLASS?
+CLASS=C
```

-------------------------------

### 23. 设备地理位置信息（经纬度，海拔）

默认值为成都地理位置信息 104.06E,30.67N,500
海拔支持负数
<table>
    <tr>
        <td rowspan="2">AT+COORD</td>    
    	 <td>AT+COORD? 查询当前设备类型<br>+COORD=<longtitude>,<latitude>,<altitude> 地理位置信息</td> 
    </tr>
    <tr>
        <td>AT+CLASS=<longtitude>,<latitude>,<altitude> 设置设备地理位置信息，海拔支持负数</td> 
    </tr>
</table>


举例

```
AT+COORD?
+COORD=104.06E,30.67N,500

AT+COORD=144.58E,37.50S,880
OK
```

---------------------

### 24. 速率自适应ADR

<table>
    <tr>
        <td rowspan="2">AT+ADR</td>    
    	 <td>AT+ADR? 查询当前设备ADR是否打开<br>+ADR=1 ADR打开<br>+ADR=0 ADR关闭</td> 
    </tr>
    <tr>
        <td>AT+ADR=1 打开ADR<br>AT+ADR=0 关闭ADR</td> 
    </tr>
</table>



举例

```
AT+ADR?
+ADR=1
AT+ADR=0
OK
AT+ADR?
+ADR=0
```

--------------------

### 25. 收发数据类型
当数据类型是ASCII时，发送XYZ
AT+SEND=XYZ
当数据类型是HEX时，发送XYZ
AT+SEND=58595A

接收数据同理，参考AT+RECV指令
<table>
    <tr>
        <td rowspan="2">AT+TEXTTYPE</td>    
    	 <td>AT+TEXTTYPE? 查询收发数据类型<br>+TEXTTYPE=HEX HEX方式发送数据<br>+TEXTTYPE=ASCII ASCII方式收发数据</td> 
    </tr>
    <tr>
        <td>AT+TEXTTYPE=<type> 设置收发数据类型，type可以是HEX ASCII</td> 
    </tr>
</table>



举例

```
AT+TEXTTYPE?
+TEXT=ASCII
AT+TEXTTYPE=HEX
OK
AT+TEXTTYPE?
+TEXTTYPE=HEX
```

--------------------

### 26. 接收数据（优先级2）

Lorawan接收的数据转发到串口
格式为+RECV:U(C):D(E):Port:RSSI:SNR:Data

当数据包没有数据段时，Port会被加1000
+RECV:U:D:2:-30:8:
+RECV:U:E:2:-30:2:crc_err
当数据包有数据段时
AT+TEXT=HEX    
+RECV:C:D:2:-30:2:61626364
AT+TEXT=ASCII     
+RECV:C:D:2:-30:2:hello
<table>
    <tr>
        <td rowspan="2">AT+RECV</td>    
    	 <td>AT+RECV? 查询当前设备ADR是否打开<br>+ADR=1 ADR打开<br>+ADR=0 ADR关闭</td> 
    </tr>
    <tr>
        <td>AT+RECV=1 lorawan接收数据打印到串口<br>AT+RECV=0 Lorawan接收到的数据不打印到串口</td> 
    </tr>
</table>



举例

```
#AT+TEXT=ASCII
AT+RECV=1
+RECV:C:D:2:-30:5:hello
#接收到CONFIRMED包，包含数据段，数据段为hello，端口为2，RSSI为-30，SNR为5

+RECV:U:D:2:-38:6:
#接收到UNCONFIRMED包，不包含数据段，端口为2，RSSI为-38，SNR为6


+RECV:U:E:2:-38:6:CRC_ERR
#接收到UNCONFIRMED包，端口为2，RSSI为-38，SNR为6，包出现CRC_ERR

#AT+TEXT=HEX
AT+RECV=1
+RECV:C:D:2:-30:5:58595A
#接收到CONFIRMED包，包含数据段，数据段为HEX编码的59595A（XYZ），端口为2，RSSI为-30，SNR为5

+RECV:U:D:2:-38:6:
#接收到UNCONFIRMED包，不包含数据段，端口为2，RSSI为-38，SNR为6


+RECV:U:E:2:-38:6:CRC_ERR
#接收到UNCONFIRMED包，端口为2，RSSI为-38，SNR为6，包出现CRC_ERR
```

## 硬件控制

--------------------

### 1. 对外供电

设备上有个12V电源，可以对外供电，方便用户部署需要较大电压的外设
<table>
    <tr>
        <td rowspan="2">AT+OUTPOWER1</td>    
    	 <td>AT+OUTPOWER1? 查询当前设备供电策略</td> 
    </tr>
    <tr>
        <td>AT+OURPOWER1=<12V>,<duration> <br>duration单位为ms，0表示用元供电，-1表示永远不供电</td> 
    </tr>
</table>



举例

```
#采集数据前，对外供电12V，供电3000ms，待设备初始化完成后，再采集数据
AT+OUTPOWER1=12V,3000
OK
AT+OUTPOWER1?
+OUTPOWER1=12V,3000

#12V供电电路一直对外供电
AT+OUTPOWER1=12V,0
OK

#12V供电电路从不对外供电
AT+OUTPOWER1=12V,-1
OK
```

--------------------

###  2. 入库与出库

用户刚刚拿到设备时，设备处于睡眠模式，保持最低功耗，需要用户手动唤醒。
用户使用手机或PC软件配置后，设备将自动被唤醒。

<table>
    <tr>
        <td rowspan="2">AT+POWERON</td>    
    	 <td>AT+POWERON? 查询当前设备是否处于入库状态<br>+POWERON=0 入库状态<br>+POWERON=1 出库状态</td> 
    </tr>
    <tr>
        <td>AT+POWERON=<0/1> <br>0 表示入库状态，处于低功耗，设备不工作<br>1 表示设备开始工作</td> 
    </tr>
</table>



举例

```
AT+POWERON=0
OK
#电池供电，测试功耗为uA级别
AT+POWERON=1
OK
#电池供电，设备正常工作

AT+POWERON？
+POWERON=1
```

--------------------

### 3. 设置串口波特率

串口默认波特率为115200 8N1
支持的波特率列表为

设置串口波特率后立即生效

<table>
    <tr>
        <td rowspan="2">AT+BAUD</td>    
    	 <td>AT+BAUD? 查询当前波特率<br>+BAUD=115200,8N1</td> 
    </tr>
    <tr>
        <td>AT+BAUD=9600,8N0 这是波特率为9600,8N0模式</td> 
    </tr>
</table>



举例

```
AT+BAUD?
+BAUD=115200,8N1

AT+BAUD=9600,8E1
OK
AT+BAUD?
+BAUD=9600,8E1
```

---------------------------

### 4. ADC采集

设备有2路ADC采集

<table>
    <tr>
        <td rowspan="2">AT+ADC<n></td>    
    	 <td>AT+ADC<n>=V 读取ADC<n>电压模式的值<br>+ADC<n>=<value> <br>AT+ADC<n>=I 读取ADC<n>电流模式的值<br>AT+ADC<n>=D 禁用ADC<n></td> 
    </tr>
    <tr>
        <td>AT+ADC<n>？ <br>D 表示未启用，A表示采集电流，V表示采集电压</td> 
    </tr>
</table>



举例

```
#采集ADC1通道，以电压模式采集，同时将ADC1通道配置到Lora上传数据包中
AT+ADC1=V
+ADC1=6351

AT+ADC1？
+ADC1=V


#采集ADC2通道，以电流模式采集，同时将ADC2通道配置到Lora上传数据包中
AT+ADC2=A
+ADC2=635


AT+ADC2？
+ADC2=A

#禁止采集ADC1通道，同时将ADC1通道从Lora上传数据包中屏蔽
AT+ADC1=D
OK


AT+ADC1？
+ADC1=D

#禁止采集ADC2通道，同时将ADC1通道从Lora上传数据包中屏蔽
#禁用ADC2采集
AT+ADC2=D
OK

AT+ADC2？
+ADC2=D
```

--------------------

### 5. IOOUT引脚输出策略

设备有2路IO，可以配置为IO输出，输出电平为3.3V
支持电平序列对，最多10对

IOIN IOOUT IOCNT是互斥的，设置了其中一种模式，另外两种直接不再生效

<table>
    <tr>
        <td rowspan="2">AT+IOOUT<n></td>    
    	 <td>AT+IOOUT<n>=<level_0>,<duration_0>,<level_1>,<duration1>,...<level_n>,<duration_n> 设置引脚输出策略，duration单位为ms，0表示永远<br>TOGLE 表示取反（优先级2）</td> 
    </tr>
    <tr>
        <td>AT+IOOUT<n>？ <br><level_0>,<duration_0>,<level_1>,<duration1>,...<level_n>,<duration_n><br>D 表示未启用</td> 
    </tr>
</table>



举例

```
#设置IO1为OUT模式，在每个Loop中，输出低电平200ms，高电平200ms，低电平500ms，高电平500ms

AT+IOOUT1?
+IOOUT1=D

AT+IOOUT1=0,200,1,200,0,500,1,500
OK

AT+IOOUT1?
+IOOUT1=0,200,1,200,0,500,1,500

AT+IOOUT2?
+IOOUT2=D

#设置IO2位OUT模式，在每个Loop中，输出高电平5000ms，后续持续输出低电平
AT+IOOUT2=1,5000,0,0
OK
AT+IOOUT2=1,5000,0,0
OK

#设置IO1为OUT模式，在每个Loop中，对IO1输出电平取反
AT+IOOUT1=TOGLE
OK
AT+IOOUT1?
+IOOUT1=TOGLE
```

-----------------------

### 6. IOIN引脚输入策略

设置为TOGLE，RISING，FAILING三种触发策略，当条件触发后，串口返回消息，同时将数据上传到lorawan（AT 端口）
设置为PULLDOWN，PULLUP两种静态策略，在每个LOOP中，上发引脚电平

IOIN IOOUT IOCNT是互斥的，设置了其中一种模式，另外两种直接不再生效

<table>
    <tr>
        <td rowspan="2">AT+IOIN<n></td>    
    	 <td>AT+IOIN<n>=<mode> mode可以为<br>TOGLE 双边沿跳变<br>RISING 上升沿跳变<br>FAILING 下降沿跳变<br>返回值  +IOIN<n>=<mode>,<value></td> 
    </tr>
    <tr>
        <td>AT+IOIN<n>? <br>+IOIN<n>=<mode><br>TOGLE,RISING,FAILING 三种工作模式，D 表示未启用</td> 
    </tr>
</table>



举例

```
#查询IOIN1模式，返回D，表示IOIN1未启用
AT+IOIN1?
+IOIN1=D

#设置IOIN1为上拉模式，返回+IOIN1=PULLUP,0，表示上拉模式，当前电平为0
AT+IOIN1=PULLUP
+IOIN1=PULLUP,0

#设置IOIN2为下拉模式，返回+IOIN1=PULLDOWN,1，表示下拉模式，当前电平为1
AT+IOIN2=PULLDOWN
+IOIN2=PULLDOWN,1

#设置IOIN1为下降沿触发，当被触发后，返回+IOIN1=FAILING,0 给串口和lorawan AT端口
AT+IOIN1=FAILING
OK

+IOIN1=FAILING,0
+IOIN1=FAILING,0
+IOIN1=FAILING,0

AT+IOIN1?
+IOIN1=FAILING

#设置IOIN2为上升沿触发，当被触发后，返回+IOIN2=RISING,1 给串口和lorawan AT端口
AT+IOIN2=RISING
OK

+IOIN2=RISING,1
+IOIN2=RISING,1
+IOIN2=RISING,1

AT+IOIN2?
+IOIN2=RISING

#设置IOIN2为双边沿沿触发，当被触发后，返回+IOIN2=TOGLE,1 给串口和lorawan AT端口
AT+IOIN2=TOGLE
OK

+IOIN2=TOGLE,1
+IOIN2=TOGLE,0
+IOIN2=TOGLE,1
+IOIN2=TOGLE,0


AT+IOIN2?
+IOIN2=TOGLE
```

-----------------------------

### 7. IOCNT引脚计数策略

设置为BOTH，RISING，FAILING三种触发策略，当条件触发后，串口返回消息，在大循环中将计数值上发到lorawan

IOIN IOOUT IOCNT是互斥的，设置了其中一种模式，另外两种直接不再生效

<table>
    <tr>
        <td rowspan="2">AT+IOCNT<n></td>    
    	 <td>AT+IOCNT<n>=<mode> mode可以为<br>BOTH 双边沿跳变<br>RISING 上升沿跳变<br>FAILING 下降沿跳变 D 禁用<br>返回值  +IOCNT<n>=<mode>,<value></td> 
    </tr>
    <tr>
        <td>AT+IOCNT<n>? <br>+IOCNT<n>=<mode><br>BOTH,RISING,FAILING 三种触发方式，D 表示未启用</td> 
    </tr>
</table>



举例

```
#查询IOCNT1模式，返回D，表示IOCNT1未启用
AT+IOCNT1?
+IOCNT1=D


#设置IOCNT1为下降沿触发，当被触发后，返回+IOIN1=FAILING,<cnt> 到串口
AT+IOIN1=FAILING
OK

+IOCNT1=FAILING,1
+IOCNT1=FAILING,2
+IOCNT1=FAILING,3

AT+IOCNT1?
+IOCNT1=FAILING

#设置IOCNT2为上升沿触发，当被触发后，返回+IOIN2=RISING,<cnt> 到串口
AT+IOCNT2=RISING
OK

+IOIN2=RISING,1
+IOIN2=RISING,2
+IOIN2=RISING,3

AT+IOCNT2?
+IOIN2=RISING

#设置IOIN2为双边沿沿触发，当被触发后，返回+IOIN2=BOTH,<cnt> 给串口
AT+IOCNT2=BOTH
OK

+IOCNT2=BOTH,1
+IOCNT2=BOTH,2
+IOCNT2=BOTH,3

AT+IOIN2?
+IOIN2=BOTH
```

---------------------

### 8. 数据采集通信大循环

设置为BOTH，RISING，FAILING三种触发策略，当条件触发后，串口返回消息，在大循环中将计数值上发到lorawan

IOIN IOOUT IOCNT是互斥的，设置了其中一种模式，另外两种直接不再生效

<table>
    <tr>
        <td rowspan="2">AT+LOOP</td>
    	 <td>AT+LOOP=<duration> duration单位为ms，不少于10000</td> 
    </tr>
    <tr>
        <td>AT+LOOP? <br>+LOOP=<duration>  duration单位为ms，不少于10000</td> 
    </tr>
</table>



举例

```
AT+LOOP?
+LOOP=15000

AT+LOOP=20000
OK

AT+LOOP?
+LOOP=20000
```

-------------------

### 9. 电池电量

电量范围为0-99%

<table>
    <tr>
        <td>AT+BATTERY</td>    
    	<td>AT+BATTERY? 查询电池电量<br>+BATTERY:99% 返回电池电量百分比</td> 
    </tr>
</table>


举例

```
AT+BATTERY?
+BATTERY=99%
```

---------------------

### 10. 升级
执行升级后，flash的前4字节擦除，然后mcu复位，电脑端将弹出BootLoader设备
PC软件将选择的固件通过BootLoader设备烧录到mcu的flash中，然后重启mcu

<table>
    <tr>
        <td>AT+UPGRADE</td>    
    	 <td>AT+UPGRADE 进入升级模式</td> 
    </tr>
</table>



举例

```
AT+UPGRADE
```

-----------------

### 11. 恢复出厂设置

<table>
    <tr>
        <td>AT+RECOVERY</td>    
    	<td>AT+RECOVERY 恢复出厂设置</td> 
    </tr>
</table>


举例

```
AT+RECOVERY
OK
```

--------------------

### 12. 重启

<table>
    <tr>
        <td>AT+REBOOT</td>    
    	<td>AT+REBOOT 系统重启</td> 
    </tr>
</table>


举例

```
AT+REBOOT
OK
```


-----------------------------------

## RS485

---------------------

### 1. 重试次数

设置为BOTH，RISING，FAILING三种触发策略，当条件触发后，串口返回消息，在大循环中将计数值上发到lorawan

IOIN IOOUT IOCNT是互斥的，设置了其中一种模式，另外两种直接不再生效

<table>
    <tr>
        <td rowspan="2">AT+RS485NBTRIALS</td>    
    	 <td>AT+RS485NBTRIALS=<duration> RS485命令的重试次数 范围0-5</td> 
    </tr>
    <tr>
        <td>AT+RS485NBTRIALS? <br>+RS485NBTRIALS=<n>  n范围0-5</td> 
    </tr>
</table>


举例

```
AT+RS485NBTRIALS?
+RS485NBTRIALS=2

AT+RS485NBTRIALS=3
OK

AT+RS485NBTRIALS?
+LOOP=3
```

------------------

### 3. 设置通信子项目

模块最多支持8个通信子项目，n的范围为0-7

<table>
    <tr>
        <td rowspan="2">AT+RS485ITEM&ltn&gt</td>    
    	 <td>AT+RS485ITEM&ltn&gt=&ltdata&gt,&ltdelay&gt,&ltstartreg&gt,&ltlength&gt,&ltbyteorder&gt n的范围为0-7  <br>data为16进制字符串<br>delay单位为ms,表示这条命令的最大等待回复时间<br>startreg，开始读取的寄存器地址<br>length，读取的数据长度<br>byteorder为字节序，目前支持AB，BA,ABCD字节序</td> 
    </tr>
    <tr>
        <td>AT+RS485ITEM&ltn&gt? <br>+RS485ITEM&ltn&gt=&ltdata&gt,&ltdelay&gt,&ltstartreg&gt,&ltlength&gt,&ltbyteorder&gt 已经配置 <br>+RS485ITEM&ltn&gt=NULL 没有配置</td> 
    </tr>
</table>




举例

```
AT+RS485ITEM<n>?
+RS485ITEM<n>=2

AT+RS485ITEM<n>=3
OK

AT+RS485ITEM<n>?
+LOOP=3
```



## 数据上传格式

* 数据在每个LOOP上传一次，比如LOOP设置为30000，那么每30秒上传一次数据

* 设备中有多路ADC，IO，RS485，我们采用掩码方式上传，掩码为1表示有数据，掩码为0表示无数据

* 如果mask为0，对应的数据段不上传

* 每次传输，电量是必须上传的

* 最小上传数据长度为 6 bytes

* 最大上传数据长度为 59 bytes

###  1. ADC段共5字节
| ADC mask（1 byte） | 数据小端字节序（2+2byte） |
| ------------------ | -------------------- |
| ADC（0） bit0      | 2 bytes              |
| ADC（1） bit1      | 2 bytes              |

### 2. IOCNT段共9字节
| ADC mask（1 byte） | 数据小端字节序（4+4byte）|
| ------------------ | -------------------- |
| ADC（0） bit0      | 2 bytes               |
| ADC（1） bit1      | 2 bytes               |

### 3. IOOUT段共2字节
| ADC mask（1 byte） | 数据小端字节序（1byte）   |
| ------------------ | --------------- |
| IOIN      | 1/2 bytes              |
| IOUT      | 1/2 bytes               |

### 4. R485（最多8条命令）
| channel mask（1 byte） | 配置 | 返回数据    |
| ------------------ | ------|---------------- |
| ch0 bit<n>  n范围0-7     |  bit6-7<br>bit3-5<br>bit2-0数据长度x     |x bytes                 |

### 5.电量
| BATTERY mask（1 byte） | 百分比（1 byte）   |
| ------------------ | --------------- |
| 1      | 0-100 （+0x80，如果最高位为0，表示正在充电）              |
