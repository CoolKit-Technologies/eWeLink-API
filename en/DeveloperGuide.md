# Developer Guide (v1)

**It is only for reference by developers of the original v1 version of the interface. It is no longer maintained and will be removed in January 2022.**

## Prepare Your Development Environment

Download necessary test tools and get needed device for test. To get started, you are required to do both otherwise you won't be able to access device data or control devices.

### Download eWeLink APP for test

[Google Play](https://play.google.com/store/apps/details?id=com.coolkit)

[Apple App Store](https://itunes.apple.com/cn/app/yi-wei-lian/id1035163158?mt=8)

You can also search 'eWeLink' on Google Play or other APP stores to download it.

### Buy a test device

Purchase Link: [Buy on Amazon](https://www.amazon.cn/s?k=sonoff)

### Register a test account

Downoad eWeLink app and register an account in the app.

### Log in your account

Log in with the account you just created and add a test device.

### Add Device

Open eWeLink app and follow user manual to enter pairing mode and add the device you bought.

![addDevice](./img/addDevice.png)

### Control Device

As soon as the device is online, try to control the device in app.

## Become a developer

Only through APPID assigned by eWeLink will you have access to API and get professional support from eWeLink to speed up your development. 

### APPID

Once commercial agreement is reached and payment is settled, you will receive an APPID sent by your salesperson.

### Technical Support

Your salesperson will create a WeChat group for communication with tech support.

## Create your first application

This part explains in details on Login, Accessing device data, Building persistent connection and many other topics, for you to understand how device data are Interchanged on Coolkit Cloud platform.You will be able to develop your application faster with it.It helps you understand the Interaction between users and devices and the process of controlling devices and the response from devices.

Quick start to learn how to develop your own application by referring to the example below.

### Example

Example values are for reference only. Please replace them with your own parameters.

### Workflow

- Step 1.Login, authenticate your account and get authentication token. You will be granted access to services after being authenticated.
- Step  2.Device List. Obtain all the devices in your account. When you control the device, you need to provide related device info and user info.
- Step 3.Access dispatched server to get connection info.
- Step 4.Build persistent connection.Build persistent connection with the connection info from third step.
- Step 5.Handshake.Handshake with the access token(‘at’ means access token) you get on the first step.If handshake is done successfully, you have passed the authentication and should be ready to control devices.
- Step 6.Control the device. Send update command to the device through the device info you get on the second step.

#### Step 1.Login

REST API Test Tool: [https://www.getpostman.com/](https://www.getpostman.com/)

Online Quick Test: [https://getman.cn/](https://getman.cn/)

- URL:  https://{region}-api.coolkit.cc:8080/api/user/login
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
    "appid": "McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "phoneNumber": "+8613185260282", // or "email": "test@test.com"
    "password": "12345678",
    "ts": 1558004249,
    "version":8,
    "nonce": "asbsedwq"
}
```

Note: 

- Change region parameter to your own server. 4 servers available now, respetively cn, as, eu, and us.
- Users in mainland China should use: https://cn-api.coolkit.cn:8080 -> .cn as domain suffix
- Users in other regions should use: https://{region}-api.coolkit.cn:8080 -> .cc as domain suffix
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
    "at": "a527297584f1ca030579a90d2e800481e22e850a",
    "rt": "24670a9e493ba18cf5d9750f14505705824fcfd9",
    "user":{
        "_id": "5c984cd3dc8295fa0ef3e592",
        "phoneNumber": "+8613185260282",
        "appId": "1xMdjbmOBYctEJfye4EjFLR2M6YpYyyJ",
        "lang": "cn",
        "online": false,
        "onlineTime": "2019-05-16T10:48:42.091Z",
        "ip": "113.87.160.95",
        "location": "Guangdong",
        "offlineTime": "2019-05-16T10:51:22.090Z",
        "appInfos":[
            {
                "appVersion": "3.6.1",
                "os": "android"
            }
        ],
        "nickname": "coco",
        "yanKanYunInfo":{
            "username": "yk_+8613185260282",
            "uid": "a26c94ad607a4a47885dcacbcd66b50a",
            "app_id": "15241956565715",
            "accountType": 0,
            "password": "12345678",
            "token": "f4d0e6f389f441f1aa61d815ac833b90"
        },
        "createdAt": "2019-03-25T03:36:51.335Z",
        "apikey": "95da0fea-6834-469a-b247-4dd5ee9a51f1"
    },
    "region": "cn"
}
```

Note: 

- [at] is the required parameter for other interfaces, to replace [Authorization]（Authorization: Bearer+SPACE+at）.
- [rt] is used to refresh [at].
- [region] is the server in which your account is created.

#### Step 2.Obtain device list

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
| lang | string | No | the languages of response, cn means Chinese, en English |
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

Note: If an empty list is returned, then there is no device in this account or the device hasn’t been associated with your APPID. In the case of lack association, you need to contact your salesperson to get help.

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

#### Step 3.Request Dispatchservice

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
    "accept": "ws",
    "appid": "McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
    "ts":15452192511,
    "version":8,
    "nonce": "asbsedwq"
}
```

**Response parameters:**

| Name | Type | Required | Comment |
| :--- | :--- | :--- | :--- |
| IP | string | Yes | server IP for persistent connection |
| port | number | Yes | server port for persistent connection |
| domain | string | Yes | domain name for persistent connection. Currently, only app client returns domain name. IP should be used by android client to reduce issues caused by dns resolution. As js client could not skip certificate check, only domain can be used. |
| error | string | Yes | return ‘error:0’ when successful |
| reason | string | Yes | return ‘ok’ when successful |


Error code: 

0: success  
400: Client Parameter error  
401: authentication failed（ prompts to login）  
402: [at] expired（ APP refreshes [access token] automatically）  
403: no permission（ APP prompts no permission, for instance, app has no permission to access OTA interface）（401-403 authentication error sent by internal authorization system）  
500: server error  

**Example Response:**

```json
{
    "port": 8080,
    "IP": "52.80.19.131",
    "reason": "ok",
    "domain": "cn-pconnect2.coolkit.cc",
    "error": 0
}
```

#### Step 4.Establish persistent connection

Workflows for establishing websocket connection and sending control commands: 

![controlDeviceProcess](./img/controlDeviceProcess.jpeg)

Establish persistant connection through the IP or domain+Port returned from Step 3.

Request: wss://eu-pconnect2.coolkit.cc:8080/api/ws

WebSocket test tool:  [http://www.blue-zero.com/WebSocket/](http://www.blue-zero.com/WebSocket/)

Create handshake through IP returned by Dispatchservice or domain.

#### Step 5.Handshake

![userOnline](./img/userOnline.png)

See pic above: 'connection has been created, receiving data…'.
This means connection has been created successfully. Ready to start handshake.

Handshake example:

```json
{
    "action": "userOnline",
    "version":8,
    "ts":1571141259,
    "at": "<AT>",
    "userAgent": "app",
    "apikey": "<USER APIKEY>",
    "nonce": "2plz69ax",
    "sequence": "1571141530100",
  	"appid": "xxxx"
}
// remove space before you compress it: https://www.json.cn/
```

**handshake success response:**

![userOnlineSuccess.png](./img/userOnlineSuccess.png)

**Hearbeat Interval:**

'hbInterval' means hearbeat Interval. '**ping**' needs to be sent in 145S.Server will respond pong when ping is received.You can send ping manually when testing.

![hbInterval](./img/hbInterval.png)

#### Step 6.Control devices

Note: 

Device will report data when its status changes.Once the app receives the update, it will sync device status. When you are hosting your own server or client, you can also take down the change and use it for statistics or logs features.

![controlDevice](./img/controlDevice.png)

**Send control command:**

Params vary accoridng to protocols.When business agreement is reached, '**protocol documentation**' will be provided by your salesperson based on the type of your devices.

「apikey、deviceid、sequence、params」should be replaced with the parameters of the added devices in your account.

For parameter description, please check '**Update/Report Status**'.

Example:

```json
{
    "action": "update",
    "apikey": "<USER APIKEY>",
    "deviceid": "10000xxxxx",
    "userAgent": "app",
    "sequence": "1571141530100",
    "params":{
        "switch": "off"
    }
}
// remove space before you compress it
```

![controlDeviceSuccess.png](./img/controlDeviceSuccess.png)

**Response:**

'error:0' means success. For more error codes, please check 「**Update/Report Status**」

Example: 

```json
{
    "error":0,
    "deviceid": "10000xxxxx",
    "apikey": "xxxxx",
    "sequence": "1571141530100"
}
```

Note: 

- If device is shared by other user,you must select apikey returned from device list.If you are device owner,both apikey returned from login and apikey from device list will work.
- Device must be online.After command is sent, check if device turns on/off accordingly.When device is offline, error will be returned for sure.

If everything goes on well until now, next, please check '**API Center**' for how to use server region, account, device management, device control and authorization.

## General instructions

Preparation for accessing Cloud platform services,including descriptions of general parameters,introduction to signature rule for authorization,examples for signature calculation, and expanation for access token and refresh token.

Description: 

Parameters in general instructions are public for all APIs.Accessing API takes both general parameters and interface parameters.（General instructions only apply to REST API.For WebSocket API, please check distribution service）

- HTTP Request Header should specify Content-Type:application/json
- Character Encoding: utf-8
- The Authorization field of HTTP Request Header must include signature or access token value
- Both HTTP and websocket uses SSL/TLS，port is 8080，Server end supports SSLV3,TLS1.1, TLS 1.2

### Required Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| appid  | string | Yes | appid provided by Coolkit |
| nonce  | string | Yes | 8-digit random alphanumeric String |
| ts | number | Yes | timestamp of API calling, say current timestamp（timestamp: current time in seconds from Epoch（Jan 1, 1970），say unix-timestamp） |
| version | number | Yes | Numbererface version:8 |

Note: 

- In principle, user or device apikey should be uploaded. Upload apikey of device when operating on devices such as checking device info, change device name etc.
- When getting 400 error from interface, please check these required parameters.

### Signature Rule

- All API accessing(including login) before login requires signature calculation.Signature value is put in **Authorization.**

e.g. _Authorization: Sign QtKh6EnKoNmPnv17Ump3b/6r2hjojWb4nqSt4lnyj2U=_

- GET Request: 
    Order all parameters alphabetically based on the names of parameters and concatenate them with &:

```json
appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&deviceid=1000012345&nonce=2323dfgh&ts=1558004249
```

Signature Calculation:

Set 'app secret' as key，generate sigature String based on HMAC-SHA256.Encode the signature String by Base64 and add to Authorization header.

- POST request:

Create json data with signature String and all other parameters(parameters in general instruction and API parameters).Take example of Login API.

e.g

```json
{"appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr","nonce":"232323df","ts":1558004249,"version":8,"phoneNumber":"+8613123456789","password":"12345678"}
```

Or: 

```json
{"appid":"McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr","nonce":"232323df","ts":1558004249,"version":8,"email":"123@gmail.com","password":"12345678"}
```

**Note:**

Country code must be added to the value of phoneNumber,such as: +86
Only one of phoneNumber and email need to be passed. 'phoneNumber' is passed only for accounts in cn server, 'email' or 'phoneNumber' for as server, 'email' for eu and us server.

**Signature Calculation**

**Sha256 encrypted calculation examples in other programming languages:**[https://www.jokecamp.com/blog/examples-of-creating-base64-hashes-using-hmac-sha256-in-different-languages/](https://www.jokecamp.com/blog/examples-of-creating-base64-hashes-using-hmac-sha256-in-different-languages/)

Online calculation site: [https://1024tools.com/hmac](https://1024tools.com/hmac)

![calculateSignature](./img/calculateSignature.png)

- Signature Algorithm demo①: taking login as example, method: POST（check 'signature rule' for GET method）

```Javascript
// node.js
let crypto = require('crypto');
let appid="McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr";
let appsecret="OdPuCZ4PkPPi0rVKRVcGmll2NM6vVk0c";
let params={"appid": appid, "nonce": "asbsedwq", "password": "12345678", "phoneNumber": "+8613123456789", "ts": 1560306258, "version": 8}
let buffer = Buffer.from(json.stringify(params),"utf-8");
let theSign = crypto.createHmac('sha256', appsecret).update(buffer).digest('base64')
console.log(theSign)
// XuOzGxtG50CiF4H3odUfZsvKVl5+qSPzhfLEuUd4eJw=
```

- Signature Algorithm demo②: 

```Python
# Python
# generate signature
import hashlib
import hmac
import base64
import json

def makeSign(key, message):
    j = hmac.new(key.encode(), message.encode(), digestmod=hashlib.sha256)
    return (base64.b64encode(j.digest())).decode()

def main():
    data = {
        'appid': 'McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr',
        'nonce': 'asbsedwq',
        'password': '12345678',  # password
        'phoneNumber': '+8613123456789',  # mobile number （superior） or email
        'ts': 1560306258,
        'version': 8
    }
    message = json.dumps(data, sort_keys=True) # dict sort
    # '{"appid": "McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr", "nonce": "asbsedwq", "password": "12345678", "phoneNumber": "+8613123456789", "ts": 1560306258, "version": 8}'
    Sign = makeSign(key='OdPuCZ4PkPPi0rVKRVcGmll2NM6vVk0c', message=message)
    print(Sign)
    # XfWcNURxPxpk6Z+6I+WR/j9wHURhvTEK1qa3sAJFNR0=

if __name__ == "__main__":
    main()
```

It is normal that signature value varies according to different orders of characters in signatures.

You can use demo parameters in your own authorization calculation.If the signature value is same as the one above, your signature algorithm is working correctly.

### Descirptions of at and rt

- After login,all API callings require adding access tocken in Authorization header.For example:
Authorization: Bearer a527297584f1ca030579a90d2e800481e22e850a
After login succeeds,access token will be returned（at returned after login，say access token）.
- access token remains valid for one month.One account can not be logined by multiple users at the same time.Every time one logins,token will be refreshed.Thus,the second user who logins later will refresh the token and make the token of previous user expire.First user will be forced to log out.
- Refresh Token remains valid for two months.When access token expires,access token and Refresh Token can be regained by accessing Refresh Token API. Please check 'Refresh Token' for details.

## Pairing devices

### Purposes for pairing

- Get device data
- Connect device to Internet
- Add device to user account

Note: 

- Pairing process only fits for devices that can not be paired by eWeLink APP, such as a device whose APP is developed by yourself.
- Devices that can be added through eWeLink APP do not need to go through this pairing process.
- IP and all other data in this documentation are examples for references only.
- There are two pairing modes, Touch and AP.
- Our Touch pairing is based on [ Espressif ESP-TOUCH SDK](https://www.espressif.com/zh-hans/products/software/esp-touch/resources), but we added encrypted authentication in broadcasting.Please consult your salesperson for this part.

### Pairing Process

![distributionProcess](./img/distributionProcess.png)

#### Touch pairing process

1. Device enters pairing mode: Touch mode.
2. Device waits for APP to broadcast SSID & Password.
3. Device acquires SSID & password and connect to router. Return touch UDP ACK packet.
4. Device establishes TCP server（http server）.
5. Smartphone sends: (Pairing request).

```json
GET /device HTTP/1.1
Host: 172.10.0.163
Accept: application/json
Content-Type: application/json; charset=utf-8
Package-Name: com.coolkit
Cache-Control: no-store
```

6. Device responds:（Responds deviceID, apikey）

```
HTTP/1.1 200 OK  
Content-Type: application/json  
Connection: keep-alive
Content-Length: 99
```

```json
{
  "deviceid": "100000788a",
  "apikey": "4b21ebbe-8870-4d4a-93f2-*********",
  "chipid": "sjljb",
  "accept": "post"
}
```

7. APP requests add device interface and add parameters of devices to user account

8. APP sends: Dispatchserver address, port, WiFi SSID and password

```json
POST /ap HTTP/1.1
Host: 172.10.0.163
Accept: application/json
Content-Type: application/json; charset=utf-8
Package-Name: com.coolkit
Cache-Control: no-store
```

```json
{"port":443,"serverName": "{region}-disp.coolkit.cc","password": "12345678","ssid": "eWeLink"}
```

Note: {region}-disp.coolkit.cc, region can be as, us, eu, for example: eu-disp.coolkit.cc

cn region write：cn-disp.coolkit.cn

9. Device response:

```json
HTTP/1.1 200 OK
Content-Type: application/json
Connection: keep-alive
Content-Length: 11
```

```json
{"error":0}
```

Pairing completed, The application can request the "Get Device List" interface at this time to obtain the added device information. At the same time, a long connection should be established to monitor the device online status and wait for the device online message.

#### AP Pairing Process

Essentially, the device is a hotspot open. After the APP connects to the hotspot of the device, the formal router WIFI information is transmitted to complete the network distribution.

Consistent with steps 1-7 of Touch pairing, step 8 is put to the end (send a POST request to the device first, and then request to add a device interface). WiFi information is transmitted without encryption.

After connecting to the AP of the device, the routing address is: 10.10.7.1 (iOS). Android can obtain the current router IP address from the underlying library.

### Encryption Rule of Pairing 

Because we need to guarantee the security of the brand devices of eWeLink, we have encrypted content during the touch pairing process, so you need to apply to the sales personnel for this information.