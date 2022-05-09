# COTX APIs

## Introduction


## Accounts

---

## Account MQTT connection key

```
POST https://api.cotx-sg.io/v1/accounts
```

_Request Parameters_

| param             | Type     | Note                                     |
| ----------------- | -------- | ---------------------------------------- |
| username (must) | _string_ | Account of CoTX Device app |
| password (must) | _string_ | md5(password) |

_Sample request_
```
{
    "username": test@cotxnetworks.com,
    "password": "E10ADC3949BA59ABBE56E057F20F883E"
}
```
_Responses_

200: OK

```json
{
  "mqtt": "0e6d0590-4557-4c2a-b0ba-b10c645fd9e6"
}
```


## Subscription data

_Responses_

```json
{
 "sn": "SN9012PLPL06AF4C",
 "dev_eui": "1122334455667788",
 "epo_status": 0,
 "position_mark": 2,
 "upload_tag": 0,
 "is_charge": 0,
 "connect": 1,
 "longitude": 0,
 "latitude": 0,
 "precious": 0,
 "star_num": 0,
 "timestamp": 1652091432,
 "walking": 0,
 "power": 67,
 "working": 0,
 "mac": "4caf06faee02",
 "msg_id": 19,
 "msg_type": 177,
 "relay_rssi": 0,
 "relay_expect": 0,
 "relsy_actual": 0,
 "time_zone": 0,
 "last _position_time": 1652091432
}
```

---
