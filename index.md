# COTX APIs

## Introduction
The COTX iot cloud service API is a set of HTTP Request that allows you to programatically interact with iot cloud service . It's the lowest level building block and is ideal for integrating with back-end services, for example.

When you register the device through the COTX Device App, you can use your username and password to get a key, and then subscribe to the device data through MQTT to make your own application.

## Base URL
https://api.cotx-sg.io/

## Account

### Account MQTT connection key

```
POST https://api.cotx-sg.io/api/v1/get_mqtt_key
Content-Type:application/json;
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
    "password": "92279f433cba733464fa816a40b2f031"
}
```
_Responses_

200: OK

```json
{
  "secret": "f0051e56-9c94-4d4d-8c22-e69cedcbcbdc"
}
```


## Subscription data
Take the MQTT tool as an example
Topic: `{{username}}/{{dev_eui}}/rx`

example: test@cotxnetworks.com/1122334455667788/rx


![image](https://user-images.githubusercontent.com/76096088/167827968-a4f11e10-3499-4c7c-a4ee-4e76423a63ce.png)


_join Responses_
```json
{
 "data_type":"join",            // Data type Only two cases: join/uplink
 "sn": "SN9012PLPL06AF4C",      // SN
 "dev_eui": "1122334455667788", // DevEui
 "rssi":-18,                    // RSSI
 "timestamp": 1652091432        // timestamp UTC
 }
```

_uplink Responses_
```json
{
 "data_type":"uplink",          // Data type Only two cases: join/uplink
 "sn": "SN9012PLPL06AF4C",      // SN
 "dev_eui": "1122334455667788", // DevEui
 "rssi":-18,                    // RSSI 
 "epo_status": 0,               // EPOstatus  0-invalid/overdue 1-available
 "position_mark": 2,            // position mark 0-no-location 1-device 2-phone 3-wifi
 "upload_tag": 0,               // upload status 0-realtime 1-complementary
 "is_charge": 0,                // charge status 0-not charged 1-charge
 "connect": 1,                  // connection method 0-Lora 1-BLE 2-WiFi
 "longitude": 0,                // longitude (double longitude * 1000000)
 "latitude": 0,                 // latitude (double latitude * 1000000)
 "precious": 0,                 // position accuracy 0~2047
 "star_num": 0,                 // number of satellites 0~37
 "timestamp": 1652091432,       // Positioning time UTC timestamp
 "paws":11,                     // number of steps
 "walking": 0,                  // movement time(min) 0~1440
 "power": 67,                   // power 0~100
 "working": 0,                  // movement time(min) 0~1440
 "assist_mac":[                 // wifi auxiliary positioning data, 4 groups of mac. through the auxiliary positioning can get latitude and longitude                                     //https://developers.google.com/maps/documentation/geolocation/overview
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
 "helium_report_interval":5,       // device report data interval 5~600 unit minutes
 "last_position_time": 1652091432  // last position time UTC timestamp
}
```

---
