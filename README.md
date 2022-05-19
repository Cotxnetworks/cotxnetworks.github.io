# COTX APIs

## Introduction
The COTX iot cloud service API is a set of HTTP Request that allows you to programatically interact with iot cloud service . It's the lowest level building block and is ideal for integrating with back-end services, for example.

When you register the device through the COTX Device App, you can use your username and password to get a key, and then subscribe to the device data through MQTT to make your own application.

## Base URL
https://api.cotx-sg.io/

## Account

### Account MQTT connection key

```
POST https://api.cotx-sg.io/api/v1/secret
```

_Request Parameters_

| param             | Type     | Note                                     |
| ----------------- | -------- | ---------------------------------------- |
| username (must) | _string_ | Account of CoTX Device app |
| password (must) | _string_ | md5(password) |

_Sample request_
```
{
    "username": "test@cotxnetworks.com",
    "password": "E10ADC3949BA59ABBE56E057F20F883E"
}
```
_Responses_

200: OK

```json
{
  "secret": "0e6d0590-4557-4c2a-b0ba-b10c645fd9e6"
}
```


## Subscription data
Take the MQTT tool as an example
![image](https://user-images.githubusercontent.com/76096088/167827968-a4f11e10-3499-4c7c-a4ee-4e76423a63ce.png)


_Responses_

```json
{
 "sn": "SN9012PLPL06AF4C",
 "dev_eui": "1122334455667788",
 "epo_status": 0,      // EPOstatus  0-invalid/overdue 1-available
 "position_mark": 2,   // 定位标记 0-无定位 1-设备 2-手机 3-wifi
 "upload_tag": 0,      // 上传状态 0-实时 1-补传
 "is_charge": 0,       // 充电状态 0-未充电 1-充电
 "connect": 1,         // 连接方式 0:Lora 1:BLE 2:WiFi
 "longitude": 0,       // 经度 (double longitude * 1000000)
 "latitude": 0,        // 纬度 (double latitude * 1000000)
 "precious": 0,        // 定位精度  0~2047
 "star_num": 0,        // 定位卫星数  0~37
 "timestamp": 1652091432,// 定位时间 UTC时间戳
 "paws":11,              // 步数
 "walking": 0,           // 运动时间(min) 0~1440
 "power": 67,            // 电量 0~100 
 "working": 0,           // 运动时间(min) 0~1440
 "assist_mac":[          /// wifi辅助定位数据 4组mac 通过辅助定位可以拿到经纬度 https://developers.google.com/maps/documentation/geolocation/overview
     {
     "mac":"43:AE:82:F5:8A:FB",
     "rssi":-1
     },
      {
     "mac":"43:AE:82:F5:8A:FB",
     "rssi":-1
     },
      {
     "mac":"43:AE:82:F5:8A:FB",
     "rssi":-1
     },
      {
     "mac":"43:AE:82:F5:8A:FB",
     "rssi":-1
     }
 ]         
 
 "helium_report_interval":5,       // 设备上报数据间隔5~600 单位分钟
 "last _position_time": 1652091432 // 上一次定位时间 UTC时间戳
}
```

---
