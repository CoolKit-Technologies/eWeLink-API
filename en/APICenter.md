# API Center (Disuse)

## API Overview

API center gives access to user account management, registration,changing password,etc.

Device management includes adding device, grouping device, etc.

Device control allows to turn on/off devices, adjust color, color temperature,and brightness, share devices, create timers on devices, etc.

Please choose your own server region from cn, as, eu and us.
Users in mainland China are recommended to use:https://cn-api.coolkit.cn:8080 -> .cn domain
Other regions please use:https://{region}-api.coolkit.cc:8080 -> .cc domain

## Region server

### Check current server

Returns the region server in which the current account is registered now. Regions allow users to connect to nearest server and have a better experience over devices. Server is assigned during registration. Devices in the account will connect to the assigned server as well.

For example: User is in cn region, but account was created in eu region. Devices in this account will connect to eu server, causing slow response on device.

- URL: [https://api.coolkit.cc:8080/api/user/region](https://api.coolkit.cc:8080/api/user/region)
- Method: get

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Sign+SPACE+SIGNATURE | Yes | Sign Qbd+knKCUb8LAP6yMv1SSqYwmm1vDIxG3rHeq1Ul+ |
| Content-Type | application/json | Yes | application/json |


Params: 

| Name | Type | Required | Comment |
| :--- | --- | --- | --- |
| country_code | string | No | [country/region code](http://www.yadexp.com/yadexp/209/d.htm) |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
https://api.coolkit.cc:8080/api/user/region?country_code=86&appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&nonce=q3wz95p6&ts=1558004249&version=8
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | --- | --- | --- |
| error | number | Yes |  |
| region | string | Yes | Region server |
| requestid| string| No| ts+"-"+nonce |

**Example Response:**

```json
{
    "region":"cn",
    "error":0,
    "requestid": "q3wz95p6-1558004249"
}
```

## Account management

### Verification code

As a security verification method, verification code is sent to the email or phone number user input to register and reset password.

- URL: https://{region}-api.coolkit.cc:8080/api/sms
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Sign+SPACE+SIGNATURE | Yes | Sign Qbd+knKCUb8LAP6yMv1SSqYwmm1vDIxG3rHeq1Ul+is= |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| sendType | string | Yes | "0"register；"1"reset password；"3"delete account；"4"Wechat register and login |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |
| email | string | - | email account |
| to | string | - | mobile account, with country code. Format: +8615815725225 (+86 China) |

Example: 

```json
{
    "sendType":"0",
    "to":"+8613123456789",// or "email":"test@test.com"
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts": 1558004249,
    "version":8,
    "nonce":"asbsedwq"
}
```

Note: 

- Change region parameter to your own server. 4 servers available now,  respectively cn, as, eu, and us.
- Users in mainland China should use: [https://cn-api.coolkit.cn:8080](https://cn-api.coolkit.cn:8080) -> .cn as domain suffix
- Users in other regions should use: [https://cn-api.coolkit.cn:8080](https://cn-api.coolkit.cn:8080) -> .cc as domain suffix
- Please check [General instructions] for signature algorithm.
- You cannot pass both 'email' and 'to'. Please only pass email when receiving verification code by email. So does 'to' by mobile.

**Response parameters:**


| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |
| region | string | No | returned when account not in current region |
| msg | string | No | error cause |

Error code: 

0: Success  
301: user is in another server, app need to relocate server and reconnect   
400: Parameter error  
401: User does not exist   
409: account already registered  
500: Server error  
504: Failed to send  
160038: Sending too fast which exceeds frequency limit  

**Example Response:**

```json
{
    "error": 0
}
```

### Register account

You will be able to control and manage devices after registering an account.

- URL: https://{region}-api.coolkit.cc:8080/api/user/register
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Sign+SPACE+Signature | Yes | Sign 7z8pd9cGSxizuAm5kl4TmRcRzMuVQK/6Ye3DREUnM5E= |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| email | string | Y | registration email |
| phoneNumber | string | Y | registration mobile |
| verificationCode | string | Yes | verification code |
| password | string | Yes | registration password |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "verificationCode":"1234",
    "phoneNumber":"+861312345678",// or "email":"test@test.com"
    "password":"12345678",
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts": 1558004249,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| user | Array | No | user info |
| region| string  | No | registered region server |
| error | number | No | error will be returned in case of failure |
| rt | string | No | Refresh Token |
| at | string | No | Access Token |

User description: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| apikey | string | No | user apikey|
| phoneNumber| string  | No | user mobile|
| email | string | No | user email |
| createdAt | date | No | registration time |


Error code: 

401: Failed to get authorization token  
500: server error  
498: wrong verification code  
409: Account already registered  
Success: no error returned  

**Example Response:**

```json
{
    "at":"074e8af6f5f10183647a6a4f5b51fdc6788f617a",
    "rt":"24670a9e493ba18cf5d9750f14505705824fcfd9",
    "user":{
        "_id":"5c984cd3dc8295fa0ef3e592",
        "phoneNumber":"+8613123456789",
        "appId":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
        "lang":"cn",
        "online":false,
        "onlineTime":"2019-05-16T10:48:42.091Z",
        "ip":"110.110.110.110",
        "location":"广东",
        "offlineTime":"2019-05-16T10:51:22.090Z",
        "appInfos":[
            {
                "appVersion":"3.12.0",
                "os":"android"
            }
        ],
        "nickname":"eWeLink",
        "createdAt":"2019-03-25T03:36:51.335Z",
        "apikey":"95da0fea-5692-469a-c562-4dd5ee9a51f1"
    },
    "region":"cn"
}
```

### Account Login

You have to log in your account before you are able to manage and control devices.

- URL: https://{region}-api.coolkit.cc:8080/api/user/login
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Sign+SPACE+Signature | Yes | Sign Qbd+knKCUb8LAP6yMv1SSqYwmm1vDIxG3rHeq1Ul+ |
| Content-Type | application/json | Yes | application/json |


Body: 

| Name | Type | Required | Comment |
| :--- | --- | --- | --- |
| password | string | Yes | Login password |
| phoneNumber | string | NO | Login mobile(prior) |
| email | string | NO | Login email |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "phoneNumber":"+8613185260282",// or "email":"test@test.com"
    "password":"12345678",
    "ts": 1558004249,
    "version":8,
    "nonce":"asbsedwq"
}
```

Note: 

- Change region parameter to your own server. 4 servers available now, respetively cn, as, eu, and us.
- Users in mainland China should use: https://cn-api.coolkit.cn:8080 -> .cn as domain suffix
- Users in other regions should use: https://cn-api.coolkit.cn:8080 -> .cc as domain suffix
- Please check  for signature algorithm.

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | error will be returned in case of failure |
| at | string | No | Access Token |
| rt | string | No | Refresh Token |
| user | Array | No | user info |
| region | string | No | registered region server |

Error code: 

400: Missing parameter  
301: user in another server region, so app needs to relocate server and reconnect   
401: Wrong account or password  
402: Email inactivated  
404: User does not exist  
406: authentication failed（ wrong APPID or incomplete parameters）  
500: server error  

**Example Response:**

```json
{
    "at":"a527297584f1ca030579a90d2e800481e22e850a",
    "rt":"24670a9e493ba18cf5d9750f14505705824fcfd9",
    "user":{
        "_id":"5c984cd3dc8295fa0ef3e592",
        "phoneNumber":"+8613185260282",
        "appId":"1xMdjbmOBYctEJfye4EjFLR2M6YpYyyJ",
        "lang":"cn",
        "online":false,
        "onlineTime":"2019-05-16T10:48:42.091Z",
        "ip":"113.87.160.95",
        "location":"Guangdong",
        "offlineTime":"2019-05-16T10:51:22.090Z",
        "appInfos":[
            {
                "appVersion":"3.6.1",
                "os":"android"
            }
        ],
        "nickname":"coco",
        "yanKanYunInfo":{
            "username":"yk_+8613185260282",
            "uid":"a26c94ad607a4a47885dcacbcd66b50a",
            "app_id":"15241956565715",
            "accountType":0,
            "password":"12345678",
            "token":"f4d0e6f389f441f1aa61d815ac833b90"
        },
        "createdAt":"2019-03-25T03:36:51.335Z",
        "apikey":"95da0fea-6834-469a-b247-4dd5ee9a51f1"
    },
    "region":"cn"
}
```

Note: 

- [at] is the required parameter for other interfaces, to replace [Authorization]（Authorization: Bearer+SPACE+at）.
- [rt] is used to refresh [at].
- [region] is the server in which your account is created.

### Reset Password

When you forget your password, you can verify your registration account with verification code to reset it.

- URL: https://{region}-api.coolkit.cc:8080/api/user/password/reset
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Sign+SPACE+Signature | Yes | Sign 1zMaXhUQsSORdLo3mfA5igVSbrlkdDIStLtInz5Bjeg= |
| Content-Type | application/json | Yes | application/json |


Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| verificationCode | string | Yes | verification code |
| email | string | No | email account |
| phoneNumber | string | No | mobile account |
| password | string | Yes | new password |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "verificationCode": "1234",
    "phoneNumber":"+8613123456789",// or "email":"test@test.com"
    "password":"12345678",
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts": 1558004249,
    "version":8,
    "nonce":"q3wz95p6"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| user | Array | No | user info |
| region | string | No | registered region server |
| error | number | No | error will be returned in case of failure |
| rt | string | No | Refresh Token |
| at | string | No | Access Token |

Error code: 

0: Success  
400: Parameter error  
401: authentication failed  
403: lack permission  
498: wrong verification code  
500: server error  

**Example Response:**

```json
{
    "at":"354da69e2a30706f7c4c15e3eda0848d42c6a1bd",
    "rt":"f82cbbfb0330d99d367835a7fd0a19c65513c4b4",
    "user":{
        "_id":"5c984cd3dc8295fa0ef3e592",
        "phoneNumber":"+8613185260282",
        "appId":"1xMdjbmOBYctEJfye4EjFLR2M6YpYyyJ",
        "lang":"cn",
        "online":false,
        "onlineTime":"2019-05-16T10:48:42.091Z",
        "ip":"113.87.160.95",
        "location":"广东",
        "offlineTime":"2019-05-16T10:51:22.090Z",
        "appInfos":[
            {
                "appVersion":"3.6.1",
                "os":"android"
            }
        ],
        "nickname":"coco",
        "createdAt":"2019-03-25T03:36:51.335Z",
        "apikey":"95da0fea-6834-469a-b247-4dd5ee9a51f1"
    },
    "region":"cn"
}
```

### Change password

For security concerns, there is no need to verify user account when changing password through original password.

- URL: https://{region}-api.coolkit.cc:8080/api/user/password
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| oldPassword | string | Yes | Old password |
| newPassword | string | Yes | New password |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "oldPassword":"12345678",
    "newPassword":"123456789",
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | No | error will be returned in case of failure |
| message | string | No | message is returned when request is successful |

Legacy causes such a problem, and the new interface has now standardized return parameters.

Error code: 

**Example Response:**

```json
{
    "message": "Change password is success!"
}
```

### Token Refresh

Access Token expires every 30 days by default due to security reasons. while users do not need to login again to get access token, instead uses Refresh Token to refresh and get access token.

- URL: https://{region}-api.coolkit.cc:8080/api/user/refresh
- Method: get

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Sign+SPACE+Signature | Yes | Sign 3uvYDwdnrpMmToyGpJdm8z4qmkbgI4PWayoJd11t4I4= |
| Content-Type | application/json | Yes | application/json |

Params: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| rt | string | Yes | Refresh Token |
| grantType | string | Yes | fixed parameter: refresh |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
https://eu-api.coolkit.cc:8080/api/user/refresh?grantType=refresh&rt=24670a9e493ba18cf5d9750f14505705824fcfd9&appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&ts=1558004249&version=8&nonce=asbsedwq
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | string | No | 'error' will be returned in case of failure |
| at | string | No | Access Token |
| rt | string | No | Refresh Token |
| user | object | Yes | user info |
| region | string | Yes | registered region server |

Error code: 

400: Missing paramter  
401: Failed to get [at]  
402: [rt] expired  

**Example Response:**

```json
{
    "at":"174e8af6f5f10183647a6a4f5b51fdc6788f6172",
    "rt":"24670a9e493ba18cf5d9750f14505705824fcfd9",
    "user":{
        "_id":"5c984cd3dc8295fa0ef3e592",
        "phoneNumber":"+8613123456789",
        "appId":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
        "lang":"cn",
        "online":false,
        "onlineTime":"2019-05-16T10:48:42.091Z",
        "ip":"110.110.110.110",
        "location":"广东",
        "offlineTime":"2019-05-16T10:51:22.090Z",
        "appInfos":[
            {
                "appVersion":"3.12.0",
                "os":"android"
            }
        ],
        "nickname":"eWeLink",
        "createdAt":"2019-03-25T03:36:51.335Z",
        "apikey":"95da0fea-5692-469a-c562-4dd5ee9a51f1"
    },
    "region":"cn"
}
```
## Manage device

### Device List

Return all the devices added to this account, including devices shared by others.

- URL: https://{region}-api.coolkit.cc:8080/api/user/device
- Method: get

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Params: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| lang | string | No | the languages of response, cn means Chinese en English |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |
| getTags | number | No | 0: Do not return the content of the tags; 1: Return the content of the tags; the default is 0 |

Example: 

```json
https://eu-api.coolkit.cc:8080/api/user/device?lang=cn&appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&ts=1558004249&version=8&nonce=asbsedwq
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | No | Error code, error: 0 Success |
| devicelist | [object] | Yes | return device list when request is successful |

Note: If an empty list is returned, then there is no device in this account or the device hasn't been associated with your APPID. In the case of lack association, you need to contact your salesperson to get help.

Device info list: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| name | N | string | Device name |
| type | N | string | Type |
| deviceid | N | string | device ID |
| apikey | N | string | user apikey |
| extra | N | object | Reference to associated tables |
| onlineTime | N | string | Last time when device was online |
| ip | N | string | ip address of device |
| location | N | string | location where device was offline |
| settings | N | object | Device settings |
| groups | N | list | Group ID for groups device belongs to.One device can belong to multiple group.If device not in group,returns empty array[] |
| params | N | object | Device parameters |
| online | N | boolean | Device online or not |
| createdAt | N | date | time when device was added |
| sharedTo | Y | object | list of users to whom the device has been shared |
| devicekey | N | string |Device apikey |
| deviceUrl | Y | string | Url of device detail page |
| brandName | N | string | Brand |
| productModel | N | string | Product model |
| showBrand | N | boolean | Display brand and product model or not |
| uiid | N | number | id of device ui |

Example response: 

```json
[
    {
        "_id": "***************",
        "name": "My device 213ac8",
        "type": "10",
        "deviceid": "1000213ac8",
        "apikey": "3541f7af-*ec5-4502-9bf3-eb4b09e9e12*",
        "extra": {
            "_id": "***************",
            "extra": {
                "model": "PSA-B11-GL",
                "ui": "Single Channel Switch",
                "description": "WWJG001111",
                "manufacturer": "深圳创易智能系统有限公司",
                "mac": "**:**:**:**:**:**",
                "apmac": "**:**:**:**:**:**",
                "modelInfo": "***************",
                "brandId": "***************",
                "uiid": 6,
                "staMac": "**:**:**:**:**:**",
                "chipid": "********"
            }
        },
        "__v": 0,
        "onlineTime": "2019-10-15T07:22:14.361Z",
        "ip": "110.110.110.110",
        "location": "Guangdong",
        "settings": {
            "opsNotify": 0,
            "opsHistory": 1,
            "alarmNotify": 1,
            "wxAlarmNotify": 0,
            "wxOpsNotify": 0,
            "wxDoorbellNotify": 0,
            "appDoorbellNotify": 1
        },
        "devGroups": [],
        "groups": [],
        "params": {
            "pulseWidth": 500,
            "pulse": "off",
            "init": 1,
            "startup": "off",
            "staMac": "**:**:**:**:**:**",
            "rssi": -50,
            "fwVersion": "3.0.1",
            "switch": "off",
            "sledOnline": "on",
            "version": 8
        },
        "online": true,
        "createdAt": "2019-10-15T07:22:11.700Z",
        "group": "",
        "sharedTo": [],
        "devicekey": "***************",
        "deviceUrl": "",
        "brandName": "Maker",
        "showBrand": true,
        "brandLogoUrl": "",
        "productModel": "Sonoff basic R2",
        "devConfig": {},
        "uiid": 6
    }
]
```


### Check a device info

Get data of a device by DeviceId

- URL: https://{region}-api.coolkit.cc:8080/api/user/device/{DeviceID}
- Method: get

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Params: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| deviceid | string | Yes | device ID |
| apikey | string | Yes | user apikey(obtainable from login page) |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
https://eu-api.coolkit.cc:8080/api/user/device/1000000001?deviceid=&1000000001&appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&ts=1558004249&version=8&nonce=asbsedwq&apikey=95da0fea-6834-469a-b247-4dd5ee9a51f1
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | No | Error code |
| device | Array | No | device info which is returned when request is successful |

Error code: 

0: Success  
400: Parameter error  
401: Failed to get [at]  

**Example Response:**

```json
{
   "name": "My device 00001",
   "deviceid": "100000001"
   ...
}
```

### Add WiFi Device

All the parameters of this interface are being obtained when pairing a device. In the process of pairing a device, device will be added to user account and device info will be returned when it is added successfully.

- URL: https://{region}-api.coolkit.cc:8080/api/user/device/add
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| deviceid | string | Yes | device ID |
| apikey | string | Yes | device APIKEY |
| name | string | Yes | Device name |
| isSub | number | Yes | Child device or not（0 no；1 yes） |
| subDeviceId | string | - | device id of child device, which coexists with 'isSub' |
| chipid | string | No | chipset ID |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "deviceid":"100000001",
    "apikey":"xxxx-xxxx-xxx",
    "name":"Mydevice0001",
    "chipid": "zaqozs",
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| code| number  | Y | Error code |
| error | number | Y | wrong info |
| device | object | Y | device info which is returned when request is successful |

Error code: 

**Example Response:**

```json
{
   "name": "My device 00001",
   "deviceid":"100000001"
   ...
}
```

### Add GSM device

Parameters of [Add GSM device] comes from the QR code on the sticker of the device which contains device ID.

- URL: https://{region}-api.coolkit.cc:8080/api/user/device/addGsm
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| id | string | Yes | device gsmId, algorithm: MD5(deviceid + apikey) Do not include [+] |
| name | string | Yes | Device name |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "id":"xxxxxxxxxxxxxxxxxxxx",
    "name":"My device 0001",
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| code | number | Y | Error code which is returned in case of failure |
| error | number | Y | 'error' is returned in case of failure |
| device | object | Y | device info which is returned when request is successful |

**Example Response:**

```json
{
   "name": "My device 00001",
   "deviceid":"100000001"
   ...
}
```

**Examples of errors:**

```json
{
    "code":404,
    "error":"fd data is null"
}
```

### Delete regular device

Delete eWeLink devices in this account

- URL: https://{region}-api.coolkit.cc:8080/api/user/device/{deviceID}
- Method: delete

**Request Parameters:**

Headers: 

| name | parameter | required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Params: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| deviceid | string | Yes | device ID |
| apikey | string | Yes | device APIKEY |
| isSub | number | Yes | Child device or not（0 no；1 yes） |
| subDeviceId | string | - | child device ID, which coexists with [isSub] |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |


Example: 

```json
https://eu-api.coolkit.cc:8080/api/user/device/1000000001?deviceid=&1000000001&appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&ts=1558004249&version=8&nonce=asbsedwq
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| device | object | Array | device info, which is returned when request is successful |

**Example Response:**

```json
{
   "name": "My device 00001",
   "deviceid":"100000001"
   ...
}
```
### Change Device Name

Change the name of single channel device.

- URL: https://{region}-api.coolkit.cc:8080/api/user/device/{deviceID}
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |


Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| deviceid | string | Yes | device ID |
| apikey | string | Yes | device APIKEY |
| name | string | Yes | Device name |
| group | string | Yes | null character by default |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "deviceid":"100000001",
    "apikey":"xxxx-xxxx-xxx",
    "name":"My device 0002",
    "group": "",
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |
| device | Array | No | device info, which is returned when request is successful |

Error code: 

0: success

**Example Response:**

```json
{
   "error": 0,
   "deviceid":"1000000001"
}
```

### Change Child Device Name

Change the name of the channel of multi-channel device.

- URL: https://{region}-api.coolkit.cc:8080/api/user/tags
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |


Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| deviceid | string | Yes | device ID |
| apikey | string | Yes | Device APIKEY |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |
| key | string | Yes | fixed parameter: ck_channel_name |
| value | Array | Yes | Array in the format of {k:v} |

Example: 

```json
{
    "deviceid":"100000001",
    "apikey":"xxxx-xxxx-xxx",
    "key":"ck_channel_name",
      "value":{
        "0": "CH1", 
        "1": "CH2", 
        "2": "CH3", 
        "3": "CH4"
    },
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | N | Error code |

Error code: 

0: Success  
400: Parameter error  
401: authentication failed  
500: server error  

**Example Response:**

```json
{
   "error": 0
}
```
### Add Device Group
Add a group and order the group.

- URL: https://{region}-api.coolkit.cc:8080/api/group
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| index | number | Yes | index of the group |
| name | string | Yes | Group name |
| groupType | number | Yes | fixed parameter: 0 |
| apikey | string | Yes | user apikey (obtainable from login page) |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |


Example: 

```json
{
    "index":0,
    "apikey":"xxxx-xxxx-xxx",
    "name":"My group-1L",
    "groupType": 0,
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |
| groupid | string | No| group ID when created successfully |


Error code: 

0: Success  
400: Parameter error  
401: authentication failed  
500: server error  

**Example Response:**

```json
{
   "error": 0,
   "groupid":"123456789123"
}
```

### Change Group
Change group order and group name.

- URL: https://{region}-api.coolkit.cc:8080/api/group
- Method: put

**Request Parameters:**

Headers: 

| Name | Value | Required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| id | string | Yes | groupid |
| index | number | Yes | group index |
| name | string | Yes | group name |
| groupType | number | Yes | fixed parameter: 0 |
| apikey | string | Yes | user apikey (obtainable from login page) |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "id":"123456789123",
    "index":2,
    "apikey":"xxxx-xxxx-xxx",
    "name":"My group-2L",
    "groupType": 0,
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |

**Example Response:**

```json
{
   "error": 0
}
```
### Delete Group
Devices in deleted group will become ungrouped.

- URL: https://{region}-api.coolkit.cc:8080/api/group
- Method: delete

**Request Parameters:**

Headers: 

| Name | Value | Required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |


Params: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| id | string | Yes | groupid |
| type | number | Yes | fixed parameter: 0 |
| apikey | string | Yes | user apikey (obtainable from login page) |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |


Example: 

```json
https://eu-api.coolkit.cc:8080/api/group?id=123456789123&type=0&apikey=xxxx-xxxx-xxx&appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&ts=15452192511&version=8&nonce=asbsedwq
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |


**Example Response:**

```json
{
   "error": 0
}
```
### Add device to Group

Add device to a group. One device can be in multiple groups. If target group id is empty, device will be removed from current group.

- URL: https://{region}-api.coolkit.cc:8080/api/group/addDevice
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| deviceinfos | Array | Yes | device array: [device] |
| groupType | number | Yes | fixed parameter: 0 |
| apikey | string | Yes | user apikey (obtainable from login page) |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |


device description: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| source_id | string | Yes | source group id which can be empty. |
| target_id | string | Yes | target group id which can be empty. |
| deviceid | string | Yes | device ID |
| type | string | Yes | fixed parameter: 1 |


Example: 

```json
{
    "deviceinfos":{
        "source_id":"10001",
        "target_id":"10002",
        "deviceid":"10000000001",
        "type":1
    },
    "groupType":0,
    "apikey":"xxxx-xxxx-xxx",
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |

**Example Response:**

```json
{
   "error": 0
}
```

### Get Group List

Get the info of all groups in this account, the time when the groups were created, and the indexes of the groups(the info of all the groups that one device is in is provided by [Device List]).

- URL: https://{region}-api.coolkit.cc:8080/api/group
- Method: get

**Request Parameters:**

Headers: 

| Name | Value | Required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |


Params: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| groupType | number | Yes | fixed parameter: 0 |
| apikey | string | Yes | user apikey (obtainable from login page) |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
https://eu-api.coolkit.cc:8080/api/group?groupType=0&apikey=xxxx-xxxx-xxx&appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&ts=15452192511&version=8&nonce=asbsedwq
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |
| groupinfos | Array | Yes | group list: [{k:v},{k:v}] |

groupinfos description: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| id | string | Yes | group ID |
| name | string | Yes | group name |
| index | number | Yes | group index |
| createdAt | date | Yes | time when the group was created |

Error code: 

0: Success  
400: Parameter error  
401: authentication failed  
500: server error  

**Example Response:**

```json
{
    "groupinfos":[
        {
            "id": "12345678",
            "name": "group one"
        }
    "error":0
}
```

## Device Control

### HTTP : Server Dispatch

Please refer to: [Developer Guide->Step 3: Request Dispatchservice]
Persistent connection can only be built after address and port are obtained.

- URL: https://{region}-api.coolkit.cc:8080/dispatch/app
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |


Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| accept | string | Yes | fixed parameter: ws |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "accept":"ws",
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| IP | string | Yes | server IP for persistent connection |
| port | number | Yes | server port for persistent connection |
| domain | string | Yes | domain name for persistent connection. Currently, only app client returns domain name. IP should be used by android client to reduce issues caused by dns resolution. As js client could not skip certificate check, only domain can be used. |
| error | string | Yes | return 'error:0' when successful |
| reason | string | Yes | return 'ok' when successful |


Error code: 

0: Success  
400: Client Parameter error  
401: authentication failed（ prompts to login）  
402: [at] expired（ APP refreshes [access token] automatically）  
403: no permission（ APP prompts no permission, for instance, app has no permission to access OTA interface）（401-403 authentication error sent by internal authorization system）  
500: server error  

**Example Response:**

```json
{
    "port": 8080,
    "IP": "52.80.9.35",
    "reason": "ok",
    "domain": "cn-pconnect3.coolkit.cc",
    "error": 0
}
```

### WebSocket: Handshake

This is the authentication process when connection is being built. Handshake happens on both app client and device. This is the handshake of app.

**Note:**

When creating wss connection, client will verify the consistency of domain in certificate.Therefore, creating connection with ip by default will fail.

Consequently, we suggest skipping verification for certificate domain (which works for both android and java). When impossible to skip certificate verification, the last resort would be to create wss connection with domain name.

- URL: wss://IP:Port/api/ws 

Parameters are as follows:

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| action | string | Yes | fixed parameter: userOnline |
| at | string | Yes | AT obtainbed from login interface |
| apikey | string | Yes | user apikey (obtainable from login page) |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| userAgent | string | Yes | fixed parameter: app |
| sequence | string | Yes | 13-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
   "action":"userOnline",
   "version":8,
   "ts":1571141259,
   "at":"AT obtainbed from login interface",
   "userAgent":"app",
   "apikey":"APIKEY obtained from login interface",
   "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
   "nonce":"2plz69ax",
   "sequence": "1571141530100"
}
// Remove SPACE before compressing, 不要带多余的逗号
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | Yes | number | Error code |
| apikey | Yes | string | user apikey |
| config | No | string | configuration info |
| sequence | Yes | string | 13-digit standard timestamp |

Configdescription: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| hbl | number | No | turn on heartbeat or not.  0: no  1: yes |
| hbInterval | number | No | heartbeat interval in seconds.Client needs to add 7 to this value and send the result as interval to keep alive ping heartbeat.By default, the interval is 90 seconds. |

Error code: 

0: success

**Example Response:**

```json
{
  "error": 0,
  "apikey":"User APIKEY",
  "config":{
    "hbl":1,
    "hbInterval": 145
  },
  "sequence": "13-digit standard timestamp，Example: 1571141530100" // 和发送的一样
}
```


### WebSocket: Device online/offline

When server detects device going online or offline, app will be notified of the update.Such notification is sent by server automatically. No need to request from app.

Parameters: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| action | string | Yes | fixed parameter: sysmsg |
| apikey | string | Yes | user apikey (obtainable from login page) |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | fixed parameter: 0 |
| deviceid | string | Yes | device ID |
| params | object | Yes | Parameters: {k:v} |

Example: 

```json
{
    "action":"sysmsg",
    "deviceid":"1000000001",
    "apikey":"User APIKEY",
    "ts": 0,
    "params":{
        "online":false
    }
}
```

### WebSocket: Update Device Status

**After the device status change is reported to the "update" command, as long as the client has established a long connection, it can receive the information. Therefore, it is recommended that the client maintain a long connection to monitor the device status or send a query command to obtain a single device status information, rather than a regular request The HTTP interface obtains the device status and avoids placing a heavy burden on the server.**

Update statuses of devices, such as timers, sharing status, and on/off etc.

Parameters: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| action | string | Yes | fixed parameter: update |
| apikey | string | Yes | user apikey (obtainable from login page) |
| deviceid | string | Yes | device ID |
| params | object | Yes | The statuses of device to change, either object or object array. Server sends sends this parameter by transparent transmission. |
| userAgent | string | Yes| client: app|
| sequence | string | Yes| 13-digit standard timestamp |
| ts | number | Yes | fixed parameter: 0|

Example: 

```json
{
    "action":"update",
    "deviceid":"10000001",
    "apikey":"User Apikey",
    "userAgent":"app",
    "sequence": "1585297259553",
    "ts": 0,
    "params":{
        "switch": "on" // 1 channel device
    }
}
```

Params description: 

This parameter comes from protocol documentation. Protocols differ from the types of devices. For example, 1 channel switch must have only one switch. While multiple channel devices will have more than one switch. Light bulbs support tuning colors and dimming. 
Contact your salesperson to get related protocol documentation. For those who use plug and play app without UI, extra fee for customization will apply. Reach your salesperson to know more about it.

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |
| apikey | string | No | User APIKEY |
| deviceid | string | No | device ID |
| sequence | string | Yes| 13-digit standard timestamp |

Example: 

```json
{
    "error": 0,
    "deviceid": "1000000001",
    "apikey": "***************",
    "sequence": "1585297259553"
}
```

Error code:

0: success  
504: Device does not respond (offline or command error)  

### WebSocket: Inquire device status

Check device statuses, such as timers, share status, on/off etc.

Parameters: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| action | string | Yes | fixed parameter: query |
| apikey | string | Yes | user apikey (obtainable from login page) |
| deviceid | string | Yes | device ID |
| params | array | Yes | String array specifying parameters to check. By default, check all parameters. |
| userAgent | string | Yes |client: app |
| sequence | string | Yes| 13-digit standard timestamp |
| ts | number | Yes | fixed parameter: 0|

Example: 

```json
{
    "action":"query",
    "deviceid":"1000000001",
    "apikey":"User APIKEY",
    "sequence": "1585296084000",
    "params":["switch","timers"], // If the return is empty, you can use [] to query the status of all fields
    "ts": 0,
    "userAgent": "app"
}
```

paramsdescription: 

This parameter comes from protocol documentation. Protocols differ from the types of devices. For example, 1 channel switch must have only one switch. While multiple channel devices will have more than one switch. Light bulbs support tuning colors and dimming. 
Contact your salesperson to get related protocol documentation. For those who use plug and play app without UI, extra fee for customization will apply. Reach your salesperson to know more about it.

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |
| apikey | string | No | User APIKEY |
| deviceid | string | No | device ID |
| params | Array | Yes| parameters by transparent transmission |

Example: 

```json
{
    "error":0,
    "deviceid":"1000000001",
    "apikey":"***************",
    "params":{
        "switch":"on",
        ...
    }
}
```

### WebSocket: Share device

Client sends this command to server to share a device to another user in the same server.

description: 

1. Device having been shared cannot be shared again. 
2. Receiver must be online when device is being shared. Sharing will time out when receiver fails to confirm in time. Sharing cannot be done again until 3 minutes later. 
3. There is no time limit to the duration after sharing is completed. 
4. When sharing is successful, receiver will be able to control devices, while receiver cannot share the device, change device name or use other owner-exclusive features.

Parameters: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| action | string | Yes | fixed parameter: share |
| apikey | string | Yes | user apikey (obtainable from login page) |
| selfApikey | string | Yes | user apikey: Same as apikey|
| deviceid | string | Yes | device ID |
| params | Array | Yes | share parameters |
| userAgent | string | Yes | fixed parameter: app |
| sequence | string | Yes | 13-digit standard timestamp |

Params description: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| uid | string | Yes | receiver's account(email or mobile) |
| deviceName | string | Yes | device name by owner |
| userName | string | Yes | user name of owner |
| permit | number | No | um of permission values, calculated by offset. |
| shareTime | string | No | GMT standard time, in milliseconds, used to order sharing in app |
| note | string | Yes | Note by owner, 10 Chinese characters at most |
| sender_appid | string | Yes | sender appid |

**permit Calculation Rules: 1:add new timers; 2:edit timers; 4:delete timers; 8:enable timers；The sum of all four permissions is 15.**

Example: 

```json
{
    "action":"share",
    "apikey":"User APIKEY",
    "selfApikey": "User APIKEY",
    "deviceid": "1000000001",
    "sequence": "1585296084000",
    "userAgent": "app",
    "params":{
        "uid":"+86127123456789",
        "deviceName":"My device 00001",
        "userName":"Friend",
        "permit":15,
        "note":"Test sharing.",
        "shareTime": "1584231085395",
        "sender_appid": "McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr"
    }
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| result | number | No | 1: user not found；2: user accepted；3: user refused；4: sharing completed |
| error | number | Yes | Error code |
| apikey | string | No | Sharer user apikey, return what you receive |
| deviceid | string | No | device ID |
| sequence | string | No | 13-digit standard timestamp, return what you receive |

**Example Response:**

```json
{
  "error": 0,
  "result": 2,
  "apikey": "Sharer user apikey", // return what you receive
  "deviceid": "1000000001", // return what you receive
  "sequence": "1585296084000" // return what you receive
}
```

### WebSocket: Edit Sharing

App sends this command to the server to update timer permissions given to the receiver.

Parameters: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| action | string | Yes | fixed parameter: updateShare |
| apikey | string | Yes | user apikey (obtainable from login page) |
| deviceid | string | Yes | device ID |
| params | Array | Yes | share parameters |
| userAgent | string | Yes | fixed parameter: app |
| sequence | string | Yes | 13-digit standard timestamp |

paramsdescription: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| uid | string | Yes | receiver account(email or mobile) |
| deviceName | string | Yes | device name by owner |
| userName | string | Yes | user name of owner |
| permit | number | No | sum of permission values, calculated by offset. |
| shareTime | number | No | GMT standard time, in milliseconds, used to order sharing in app |
| note | string | Yes | Note by owner, 10 Chinese characters at most |

**permit Calculation Rules: 1:add new timers; 2:edit timers; 4:delete timers; 8:enable timers；The sum of all four permissions is 15.**

Example: 

```json
{
    "action": "updateShare",
    "apikey": "User APIKEY",
    "deviceid": "1000000001",
    "sequence": "1585296084000",
    "nonce": "asdasvz1",
    "userAgent": "app",
    "params":{
        "uid": "+86127123456789",
        "deviceName": "My device 00001",
        "userName": "Friend",
        "permit": 11,
        "note": "Testing share edit. "
    }
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| result | number | No | 1: user not found；2: user accepted；3: user refused；4: sharing completed |
| error | string | Yes | Error code |
| apikey | string | No | User APIKEY |
| deviceid | string | No | device ID|
| sequence | string | No | 13-digit standard timestamp, returned by server as is |

Error code: 

0: Success  
400: Bad Request（Parameter error）  
401: Unauthorized.  
403: Forbidden（no permission）  
406: User has logined another device.  
500: Internal Server Error   
504: Sharing timed out. (Neither accepted nor refused)  

**Example Response:**

```json
{
  "error": 0,
  "result": 2,
  "apikey":"User APIKEY",
  "deviceid": "1000000001",
  "sequence": "1585296084000"
}
```

### WebSocket: Cancel sharing

Client sends a command to server to cancel sharing a device. When owner cancels sharing a device, device will be deleted from receiver's device list, thus revoking the permission to control the device.

description: If share has been canceled when owner does it again, response parameters will be the same.

Parameters: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| action | string | Yes | fixed parameter: cancelShare |
| apikey | string | Yes | user apikey(obtainable from login page) |
| deviceid | string | Yes | device ID |
| params | Array | Yes | share parameters |
| userAgent | string | Yes | fixed parameter: app |
| sequence | string | Yes | 13-digit standard timestamp |

paramsdescription: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| uid | string | Yes | receiver's account(email or mobile) |
| deviceName | string | Yes | device name of owner |

Example: 

```json
{
    "action":"cancelShare",
    "apikey":"User APIKEY",
    "deviceid":"1000000001",
    "sequence": "1585296084000",
    "userAgent":"app",
    "params":{
        "uid":"+86127123456789",
        "deviceName":"My device 00001",
    }
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | string | Yes | Error code |
| sequence | string | No | 13-digit standard timestamp, returned by server as is |

Error code: 

0: Success

**Example Response:**

```json
{
  "error": 0,
  "result": 2,
  "apikey":"User APIKEY",
  "deviceid": "1000000001",
  "sequence": "1585296084000"
}
```

### HTTP: Check device status

Check device statuses, such as timers, share status, on/off etc.

- URL: https://{region}-api.coolkit.cc:8080/api/user/device/status
- Method: get

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Params: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| deviceid | string | Yes | device ID to check |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |
| params | string | No | parameter list, specifying parameters to check, separated by |

Example: 

```json
https://eu-api.coolkit.cc:8080/api/user/device/status?deviceid=1234abcd&params=switch|timers&appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&ts=1558004249&version=8&nonce=asbsedwq
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | No | Error code |
| errmsg | string | - | returned in case of error |
| params | Array | No | device statuse |

Error code: 

0: Success  
400: Parameter error

**Example Response:**

```json
{
    "error":0,
    "params":{
        "switch":"on"
    }
}
```

### HTTP: Update device status

Update device statuses, such as timers, share status, on/off etc.

- URL: https://{region}-api.coolkit.cc:8080/api/user/device/status
- Method: post

**Request Parameters:**

Headers: 

| Name | Value | Required | Example |
| :--- | :--- | :--- | :--- |
| Authorization | Bearer+SPACE+at | Yes | Bearer 074e8af6f5f10183647a6a4f5b51fdc6788f617a |
| Content-Type | application/json | Yes | application/json |

Body: 

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| deviceid | string | Yes | device ID |
| params | object | Yes | The statuses of device to change, either object or object array. Server sends sends this parameter by transparent transmission. |
| appid | string | Yes | APPID |
| nonce | string | Yes | 8-digit random alphanumeric characters |
| ts | number | Yes | 10-digit standard timestamp |
| version | number | Yes | Numbererface version: 8 |

Example: 

```json
{
    "deviceid":"100000001",
    "params": {
        "switch": "on"
    },
    "appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":1585296084,
    "version":8,
    "nonce":"asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| error | number | Yes | Error code |
| deviceid | string | Yes | device ID |

Error code: 

0: Success  
400: Parameter error  
504: Device does not respond (offline or command error)  

**Example Response:**

```json
{
   "error": 0,
   "deviceid":"1000000001"
}
```