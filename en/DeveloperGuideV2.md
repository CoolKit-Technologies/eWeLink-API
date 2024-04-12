# Developer Guide

## Prepare the development environment

Download test software and prepare test equipment

### Download eWeLink

[Android (Google Play)](https://play.google.com/store/apps/details?id=com.coolkit)

[iOS (Apple Store)](https://itunes.apple.com/cn/app/yi-wei-lian/id1035163158?mt=8)

### Purchase test devices

Purchase link: [Amazon store URL](https://www.amazon.cn/s?k=sonoff)

### Register a test account

Install the app, then register an account.

### Log In

Log in to the APP.

### Add Device

Follow the instructions to set the device in pairing mode and add it to your account.

![Add Device](./img/addDevice.png)

### Control Device

When the device is online, you can try to control the device via the APP.

## Become a developer

Only through the assigned APPID can you have the authority to request platform services and contact technical support of eWeLink to shorten the development time.

### APPID

After business cooperation is reached, the APPID will be provided by the salesperson.

### Technical Support

eWeLink staff will create a WeChat group, and technical support will provide services.

## Build the first application

This section explains how to implement data interaction between the client and the device on the Coolkit Cloud Platform from the aspects of account login, acquisition of device data, and establishment of persistent connections to achieve device control.

Let’s get started  with a sample "How to develop my own application?".

### Basic Process

- Step 1: Log in to the account and get the access token by authenticating the account. Only after passing the authentication can you gain access to the service.
- Step 2: Request the "Get Home Page" or "Get Things List" interface to get all the devices added under the account. Controlling devices requires device and user data.
- Step 3: Access the Dispatchservice to get the port, persistent connection IP, and other information.
- Step 4: Establish a persistent connection. According to the information obtained from step 3, establish a connection.
- Step 5: According to the authentication information (at means access token) obtained from step 1, establish the handshake. Once the handshake is established, you've passed the authentication and you are allowed to control devices.
- Step 6: Control the device. Send the update command according to the device information obtained from step 2 to control the device.
- Step 7: Monitor the device status. After establishing a persistent connection, wait until device status changes, and then receive an update command from the device.

### Signature Rules

- Calling all interfaces before login (including the login interface) requires signature calculation, and The signature value is placed in the **Authorization** parameter of the request header.

Example: Authorization: Sign QtKh6EnKoNmPnv17Ump3b/6r2hjojWb4nqSt4lnyj2U=

Calculate the signature:

Use the "app secret" as the key to generate the HMAC-SHA256 signature of the signed string, and set the Base64-encoded signature to Authorization.

- GET request:

Sort all parameters (except sign) in alphabetical order and connect them with&:

```
appid=McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr&deviceid=1000012345&nonce=2323dfgh&ts=1558004249
```

- POST request:

The string to be encrypted is the entire body of the json data (http body). Take the login interface as an example.

For example:

```json
{"email":"1234@gmail.com","password":"12345678","countryCode":"+1"}
```

**Notes:**

The value of phoneNumber needs to add country code such as: +86

phoneNumber or email, only one of them need to be passed. In China mainland only "phoneNumber" can be passed. In the rest of Asia region, "phoneNumber" or "email" can be passed, and "email" can be passed in Europe and America.

Calculating the signature:

Use the "app secret" as the key to generate the HMAC-SHA256 signature of the signed string, and set the Base64-encoded signature to Authorization.

**Signature Calculation**

**Examples of Sha256 encryption functions in 15 programming languages:** [https://www.jokecamp.com/blog/examples-of-creating-base64-hashes-using-hmac-sha256-in-different-languages/ ](https://www.jokecamp.com/blog/examples-of-creating-base64-hashes-using-hmac-sha256-in-different-languages/)

Online Calculator: [https://1024tools.com/hmac ](https://1024tools.com/hmac)

![calculateSignature](./img/calculateSignature.png)

- Digital Signature Algorithm Demo ①: Take the login interface as an example (Method: POST).

```JavaScript
// node.js
var crypto = require('crypto');
let appsecret="OdPuCZ4PkPPi0rVKRVcGmll2NM6vVk0c";
let body={"email":"1234@gmail.com","password":"12345678","countryCode":"+1"}
let buffer = Buffer.from(JSON.stringify(body),"utf-8" );
let theSign = crypto.createHmac('sha256', appsecret).update(buffer).digest('base64')
// or let theSign = CryptoJS.enc.Base64.stringify(CryptoJS.HmacSHA256(buffer, appsecret));
console.log(theSign)
// ttZ/gluzqrafvGonjMD20p4//arW6KoZKbo1SOMEzCA=
```

- Digital Signature Algorithm Demo ②:

```Python
# Python
#Gernerate signature 
import hashlib
import hmac
import base64
import json

def makeSign(key, message):
    j = hmac.new(key.encode(), message.encode(), digestmod=hashlib.sha256)
    return (base64.b64encode(j.digest())).decode()

def main():
    data = {
        "email":"1234@gmail.com",
        "password":"12345678",
        "countryCode":"+1"
    }
    message = json.dumps(data)
    # '{"email":"1234@gmail.com","password":"12345678","countryCode":"+1"}'
    Sign = makeSign(key='OdPuCZ4PkPPi0rVKRVcGmll2NM6vVk0c', message=message)
    print(Sign)
    # cE/Wl57Ithy21Elieq5wFsYwJWl2IrkBxlmuCnwI73c=

if __name__ == "__main__":
    main()
```

Notes: Due to the different character sequence, the signature will be different, which is normal case.

You can put the parameters of the demo in your own signature algorithm. If the calculated signature value is consistent with the provided signature value,  means that the signature algorithm has passed.

### Description of AT and RT:

- All interfaces that can only be called after logging in need to add an access token to the Authorization parameter of the request header, for example: Authorization: Bearer a527297584f1ca030579a90d2e800481e22e850a When logging in to the interface successfully, it will return access token (at after successful login, that is, access token).
- The access token is valid for one month. The same account cannot be logged in to the same application at the same time. The token will refresh every time when logging in. Therefore, users who log in later will refresh their tokens, which invalidates the tokens of users who log in earlier, and forces them to go offline.
- The Refresh Token is valid for two months.When the access token expires, you can request the refresh interface through the Refresh Token, and get new access token and Refresh Token.For details, please refer to [Refresh Authentication Token](/en/APICenterV2?id=refresh-access-token).

## Device pairing

### Pairing Purpose

- Get device data and validation data
- Connect the device to the network
- Add the device to the user account

Note:

- The pairing process is only applicable to applications that do not pair devices through the eWeLink APP.
- Devices added by the eWeLink APP does not need to implement the pairing process.
- The IP and various data in the document are just examples.
- Device pairing have two pairing modes: Touch and AP.
- Our Touch pairing is based on [ Espressif ESP-TOUCH SDK ](https://www.espressif.com/zh-hans/products/software/esp-touch/resources) , but the password was encrypted in WiFi. For more information, please consult with the sales representatives.

### Pairing process

![distributionProcess](./img/distributionProcess.png)

#### Touch pairing

1. Device enters pairing mode: Touch mode
2. The device waits for APP multicast SSID & Password

```json
{"ssid":"cktc","password":"ck112233","bssid":"18:40:a4:bb:ec:ae"}
```

3. After the device get the SSID & Password, it connects to the router and returns the touch UDP confirmation packet

The APP will receive：

```json
{"bssid":"*********","inetAddress":"172.10.0.163"}
```

4. The device builds a TCP Server (HTTP Server)
5. The mobile phone sends a request to the device (to obtain device information):

```json
GET /device HTTP/1.1
Host: 172.10.0.163
Accept: application/json
Content-Type: application/json; charset=utf-8
Package-Name: com.coolkit
Cache-Control: no-store
```

Notes：This step can be retried multiple times. eWeLink will retry 5 times with a total interval of 70 seconds, which can be fine-tuned to adapt to the device.

6. Device response:

```
HTTP/1.1 200 OK  
Content-Type: application/json  
Connection: keep-alive
Content-Length: 99
```

```json
{
  "deviceid":"100000788a",
  "apikey":"4b21ebbe-8870-4d4a-93f2-*********",
  "chipid":"sjljb",
  "accept":" post"
}
```

7. APP requests "Add WiFi Device" HTTP interface, the request parameters include device ID, device APIKEY, CHIPID and other information. After the call is successful, the device can be added to the user account.

8. APP sending: Dispatchservice address, port number, WiFi hotspot SSID and password

```json
POST /ap HTTP/1.1
Host: 172.10.0.163
Accept: application/json
Content-Type: application/json; charset=utf-8
Package-Name: com.coolkit
Cache-Control: no-store
```

Body：

```json
{"port":443,"serverName":"device long connection Dispatchdomain name","password":"12345678","ssid":"eWeLink"}
```

Notes：This step can be retried multiple times. eWeLink will retry 5 times with a total interval of 70 seconds, which can be fine-tuned to adapt to the device.

**If Post request fails, please check if a string is passed as the port parameter.**

Distributed persistent connection domain name for the device(not including api, port 443)：

- CN: cn-dispd.coolkit.cn
- US: us-dispd.coolkit.cc
- EU: eu-dispd.coolkit.cc
- AS: as-dispd.coolkit.cc

9. Device response:

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Connection: keep-alive
Content-Length: 11
```

```json
{"error":0}
```

#### AP Pairing

The AP pairing is to enable device hotspot. After the app connects to the device hotspot, the router WiFi information will be sent to the device to complete pairing.

Device hotspot SSID format: ITEAD-{deviceID}. Hotspot password: 12345678.

After the APP connects to the device hotspot, steps 6 and 10 will be performed. Once the device responds, the app disconnects the device hotspot, and connects to the home WiFi, requests the "Add WiFi device" interface, and then adds the device to the account.

Note: iOS requires the user to manually connect to the device hotspot due to system permission restrictions. After connecting, the device hotspot IP address is: 10.10.7.1. Android can obtain the current router IP address from the underlying library, and the IP address is not fixed.

#### Refresh and get device online

After the pairing is completed, the app should request the "Get Home Page " or "Get Thing List" interface to obtain the added device. At the same time, a oersistent connection should be established to monitor the online status of the device, and wait for the device's online message.

### Encryption Rules

To ensure the security of the eWeLink platform, eWeLink has set encryption rules for the Touch pairing to refuse illegal clients to add our device.

Please contact the CoolKit salesperson or technical support for the document of the encryption rules.