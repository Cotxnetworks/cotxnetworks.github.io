# COTX APIs

## Introduction


## Accounts

---

## Account MQTT connection key

```
POST https://api.helium.io/v1/accounts
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



---
