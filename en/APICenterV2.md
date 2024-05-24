# API Center

## Overview

The APIs in this document applies HTTPS protocol, in which the client sends data with UTF-8 encoding and in json format.

**Please consider using 'Get device or group status' endpoint instead of ‘Homepage’ endpoint to get single device resource.**

### Requirements of Calling Interface (Important):

- The interval of a single IP calling the same Interface should be greater than or equal to 500ms, with no more than 300 calls in 5 minutes. If you control our devices via WebSocket, please keep in mind that every user is not allowed to log in and log out repeatedly for a short period of time (Send userOnline command). Otherwise, your IP will be blocked and terminated by the server if the userOnline command are sent too many times for a short period.
- Partners who has the business certification and enterprises that purchased the APPID have the access to [Paid APPID] to call all Interfaces without limitations for the total number of calls now but there are the same regulations for calling frequency as the above first point.（According to the conversion between the number of connected devices and the number of users, if it exceeds the official usage, advance notice will be given, ignoring the possibility of being banned in the current month. The restrictions on the frequency of calls in the short term should be consistent with the first point mentioned above.）
- For APPID applied by enterprises and personal developers, Currently open some authorized brands of equipment, as well as mainstream equipment types (which will be released in batches soon, please stay tuned). If you have demand for other complex device types or new device types, please contact our relevant staff or email us via [bd@coolkit.cn](mailto:bd@coolkit.cn).

### General parameters

Compared with the old API, below changes are made to the general parameters：

- ‘ts’, ‘version’ are deleted.
- appid can no longer be passed through the queryString of GET method or the body of POST method. Instead, it is passed via http header. In addition, it is only required for the endpoints in the user category, but not required for other endpoints.
- nonce can no longer be passed through the queryString of GET method or the body of POST method. Instead, it is passed via http header. In addition, it must be string of 8 digits with uppercase and lowercase letters and numbers only.

How access token is used remains the same.See below:

| **Http Header** | **Allows empty**                                        | **Description**                                                                                                                                                                                                                                                                                            |
| :-------------- | :------------------------------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| X-CK-Appid      | The interface under the [User] category cannot be empty | The idendifier assigned to the app to control the interface calling permission                                                                                                                                                                                                                             |
| X-CK-Nonce      | Yes                                                     | A combination of 8 uppercase or lowercase letters and numbers. The client should try to use random strings to facilitate joint debugging with the server.                                                                                                                                                  |
| Authorization   | Not allowed to be empty                                 | API call voucher in the form of "Sign {sign}" or "Bearer {at}",see [Development Documents/Signature Rules for the calculation method](/en/DeveloperGuideV?id=signature-rules), the full name of at is access token, which can be obtained in login, registration, password reset and refresh at interface. |
| Content-Type    | PUT and POST requests are not allowed to be empty       | Fixed as "application/json" or "application/json; charset=utf-8"                                                                                                                                                                                                                                           |
| Host            | Not allowed to be empty                                 | Most HTTP clients will automatically add this field. If not, it must be explicitly specified by the code. The value is the corresponding interface domain name, such as: cn-apia.coolkit.cn, us-apia.coolkit.cc                                                                                            |

### Interface domain name

- Mainland China: https://cn-apia.coolkit.cn
- Asia: https://as-apia.coolkit.cc
- Americas: https://us-apia.coolkit.cc
- Europe: https://eu-apia.coolkit.cc

Note: The domain name for China (mainland) is **.cn** , The domain name of other regions is **.cc**

### Interface response format

The data returned by all interfaces of this protocol uses UTF-8 encoding and json format.The data format is as follows

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                                                                                           |
| :------- | :------- | :--------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| error    | Int      | N                | Error code, 0 means no error. Common error code within 1000. Please refer to the [General Error Code] section of this agreement. Error code above 1000 is defined by different interfaces |
| data     | Object   | N                | Interface data                                                                                                                                                                            |
| msg      | String   | N                | Error information, when error=0, it is an empty string "". Other codes are returned based on different interfaces.                                                                        |

Example 1: Success response

```json
{
  "error": 0,
  "msg": "",
  "data": {
    "data1": "xxx",
    "data2": "yyy"
  }
}
```

Example 2: Error response

```json
{
  "error": 403,
  "msg": "api not found",
  "data": {}
}
```

### Postman Example

**Postman Demo Download：[CoolKit_API_Postman_Demo.zip](https://raw.githubusercontent.com/CoolKit-Technologies/eWeLink-API/main/media/files/CoolKit_API_Postman_Demo.zip)**

Import [Postman](https://www.postman.com/downloads/) and fill in your application information in the environment file.

General tutorial: [Click Me](https://learning.postman.com/docs/getting-started/importing-and-exporting-data/)

### JavaScript Example

It is recommended to use pnpm and download `ewelink-api-next`(node >= 16.16)

```bash
pnpm i ewelink-api-next
# or npm install ewelink-api-next
```

#### Code Example

```typescript
// eWeLink v2 API

import eWeLink from 'ewelink-api-next'

const client = new eWeLink.WebAPI({
  appId: 'xxx',
  appSecret: 'xxx',
  region: 'us',
  logObj: eWeLink.createLogger('us'), // or console
})

client.syncLocalToken((region = 'us'), (account = 'xxx@xxx.net'))
try {
  const response = await client.user.login({
    account: 'xxx@xxx.com',
    password: '12345678',
    areaCode: '+1',
  })
  const userInfo = response.error === 0 ? response.data.user : {}
  console.log('userInfo：', userInfo)
} catch (err) {
  console.log('Failed to get user information:', err.message)
}
```

```typescript
// eWeLink WebSocket API

import eWeLink from 'ewelink-api-next'

const wsClient = new eWeLink.Ws({
  appId: 'xxx',
  appSecret: 'xxx',
  region: 'us',
})
wsClient.syncLocalToken((region = 'us'), (account = 'xxx@xxx.net'))

let ws = await wsClient.Connect.create({
  appId: wsClient?.appId || '',
  at: wsClient.at,
  region: 'us',
  userApiKey: wsClient.userApiKey,
})

setTimeout(() => {
  wsClient.Connect.updateState('xxxx', {
    switch: 'on',
  })
}, 5000)
```

```typescript
// eWeLink Lan Control
import eWeLink from 'ewelink-api-next'

const lanClient = new eWeLink.Lan({
  selfApikey: 'xxx',
  logObj: eWeLink.createLogger('lan'),
})

lanClient.discovery((server) => {
  console.log('server:', server)
}) // Start Discovery Service
try {
  const res = await lanClient.zeroconf.switches({
    data: {
      switch: 'on',
    },
    deviceId: 'xxx',
    secretKey: 'xxx',
  })
  console.info('Request result:：', res)
  const res2 = await lanClient.zeroconf.switches({
    data: {
      switch: 'off',
    },
    deviceId: 'xxx',
    secretKey: 'xxx',
  })
  console.info('Request result:：', res2)
} catch (error: any) {
  console.info(error.message)
}
```

## User

### Get Region

This interface is a global interface, and the URL when all regions call this interface is the same URL: https://apia.coolkit.cn/v2/utils/get-region

Request method: GET

Authorization parameter: Sign

Request parameters:

| **Name**    | **Type** | **Allows empty** | **Description**                    |
| :---------- | :------- | :--------------- | ---------------------------------- | --- |
| :---------- | :------- | :-----------     | :-----------------------------     | --- |
| countryCode | String   | N                | Area Code starting with "+", such as "+86" |     |

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                                                                      |
| :------- | :------- | :--------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| region   | String   | N                | The region corresponding to the telephone area code selected by the user has the following conditions: as: Asia; cn: Inland China; us: Americas; eu: European Region |

### Create account

Account registration rules:

- CN Region: +86 mobile number
- AS Region: Philippines+63, Vietnam+84, Cambodia+855, Laos+856, Malaysia+60, Singapore+65, Myanmar+95, Thailand+66, Brunei+673, Indonesia+62, Timor-Leste+670, Iran +98, China Taiwan +886 13 regions support using mobile phone number to register and log in, but do not support verification code login, 12 countries in AS region and China Taiwan prompt "Please enter mobile phone or email" when registering, other countries and regions According to the original, that is, the foreign prompt "please enter your email address", the domestic prompt: "please fill in your phone number"; when users from 12 countries in the AS region and Taiwan use mobile phone numbers to register, they will fill in the verification code page and the 1-minute countdown will end. Prompt text: "If you haven't received the verification code, please check whether the selected country code is correct and then click to send the verification code", and the email registered user fills in the verification code when the 1-minute countdown ends and keeps the original prompt unchanged, that is, " There may be a delay in the verification code, if you do not receive it after 3 minutes, click Send Verification Code".
- Password rules: any combination of 8 or more alphanumeric characters.

Area code corresponding area:

```JavaScript
const AreaCodes = [
    { "+86": "China" },
    { "+93": "Afghanistan" },
    { "+355": "Albania" },
    { "+213": "Algeria" },
    { "+376": "Andorra" },
    { "+244": "Angola" },
    { "+1264": "Anguilla" },
    { "+247": "Ascension" },
    { "+1268": "Antigua and Barbuda" },
    { "+54": "Argentina" },
    { "+374": "Armenia" },
    { "+297": "Aruba" },
    { "+61": "Australia" },
    { "+43": "Austria" },
    { "+994": "Azerbaijan" },
    { "+1242": "Bahamas" },
    { "+973": "Bahrain" },
    { "+880": "Bangladesh" },
    { "+1246": "Barbados" },
    { "+375": "Belarus" },
    { "+32": "Belgium" },
    { "+501": "Belize" },
    { "+229": "Benin" },
    { "+1441": "Bermuda" },
    { "+975": "Kingdom of Bhutan" },
    { "+591": "Bolivia" },
    { "+387": "Bosnia and Herzegovina" },
    { "+267": "Botswana" },
    { "+55": "Brazil" },
    { "+673": "Brunei" },
    { "+359": "Bulgaria" },
    { "+226": "Burkina Faso" },
    { "+257": "Burundi" },
    { "+855": "Cambodia" },
    { "+237": "Cameroon" },
    { "+1": "Canada" },
    { "+238": "Cape Verde Republic" },
    { "+1345": "Cayman Islands" },
    { "+236": "Central African Republic" },
    { "+235": "Chad" },
    { "+56": "Chile" },
    { "+57": "Colombia" },
    { "+269": "Islamic Federal Republic of Comoros" },
    { "+242": "Republic of Congo" },
    { "+243": "Democratic Republic of Congo" },
    { "+682": "Cook Islands" },
    { "+506": "Costa Rica" },
    { "+225": "Ivory Coast" },
    { "+385": "Croatia" },
    { "+53": "Cuba" },
    { "+357": "Cyprus" },
    { "+420": "Czech" },
    { "+45": "Denmark" },
    { "+253": "Djibouti" },
    { "+1767": "Dominica" },
    { "+1809": "Dominican Republic" },
    { "+593": "Ecuador" },
    { "+20": "Egypt" },
    { "+503": "El Salvador" },
    { "+372": "Estonia" },
    { "+251": "Ethiopia" },
    { "+298": "Faroe Islands" },
    { "+679": "Fiji" },
    { "+358": "Finland" },
    { "+33": "France" },
    { "+594": "French Guiana" },
    { "+689": "French Polynesia" },
    { "+241": "Gabon" },
    { "+220": "Gambia" },
    { "+995": "Georgia" },
    { "+49": "Germany" },
    { "+233": "Ghana" },
    { "+350": "Gibraltar" },
    { "+30": "Greece" },
    { "+299": "Greenland" },
    { "+1473": "Grenada" },
    { "+590": "Guadeloupe" },
    { "+1671": "Guam" },
    { "+502": "Guatemala" },
    { "+240": "Guinea" },
    { "+44": "Guernsey" },
    { "+224": "Guinea" },
    { "+592": "Guyana" },
    { "+509": "Haiti" },
    { "+504": "Honduras" },
    { "+852": "Hong Kong, China" },
    { "+95": "Myanmar" },
    { "+36": "Hungary" },
    { "+354": "Iceland" },
    { "+91": "India" },
    { "+62": "Indonesia" },
    { "+98": "Iran" },
    { "+964": "Republic of Iraq" },
    { "+353": "Ireland" },
    { "+44": "Isle of Man" },
    { "+972": "Israel" },
    { "+39": "Italian" },
    { "+1876": "Jamaica" },
    { "+81": "Japan" },
    { "+44": "Jersey" },
    { "+962": "Jordan" },
    { "+7": "Republic of Kazakhstan" },
    { "+254": "Kenya" },
    { "+383": "Kosovo" },
    { "+965": "Kuwait" },
    { "+996": "Kyrgyzstan" },
    { "+856": "Laos" },
    { "+371": "Latvia" },
    { "+961": "Lebanon" },
    { "+266": "Lesotho" },
    { "+231": "Liberia" },
    { "+218": "Libya" },
    { "+423": "Liechtenstein" },
    { "+370": "Lithuania" },
    { "+352": "Luxembourg" },
    { "+853": "Macau, China" },
    { "+389": "Republic of Macedonia" },
    { "+261": "Madagascar" },
    { "+265": "Malawi" },
    { "+60": "Malaysia" },
    { "+960": "Maldives" },
    { "+223": "Mali" },
    { "+356": "Malta" },
    { "+596": "Martinique" },
    { "+222": "Mauritania" },
    { "+230": "Mauritius" },
    { "+262": "Mayotte" },
    { "+52": "Mexico" },
    { "+373": "Moldova" },
    { "+377": "Monaco" },
    { "+976": "Mongolia" },
    { "+382": "Montenegro" },
    { "+1664": "Montserrat" },
    { "+212": "Morocco" },
    { "+258": "Mozambique" },
    { "+264": "Namibia" },
    { "+977": "Nepal" },
    { "+31": "Netherlands" },
    { "+599": "Netherlands Antilles" },
    { "+687": "New Caledonia" },
    { "+64": "New Zealand" },
    { "+505": "Nicaragua" },
    { "+227": "Niger" },
    { "+234": "Nigeria" },
    { "+47": "Norway" },
    { "+968": "Oman" },
    { "+92": "Pakistan" },
    { "+970": "Palestine" },
    { "+507": "Panama" },
    { "+675": "Papua New Guinea" },
    { "+595": "Paraguay" },
    { "+51": "Peru" },
    { "+63": "Philippines" },
    { "+48": "Poland" },
    { "+351": "Portugal" },
    { "+1": "Puerto Rico" },
    { "+974": "Qatar" },
    { "+262": "Reunion" },
    { "+40": "Romania" },
    { "+7": "Russia" },
    { "+250": "Rwanda" },
    { "+684": "Eastern Samoa (US)" },
    { "+685": "Western Samoa" },
    { "+378": "San Marino" },
    { "+239": "Sao Tome and Principe" },
    { "+966": "Saudi Arabia" },
    { "+221": "Senegal" },
    { "+381": "Serbia" },
    { "+248": "Seychelles" },
    { "+232": "Sierra Leone" },
    { "+65": "Singapore" },
    { "+421": "Slovakia" },
    { "+386": "Slovenia" },
    { "+27": "South Africa" ​​},
    { "+82": "South Korea" },
    { "+34": "Spain" },
    { "+94": "Sri Lanka" },
    { "+1869": "Saint Kitts and Nevis" },
    { "+1758": "Saint Lucia" },
    { "+1784": "Saint Vincent" },
    { "+249": "Sultan" },
    { "+597": "Suriname" },
    { "+268": "Swaziland" },
    { "+46": "Sweden" },
    { "+41": "Switzerland" },
    { "+963": "Syria" },
    { "+886": "Taiwan, China" },
    { "+992": "Tajikistan" },
    { "+255": "Tanzania" },
    { "+66": "Thailand" },
    { "+670": "East Timor" },
    { "+228": "Togo" },
    { "+676": "Tonga" },
    { "+1868": "Trinidad and Tobago" },
    { "+216": "Tunisia" },
    { "+90": "Turkey" },
    { "+993": "Turkmenistan" },
    { "+1649": "Turks and Caicos" },
    { "+256": "Uganda" },
    { "+380": "Ukraine" },
    { "+971": "United Arab Emirates" },
    { "+44": "UK" },
    { "+1": "United States" },
    { "+598": "Uruguay" },
    { "+998": "Uzbekistan" },
    { "+678": "Vanuatu" },
    { "+58": "Venezuela" },
    { "+84": "Vietnam" },
    { "+1340": "Wilk Islands" },
    { "+967": "Yemen" },
    { "+260": "Zambia" },
    { "+263": "Zimbabwe" }
]
```

URL: /v2/user/register

Request method: POST

Authorization parameter: Sign

Request parameters:

| **Name**         | **Type** | **Allows empty** | **Description**                                                                                                                                                          |
| :--------------- | :------- | :--------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| countryCode      | String   | N                | Area Code starting with "+", such as "+86"                                                                                                                               |
| email            | String   | Y                | Email address, case-insensitive (as the system automatically saves lowercase).                                                                                           |
| phoneNumber      | String   | Y                | Mobile phone number（checked in priority）which starts with country code such as "+8618023456789". Either email or phoneNumber is required. Otherwise, error will occur. |
| verificationCode | String   | N                | SMS/email verification code                                                                                                                                              |
| password         | String   | N                | Password                                                                                                                                                                 |

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                         |
| :------- | :------- | :--------------- | :-------------------------------------------------------------------------------------- |
| user     | Object   | N                | User Info                                                                               |
| at       | String   | N                | Access Token                                                                            |
| rt       | String   | N                | Refresh Token                                                                           |
| region   |  String  | N                | Region server to which the user belongs. cn=Mainland China as=Asia us=America eu=Europe |

user:

| **Name**       | **Type** | **Allows empty** | **Description**                                                                                                                                                                                                                                                                                                                                                |
| :------------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| countryCode    | String   | Y                | Area Code starting with "+", such as "+86"                                                                                                                                                                                                                                                                                                                     |
| phoneNumber    | String   | Y                | User mobile number with country code such as +8615815725225                                                                                                                                                                                                                                                                                                    |
| email          | String   | Y                | User email. Either mobile number or email is required.                                                                                                                                                                                                                                                                                                         |
| apikey         | String   | N                | User ID                                                                                                                                                                                                                                                                                                                                                        |
| nickname       | String   | Y                | User nickname                                                                                                                                                                                                                                                                                                                                                  |
| wxServiceId    | String   | Y                | WeChat Service Account                                                                                                                                                                                                                                                                                                                                         |
| wxAppId        | String   | Y                | AppID of WeChat service account                                                                                                                                                                                                                                                                                                                                |
| wxId           | String   | Y                | WeChat user ID                                                                                                                                                                                                                                                                                                                                                 |
| wxOpenId       | String   | Y                | WeChat user Open ID                                                                                                                                                                                                                                                                                                                                            |
| yanKanYunInfo  | Object   | Y                | Yaokan Cloud account                                                                                                                                                                                                                                                                                                                                           |
| accountLevel   | Int      | N                | Account level 10=Free 20=Advanced 30=Pro                                                                                                                                                                                                                                                                                                                       |
| levelExpiredAt | Long     | Y                | Subscription expiration timestamp, which is accurate to milliseconds. If this field is empty or 0, it means there is no expiration time                                                                                                                                                                                                                        |
| denyRecharge   | Boolean  | Y                | Whether the current account is allowed to extend subscription period. When this field is empty or the value is false, the current acccount can be recharged. Otherwise, recharge is prohibited.                                                                                                                                                                |
| accountConsult | Boolean  | Y                | Inquired subscription plans or not                                                                                                                                                                                                                                                                                                                             |
| ipCountry      | String   | Y                | server side works out the country and region of the user based on requester ip. Please refer to alpha-2 version of the list of country codes [here](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes). When "Get User Information" or "Homepage" interface (with the getUser parameter) is called, this field will be returned by the server side. |

See [Login](/en/APICenterV2?id=account-login) interface for error responses.

### Login

URL: /v2/user/login

Request method: POST

Authorization parameter: Sign

Request parameters:

| **Name**    | **Type** | **Allows empty** | **Description**                                                                                                                                                          |
| :---------- | :------- | :--------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| lang        | String   | Y                | cn returns Chinese, and en returns English, default en                                                                                                                   |
| countryCode | String   | N                | Area Code starting with "+", such as "+86"                                                                                                                               |
| email       | String   | Y                | Email address, case-insensitive                                                                                                                                          |
| phoneNumber | String   | Y                | Mobile phone number（checked in priority）which starts with country code such as "+8618023456789". Either email or phoneNumber is required. Otherwise, error will occur. |
| password    | String   | N                | Password                                                                                                                                                                 |

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                         |
| :------- | :------- | :--------------- | :-------------------------------------------------------------------------------------- |
| user     | Object   | N                | User info. Please refer to the [Register an account] interface                          |
| at       | String   | N                | Access Token                                                                            |
| rt       | String   | N                | Refresh Token                                                                           |
| region   |  String  | N                | Region server to which the user belongs. cn=Mainland China as=Asia us=America eu=Europe |

When the error is 10004, it means that the account is not in the current region, and the client needs to call the login interface of corresponding region based on returned info. Response example:

```json
{
  "error": 10004,
  "msg": "redirection",
  "data": { "region": "eu" }
}
```

### SMS Login

URL: /v2/user/sms-login

Request method: POST

Authorization parameter: Sign

Note: **This interface can only be accessed with mobile numbers in mainlan China.**

Request parameters:

| **Name**         | **Type** | **Allows empty** | **Description**                                                          |
| :--------------- | :------- | :--------------- | :----------------------------------------------------------------------- |
| countryCode      | String   | N                | Area Code starting with "+", such as "+86"                               |
| lang             | String   | Y                | cn returns Chinese, and en returns English, default en                   |
| phoneNumber      | String   | N                | Mobile phone number starting with country code, such as "+8618023456789" |
| verificationCode | String   | N                | SMS Verification Code                                                    |

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                |
| :------- | :------- | :--------------- | :------------------------------------------------------------- |
| user     | User     | N                | User info. Please refer to the [Register an account] interface |
| at       | String   | N                | Access Token                                                   |
| rt       | String   | N                | Refresh Token                                                  |
| region   | String   | N                | User's region code cn=China as=Asia us=Americas eu=Europe      |

See [Login](/en/APICenterV2?id=account-login) interface for error responses.

### Send Verification Code

URL: /v2/user/verification-code

Request method: POST

Authorization parameter: Sign

Note: For the same mailbox or mobile phone number, there are sending limits as follows:

- No more than 3 times within 1 minute.
- No more than 20 times in 1 hour.
- No more than 100 times in 1 day.

Request parameters:

| **Name**    | **Type** | **Allows empty** | **Description**                                                                                                                                                                    |
| :---------- | :------- | :--------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type        | Int      | N                | Type of verification code, 0: Register 1: Reset password 3: Delete account 4: Verification code login                                                                              |
| email       | String   | Y                | Email to send verification to, case sensitive.                                                                                                                                     |
| phoneNumber | String   | Y                | The mobile number to send verification to, which should start with country code such as “+8618023456789”. Either email or phoneNumber is required, otherwise, an error will occur. |

When the error is 10004, it means that the account is not in the current region, and the client needs to call the login interface of corresponding region based on returned info. Example response as follows:

```json
{
  "error": 10004,
  "msg": "redirection",
  "data": { "region": "eu" }
}
```

Response data parameter: None

### Reset Password

URL: /v2/user/reset-pwd

Authorization parameter: Sign

Description: If the user forgets their password, they can use this interface to reset it.

Request method: POST

Request parameters:

| **Name**         | **Type** | **Allows empty** | **Description**                                                                                                                                   |
| :--------------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------ |
| email            | String   | Y                | Email address, case-insensitive                                                                                                                   |
| phoneNumber      | String   | Y                | Mobile phone number starting with country code such as "+8618023456789". Either email or phoneNumber is required. Otherwise, an error will occur. |
| verificationCode | String   | N                | Verification code                                                                                                                                 |
| password         | String   | N                | Password                                                                                                                                          |

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                |
| :------- | :------- | :--------------- | :------------------------------------------------------------- |
| user     | Object   | N                | User info. Please refer to the [Register an account] interface |
| at       | String   | N                | Access Token                                                   |
| rt       | String   | N                | Refresh Token                                                  |
| region   |  String  | N                | User's region code cn=China as=Asia us=Americas eu=Europe      |

### Change Password

URL: /v2/user/change-pwd

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name**    | **Type** | **Allows empty** | **Description** |
| :---------- | :------- | :--------------- | :-------------- |
| oldPassword | String   | N                | old password    |
| newPassword | String   | N                | new password    |

Response data parameter: None

### Get User Information

URL: /v2/user/profile

Request method: GET

Authorization parameter: Token

Request parameters:

None

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                |
| :------- | :------- | :--------------- | :------------------------------------------------------------- |
| user     | Object   | N                | User info. Please refer to the [Register an account] interface |
| region   |  String  | N                | User's region code cn=China as=Asia us=Americas eu=Europe      |

### Update User Information

URL: /v2/user/profile

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name**       | **Type** | **Allows empty** | **Description**                                                                                                                                                                                |
| :------------- | :------- | :--------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| nickname       | String   | Y                | The user's nickname to be updated. If this field is empty or NULL, it means that the nickname will not be updated.                                                                             |
| acceptEmailAd  | Boolean  | Y                | Is the user subscribed to newsletter. If this field is empty or NULL, it means not to update.                                                                                                  |
| accountConsult | Boolean  | Y                | When the user has inquired subscription plans belore, the value will be fixed as true. Passing other values will cause error response. If this field is empty or NULL, it means not to update. |

Response data parameter: None

### Refresh Access Token

URL: /v2/user/refresh

Request method: POST

Authorization parameter: Token or Sign

Note: The Access Token expires in 30 days by default (for security reasons). When this happens, you do not need to log in again to obtain the Access Token, but call this interface to refresh the Access Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description** |
| :------- | :------- | :--------------- | :-------------- |
| rt       | String   | N                | Refresh Token   |

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description** |
| :------- | :------- | :--------------- | :-------------- |
| at       | String   | N                | Access Token    |
| rt       | String   | N                | Refresh Token   |

### Logout

URL: /v2/user/logout

Request method：DELETE

Authorization parameter: Token

Request parameter：none

Response data parameter：None

### Delete Account

URL: /v2/user/close-account

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name**         | **Type** | **Allows empty** | **Description**   |
| :--------------- | :------- | :--------------- | :---------------- |
| verificationCode | String   | N                | Verification code |

Response data parameter: None

## Home Page

### Get home page information

Note:

- When the user device (total parameter) exceeds 30, you need to set the beginIndex parameter to get it in pages, otherwise too much data will be acquired and the server will return timeout errors such as 500.
- The total parameter returned may be greater than the total amount of device data returned, which indicates that not all device data has been obtained. The specific reason is: at present, we only authorize the brands of Sonoff and CoolKit. The brands of other manufacturers can only be used after signing a letter of authorization with the help of our business colleagues. See the chapter "APICenterV2 - > Requirements of Calling Interface (Important)" for details.

URL: /v2/homepage

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name**   | **Type** | **Allows empty** | **Description**                                                                                                                                   |
| :--------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------ |
| lang       | String   | Y                | cn returns Chinese, and en returns English, default en                                                                                            |
| clientInfo | Object   | Y                | Client information                                                                                                                                |
| getUser    | Object   | Y                | If you want to get user information, fill in this field                                                                                           |
| getFamily  | Object   | Y                | If you want to get homes, fill in this field to get the information of all your homes.                                                            |
| getThing   | Object   | Y                | If you want to get things, fill in this field, but this field only returns the information of all the things in the current home.                 |
| getScene   | Object   | Y                | Scene list, not yet open                                                                                                                          |
| getMessage | Object   | Y                | If you want to get all the noficiations in the message center, fill in this field, but it only returns all the notifications in the current home. |

clientInfo description:

| **Name**   | **Type** | **Allows empty** | **Description**                                     |
| :--------- | :------- | :--------------- | :-------------------------------------------------- |
| model      | String   | Y                | Phone model, such as "M6 Note"                      |
| os         | String   | Y                | Operating system, whose value is "Android" or "iOs" |
| imei       | String   | Y                | Mobile IMEI number                                  |
| romVersion | String   | Y                | Android/ios OS version                              |
| appVersion | String   | Y                | App version                                         |

getThing description:

| **Name**   | **Type** | **Allows empty** | **Description**                                                                                        |
| :--------- | :------- | :--------------- | :----------------------------------------------------------------------------------------------------- |
| num        | Int      | Y                | The number of things to get. Default value, 30 will be used if not offered. 0 means to get all things. |
| beginIndex | Int      | Y                | The index of the item to begin to get. The default value,-9999999, will be used if not offered.        |

getMessage description:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                           |
| :------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------- |
| from     | Long     | Y                | Timestamp, accurate to milliseconds, from which to get earlier messages. The default is the current time. |
| num      | Int      | Y                | The maximum number of messages to obtained. 1<= num <= 30. If not offered, the default is 30.             |

Response data parameters:

| **Name**    | **Type** | **Allows empty** | **Description**                                                                            |
| :---------- | :------- | :--------------- | :----------------------------------------------------------------------------------------- |
| userInfo    | Object   | Y                | See the user description in the [Create an account] interface                              |
| familyInfo  | Object   | Y                | Please refer to the description of data response in the [Get home and room List] interface |
| thingInfo   | Object   | Y                | Refer to the description of data response in the [Get Thing List] interface                |
| sceneInfo   | Object   | Y                | Refer to the description of data response in the interface of [Get Scene List]             |
| messageInfo | Object   | Y                | Please refer to the description of data response in the [Get Notification List] interface  |

Client call example：

```json
{
  "lang": "cn",
  "clientInfo": {
    "model": "xxx"
  },
  "getUser": {},
  "getFamily": {},
  "getThing": {
    "num": 10
  },
  "getScene": {},

  "getMessage": {}
}
```

## Device

### Get the list of all devices (Please refer to get the ting list, get the specified Ting list and home page interface)

URL: None

Request method: GET

Authorization parameter: Token

Request parameter: none

Response data parameters:

| **Name**   | **Type**        | **Allows empty** | **Description** |
| :--------- | :-------------- | :--------------- | :-------------- |
| deviceList | Array\<Object\> | N                | Device list     |

List item description for deviceList:

| **Name**     | **Type**        | **Allows empty** | **Description**                                                                                           |
| :----------- | :-------------- | :--------------- | :-------------------------------------------------------------------------------------------------------- |
| name         | String          | N                | Device name                                                                                               |
| deviceid     | String          | N                | Device ID                                                                                                 |
| apikey       | String          | N                | The apikey of the device owner                                                                            |
| extra        | Object          | N                | The content in the extra field of factoryDevice                                                           |
| brandName    | String          | N                | Brand name                                                                                                |
| brandLogo    | String          | N                | Brand logo url                                                                                            |
| showBrand    | Boolean         | N                | Whether to display the brand                                                                              |
| productModel | String          | N                | Product model name                                                                                        |
| devGroups    | Array\<Object\> |  Y               | list of all the groups the device is in                                                                   |
| tags         | Object          | Y                | Tag object, which stores a custom string, and the server is only responsible for transparent transmission |
| devConfig    | Object          | Y                | Device configuration from deviceConfig in the factorydevices list                                         |
| settings     | Object          | Y                | User settings. Please refer to [Change device settings] interface description.                            |
| family       | Object          | N                | Home of the device                                                                                        |
| sharedBy     | Object          | Y                | If the device is shared by others, it will have this attribute.                                           |
| shareTo      | Array\<Object\> | Y                | The list of shared user with whom the device has been shared                                              |
| devicekey    | String          | N                | Factory apikey of the device                                                                              |
| online       | Boolean         | N                | Online status                                                                                             |
| params       | Object          | Y                | Status attributes of device                                                                               |
| gsmInfoData  | Object          | Y                | Sim card status object of GSM device                                                                      |

extra description：

| **Name**     | **Type** | **Allows empty** | **Description**  |
| :----------- | :------- | :--------------- | :--------------- |
| model        | String   | N                | Firmware name    |
| ui           | String   | N                | UI name          |
| uiid         | Int      | N                | UI ID            |
| description  | String   | N                | Factory notes    |
| manufacturer | String   | N                | manufacturer     |
| mac          | String   | N                | mac              |
| apmac        | String   | N                | ap mac           |
| modelInfo    | String   | N                | Product model ID |
| brandId      | String   | N                | Brand ID         |


settings description:

| **Name**    | **Type** | **Allows empty** | **Description**                                                                            |
| :---------- | :------- | :--------------- | :----------------------------------------------------------------------------------------- |
| opsNotify   | Int      | Y                | Whether to notify the user of device status change (default 0) 0=no 1=yes                  |
| opsHistory  | Int      | Y                | Whether to save activity logs of the device (default 1) 0=no 1=yes                         |
| alarmNotify | Int      | Y                | Whether to send alerts from sensors or alarms to the user (default 1) 0=Do not send 1=Send |

devGroups description:

| **Name** | **Type** | **Allows empty** | **Description**           |
| :------- | :------- | :--------------- | :------------------------ |
| type     | Int      | N                | 1 represents device group |
| groupId  | String   | N                | Group ID                  |

sharedBy list item description:

| **Name**    | **Type** | **Allows empty** | **Description**                                                                                              |
| :---------- | :------- | :--------------- | :----------------------------------------------------------------------------------------------------------- |
| apikey      | String   | N                | Unique identity of the user to which the device belongs (currently using symmetric encryption of the string) |
| phoneNumber | String   | Y                | Mobile number of the device owner                                                                            |
| email       | String   | Y                | Email of the device owner                                                                                    |
| nickname    | String   | Y                | Nickname of the device owner                                                                                 |
| permit      | Int      | N                | User's permission value, default is 0                                                                        |
| comment     | String   | Y                | Note of sharing                                                                                              |
| shareTime   | Long     | Y                | GMT standard time, in milliseconds, used to order sharing in app                                             |

shareTo list item description:

| **Name**    | **Type** | **Allows empty** | **Description**                                                                                                             |
| :---------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------------------------- |
| apikey      | String   | Y                | ID identification of the user account shared by the receiving device (symmetric encryption of the string is currently used) |
| email       | String   | Y                | Email of the device owner                                                                                                   |
| nickname    | String   | Y                | Nickname of the device owner                                                                                                |
| shareTime   | Long     | Y                | GMT standard time, in milliseconds, used to order sharing in app                                                            |
| phoneNumber | String   | Y                | Mobile number of the device owner                                                                                           |
| comment     | String   | Y                | Note of sharing                                                                                                             |
| permit      | Int      | N                | User's permission value, default is 0                                                                                       |

devConfig description (camera)：

| **Name**      | **Type** | **Allows empty** | **Description** |
| :------------ | :------- | :--------------- | :-------------- |
| p2pServerName | String   | Y                | Server Name     |
| p2pAccout     | String   | Y                | Account         |
| p2pLicense    | String   | Y                | License         |

family description：

| **Name** | **Type** | **Allows empty** | **Description**                       |
| :------- | :------- | :--------------- | :------------------------------------ |
| familyid | String   | N                | Home ID                               |
| index    | Int      | N                | Device index, which could be negative |
| roomid   | String   | Y                | Room ID of the device                 |

### Get Thing List

Note:

- When the user device (total parameter) exceeds 30, you need to set the beginIndex parameter to get it in pages, otherwise too much data will be acquired and the server will return timeout errors such as 500.
- The total parameter returned may be greater than the total amount of device data returned, which indicates that not all device data has been obtained. The specific reason is: at present, we only authorize the brands of Sonoff and CoolKit. The brands of other manufacturers can only be used after signing a letter of authorization with the help of our business colleagues. See the chapter "APICenterV2 - > Requirements of Calling Interface (Important)" for details.
- If multiple eWeLink accounts need to be used because of business relationships, but there are no resources to establish multiple long connections, it is recommended to share the devices of other accounts with a specific eWeLink account, and then establish a WebSocket connection for this account to passively receive messages and reduce interface call polling.

URL: /v2/device/thing

Request method: GET

Authorization parameter: Token

Description: Thing could be

- a device (owned by yourself or shared by others)
- a device group

Request parameters:

| **Name**   | **Type** | **Allows empty** | **Description**                                                                                            |
| :--------- | :------- | :--------------- | :--------------------------------------------------------------------------------------------------------- |
| lang       | String   | Y                | cn returns Chinese, and en returns English, default en                                                     |
| familyid   | String   | Y                | Home ID. Default is the current home                                                                       |
| num        | Int      | Y                | The number of things to get. The default value, 30 will be used if not offered. 0 means to get all things. |
| beginIndex | Int      | Y                | The index of the item to begin to get. The default value,-9999999, will be used if not offered.            |

Response data parameters:

| **Name**  | **Type** | **Allows empty** | **Description**                                |
| :-------- | :------- | :--------------- | :--------------------------------------------- |
| thingList | Array    | N                | Thing list                                     |
| total     | Int      | N                | Total number of things (device + device group) |

List items of thingList

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                                                                                                                                                        |
| :------- | :------- | :--------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| itemType | Int      | N                | Item type 1=user’s own device 2=device shared by others 3=user's own group                                                                                                                                                                             |
| itemData | Object   | N                | The structures of this field differs from itemType. When itemType is 1 or 2, refer to the description for device list item in [Get the list of all devices] interface. For 3, see the description of groupList item in the [Get group list] interface. |
| index    | Int      | N                | Sequence number                                                                                                                                                                                                                                        |

### Get Specified Things list

URL: /v2/device/thing

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name**  | **Type** | **Allows empty** | **Description**                                                                                   |
| :-------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------ |
| thingList | Array    | N                | The total number of things in the list to get must be greater than 0 and less than or equal to 10 |

thingList items:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                             |
| :------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------------------------- |
| itemType | Int      | N                | Item type 1=user’s own device 2=device shared by others 3=user's own group                                                  |
| id       | String   | N                | The ID of the corresponding thing. When itemType is 1 or 2, thing ID means deviceid. For 3 or 4, this field means group ID. |

Response data parameters:

| **Name**  | **Type** | **Allows empty** | **Description**                                                 |
| :-------- | :------- | :--------------- | :-------------------------------------------------------------- |
| thingList | Array    | N                | Thing list. Please refer to the description in [Get Thing list] |

### Get Device or Group Status

It is recommended to use WebSocket connect passive receiving device status update. Reduce polling and avoid frequent requests for this interface.

URL: /v2/device/thing/status

Request method: GET

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                    |
| :------- | :------- | :--------------- | :------------------------------------------------- |
| type     | Int      | N                | Whether to get device or group. 1=device 2=group   |
| id       | String   | N                | When type=1, this means deviceid. For 2, group ID. |
| params   | String   | Y                | Status parameters to be obtained                   |

**params description**

The caller can specify to obtain only the status parameters that are of interest, which should be separated by "|", and then perform url conversion.

Example: You want to get the switch and light status of a device.

1. Create the string 'switch|light'
2. Perform url conversion on the string of (1) to get the string 'switch%7Clight', which is the value of the params to send to the interface.

If you want to get all the status of the device or group, the params should be empty.

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                   |
| :------- | :------- | :--------------- | :-------------------------------- |
| params   | Object   | N                | Device or group status attributes |

### Update the Status of a Device or Group

It is recommended to use WebSocket connect to issue control commands.

URL: /v2/device/thing/status

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                    |
| :------- | :------- | :--------------- | :------------------------------------------------- |
| type     | Int      | N                | To update a device or a group. 1=device 2=group    |
| id       | String   | N                | When type=1, this means deviceid. For 2, group ID. |
| params   | Object   | N                | The status parameters to be updated                |

**params description**

- When you update a device, a control command will be sent to the device. If the device is offline or sending fails, an error will be returned.
- When you update a group, the server will send a control command to all the devices in the group and ignore any devices being offline or sending failure.

Response data parameter: None

### Update the Status of Multiple Devices or Groups

Description: This interface will actually send control commands directly to the device, which is dedicated to devices that cannot be updated via a persistent connection.

URL: /v2/device/thing/batch-status

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name**  | **Type**        | **Allows empty** | **Description**                                                                                                                                                                                    |
| :-------- | :-------------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| thingList | Array\<Object\> | N                | The list of things to update, of which the length should be greater than 0 and less than or equal to 10. The client must ensure that the ID in the list are unique, otherwise an error will occur. |
| timeout   | Int             | Y                | The time to wait for all devices to respond, in milliseconds, 0 <= timeout <= 8000. if not offered, the default is 0, which means to respond immediately.                                          |

Items in the thingList:

| **Name** | **Type** | **Allows empty** | **Description**                                    |
| :------- | :------- | :--------------- | :------------------------------------------------- |
| type     | Int      | N                | To update devices or groups. 1=device 2=group      |
| id       | String   | N                | When type=1, this means deviceid. For 2, group ID. |
| params   | Object   | N                | Status parameter to be updated                     |

Response data parameter：

| **Name** | **Type**        | **Allows empty** | **Description**                   |
| :------- | :-------------- | :--------------- | :-------------------------------- |
| respList | Array\<Object\> | N                | List of responses from all things |

Items in the respList:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                                   |
| :------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| type     | Int      | N                | To update devices or groups. 1=device 2=group                                                                                     |
| id       | String   | N                | When type=1, this means deviceid. For 2, group ID.                                                                                |
| error    | Int      | N                | Response error code, 0 means no error. If type=2, error is fixed to 0. If timeout is 0 when calling, error is fixed to 0 as well. |

### Add WiFi Device

URL: /v2/device/add

Request method: POST

Authorization parameter: Token

Description: Add regular WiFi devices

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                                                   |
| :------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------ |
| name     | String   | N                | Device name                                                                                                                                        |
| deviceid | String   | N                | Device ID                                                                                                                                         |
| settings | Object   | Y                | If there are no user settings, use the default values.                                                                                            |
| ifrCode  | String   | Y                | Code value of infrared device                                                                                                                     |
| digest   | String   | N                | The lowercase string of Hash SHA256(deviceid+device apikey)                                                                                       |
| chipid   | String   | N                | Chip ID of the device                                                                                                                             |
| familyid | String   | Y                | The home ID of the device. When this field is empty, the device will be added to the current home.                                                |
| roomid   | String   | Y                | The ID of the room to which the device belongs. If it is empty, the device will be added to [Unallocated].                                        |
| sort     | Int      | Y                | The way to assign a sequence number to a new device. If this field is empty, the default is 1. 1=smaller sequence number 2=larger sequence number |

digest algorithm:

Example: 123 Hash SHA256 result: a665a45920422f9d417e4867efdc4fb8a04a1f3fff1fa07e998e86f7f7a27ae3

settings description:

| **Name**    | **Type** | **Allows empty** | **Description**                                                                            |
| :---------- | :------- | :--------------- | :----------------------------------------------------------------------------------------- |
| opsNotify   | Int      | Y                | Whether to notify the user of device status change (default 0) 0=no 1=yes                  |
| opsHistory  | Int      | Y                | Whether to save activity logs of the device (default 1) 0=no 1=yes                         |
| alarmNotify | Int      | Y                | Whether to send alerts from sensors or alarms to the user (default 1) 0=Do not send 1=Send |

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                         |
| :------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------ |
| itemType | Int      | N                | The type of item, which is fixed to 1 here.                                                             |
| itemData | Object   | N                | Please refer to the description of the deviceList items in the [Get the list of all devices] interface. |
| index    | Int      | N                | Sequence number                                                                                         |

Note: In case that error code 30017 is returned, the reason is that the brand of this device has yet give authorization to your appid. Currently, authorization from brands owned by CoolKit is free. However, authorizations of other brands are retained by the device maker. To learn more about the brand authorization, please consult the salesperson from our company in the related WeChat groups.

```json
{
  "error": 30017,
  "msg": "this app does not support of adding this brand and its device",
  "data": {}
}
```

### Add GSM Device

URL: /v2/device/add-gsm

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                                                                                                                |
| :------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id       | String   | N                | Get the gsmId of the device from the QR code URL on the scanning device. The URL format is: https://api.coolkit.cc:8080/api/user/device/addGsm?id=348512d49379bb0acace4598e14fc450, ID is the latter parameter |
| name     | String   | N                | Device name                                                                                                                                                                                                    |
| familyid | String   | Y                | The home ID of the device. When this field is empty, the device will be added to the current home.                                                                                                             |
| roomid   | String   | Y                | The ID of the room to which the device belongs. If it is empty, the device will be added to [Unallocated].                                                                                                     |
| sort     | Int      | Y                | The way to assign a sequence number to a new device. If this field is empty, the default is 1. 1=smaller sequence number 2=larger sequence number                                                              |

Note: The application scans the QR code on the device to obtain a URL format string. Please note that the domain name may be changed, but "/addGsm?id={gsmId}" will not change here.

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                         |
| :------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------ |
| itemType | Int      | N                | The type of item, which is fixed to 1 here.                                                             |
| itemData | Object   | N                | Please refer to the description of the deviceList items in the [Get the list of all devices] interface. |
| index    | Int      | N                | Sequence number                                                                                         |

Response data parameters:

| **Name**  | **Type** | **Allows empty** | **Description**                                                                                                                                                 |
| :-------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| thingList | Array    | N                | List of devices that have been added successfully. Since multiple devices may be added simultaneously when adding third-party devices, a list is returned here. |

Items in the thingList:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                         |
| :------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------ |
| itemType | Int      | N                | The type of item, which is fixed to 1 here.                                                             |
| itemData | Object   | N                | Please refer to the description of the deviceList items in the [Get the list of all devices] interface. |
| index    | Int      | N                | Sequence number                                                                                         |

### Update Name/Room of Device

URL: /v2/device/update-info

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                             |
| :------- | :------- | :--------------- | :------------------------------------------ |
| deviceid | String   | N                | Device ID                                   |
| name     | String   | Y                | Device name                                 |
| roomid   | String   | Y                | ID of the room in which the device located. |

Response data parameter: None

### Delete Device

URL: /v2/device

Request method: DELETE

Authorization parameter: Token

Note: Deleting devices shared by others is also done through this interface.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                 |
| :------- | :------- | :--------------- | :------------------------------ |
| deviceid | String   | N                | ID of the device to be deleted. |

Response data parameter: None

### Change Device Tags

This endpoint can be used to change the names of sub-channels or realize some special functions based on your own ideas.

URL: /v2/device/tags

Request method: POST

Authorization parameter: Token

Note: The complete tags object needs to be passed. and the server will overwrite all the original values.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                     |
| :------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------- |
| deviceid | String   | N                | Device ID                                                                                           |
| type     | String   | Y                | The type of modification. If not offered, the default is 'replace'. replace=overwrite, merge=merge. |
| tags     | Object   | N                | Device tags                                                                                         |

For example, let's assumes that the original label of the device is as follows,

```json
{ "key1": "value1", "key2": "value2" }
```

When 'type=replace', tags is {"key3":"value3"}, the updated tag will be:

```json
{ "key3": "value3" }
```

When type=merge and tag is {"key3":"value3"}, the updated tag will be:

```json
{ "key1": "value1", "key2": "value2", "key3": "value3" }
```

Response data parameters:

| **Name**     | **Type** | **Allows empty** | **Description**                      |
| :----------- | :------- | :--------------- | :----------------------------------- |
| updatedThing | Object   | N                | The thing data of the updated device |

### Get Group List

URL: /v2/device/group

Request method: GET

Authorization parameter: Token

Note:

1. Groups are sorted in parallel with devices.
2. This endpoint only returns the list of groups in the current home.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                        |
| :------- | :------- | :--------------- | :----------------------------------------------------- |
| lang     | String   | Y                | cn returns Chinese, and en returns English, default en |

Response data parameters:

| **Name**  | **Type** | **Allows empty** | **Description** |
| :-------- | :------- | :--------------- | :-------------- |
| groupList | Array    | N                | Group list      |

List items of GroupList

| **Name** | **Type** | **Allows empty** | **Description**                             |
| :------- | :------- | :--------------- | :------------------------------------------ |
| itemType | Int      | N                | The type of item, which is fixed to 3 here. |
| itemData | Object   | N                | Group information                           |
| index    | Int      | N                | Sequence number                             |

itemData description:

| **Name**     | **Type** | **Allows empty** | **Description**                    |
| :----------- | :------- | :--------------- | :--------------------------------- |
| id           | String   | N                | Group ID                           |
| name         | String   | N                | Group name                         |
| mainDeviceId | String   | N                | The ID of main device in the group |
| family       | Object   | N                | Group home settings                |
| params       | Object   | N                | Group status                       |

family description:

| **Name** | **Type** | **Allows empty** | **Description**                                                    |
| :------- | :------- | :--------------- | :----------------------------------------------------------------- |
| familyid | String   | N                | Home ID                                                            |
| index    | Int      | N                | The sequence number of the group, which could be a negative number |
| roomid   | String   | Y                | The ID of the room to which the group is assigned                  |

### Add Group

URL: /v2/device/group

Request method: POST

Authorization parameter: Token

Note: If you use a device shared by others as the main device to add a group, the group will be deleted when the sharing is canceled.

Request parameters:

| **Name**     | **Type** | **Allows empty** | **Description**                                                                                          |
| :----------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------- |
| name         | String   | N                | Group name, The maximum length is 50 characters                                                          |
| mainDeviceId | String   | N                | The ID of main device in the group                                                                       |
| familyid     | String   | Y                | The home ID of the group. When this field is empty, the group will be added to the current home.         |
| roomid       | String   | Y                | The ID of the room to which the group belongs. If it is empty, the group will be added to [Unallocated]. |
| sort         | Int      | Y                | The way to assign sequence number to the new group. 1=smaller sequence number 2=larger sequence number   |

Response data parameters:

| **Name**         | **Type**        | **Allows empty** | **Description**                                                                |
| :--------------- | :-------------- | :--------------- | :----------------------------------------------------------------------------- |
| itemType         | Int             | N                | The type of item, which is fixed to 3 here.                                    |
| itemData         | Object          | N                | Refer to the description of itemData in [Get group list] interface.            |
| index            | Int             | N                | Sequence number                                                                |
| updatedThingList | Array\<Object\> | N                | The thing list of the updated devices, including the main device of the group. |

### Change Group Name

URL: /v2/device/group

Request method: PUT

Authorization parameter: Token

Note: Currently this interface can only modify the name of the group.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                         |
| :------- | :------- | :--------------- | :------------------------------------------------------ |
| id       | String   | N                | Group ID                                                |
| name     | String   | N                | The new group name, The maximum length is 50 characters |

Response data parameter: None

### Delete Group

URL: /v2/device/group

Request method: DELETE

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description** |
| :------- | :------- | :--------------- | :-------------- |
| id       | String   | N                | Group ID        |

Response data parameter: None

### Change Group Status

URL: /v2/device/group/status

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                 |
| :------- | :------- | :--------------- | :-------------------------------------------------------------- |
| id       | String   | N                | Group ID                                                        |
| params   | Object   | N                | Group status. This interface only saves data without processing |

Response data parameter: None

### Update the Device List of a Group

URL: /v2/device/group/update

Authorization parameter: Token

Description: This interface will overwrite all the devices in the group according to the passed device list.

Request method：POST

Request parameters:

| **Name**     | **Type**        | **Allows empty** | **Description**                                                                                        |
| :----------- | :-------------- | :--------------- | :----------------------------------------------------------------------------------------------------- |
| id           | String          | N                | Group ID                                                                                               |
| deviceidList | Array\<String\> | N                | The device ID list must contain the group’s main device at least, otherwise an error will be returned. |

Response data parameter：

| **Name**         | **Type** | **Allows empty** | **Description**                        |
| :--------------- | :------- | :--------------- | :------------------------------------- |
| updatedThingList | Array    | N                | The thing list of the updated devices. |

### Share Devices

URL: /v2/device/share

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name**     | **Type**      | **Allows empty** | **Description**                                                                                                                                                      |
| :----------- | :------------ | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceidList | Array<String> | N                | Device ID list                                                                                                                                                       |
| user         | Object        | N                | User info                                                                                                                                                            |
| permit       | Int           | N                | The sum of permission values, calculated by displacement. Definitions of permission values are :1：Create new timer; 2：Edit timer; 4：Delete timer; 8：Enable timer |
| comment      | String        | Y                | Sharing note                                                                                                                                                         |
| shareType    | Int           | Y                | Sharing method. If not offered, the default is 1. 1=silent sharing, without the consent of the user being shared.                                                    |

user description：

| **Name**    | **Type** | **Allows empty** | **Description**                                                                                 |
| :---------- | :------- | :--------------- | :---------------------------------------------------------------------------------------------- |
| countryCode | String   | Y                | Area Code, which is required when phoneNumber is used.                                          |
| phoneNumber | String   | Y                | The user’s mobile number must start with the country code, such as "+86".                       |
| email       | String   | Y                | User email. Either phone number or email is required. Phone number will be checked in priority. |

Response data parameters:

| **Name**         | **Type** | **Allows empty** | **Description**                                                                                                              |
| :--------------- | :------- | :--------------- | :--------------------------------------------------------------------------------------------------------------------------- |
| updatedThingList | Array    | N                | The updated thing list of the shared devices. See [Add device] for data response, containing the information of shared user. |

Note: post /v2/device/share will return the other party's apikey parameters, which can be written down and used in post /v2/device/share/permit and delete /v2/device/share.

### Change Sharing Permission

URL: /v2/device/share/permit

Request method：POST

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                             |
| :------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------------------------- |
| deviceid | String   | N                | Device ID                                                                                                                   |
| apikey   | String   | N                | ID identification of the user account shared by the receiving device (symmetric encryption of the string is currently used) |
| permit   | Int      | N                | Updated sharing permissions. See [Device sharing] endpoint for details.                                                     |

Note: The apikey parameter comes from the detailed information of the device. Please search for the parameter shareTo in the document.

Response data parameters:

| **Name**     | **Type** | **Allows empty** | **Description**                                                                                                       |
| :----------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------------------- |
| updatedThing | Array    | N                | The updated thing of the devices. See [Add device] interface for response, containing the information of shared user. |

### Cancel Sharing

URL: /v2/device/share

Request method：DELETE

Authorization parameter: Token

Request parameter：

| **Name** | **Type** | **Allows empty** | **Description**                                |
| :------- | :------- | :--------------- | :--------------------------------------------- |
| deviceid | String   | N                | Device ID                                      |
| apikey   | String   | N                | Apikey of the user to unshare the device with. |

Response data parameters:

| **Name**     | **Type** | **Allows empty** | **Description**                                                                                                       |
| :----------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------------------- |
| updatedThing | Array    | N                | The updated thing of the devices. See [Add device] interface for response, containing the information of shared user. |

### Get Device Operating History

URL: /v2/device/history

Request method: GET

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                        |
| :------- | :------- | :--------------- | :----------------------------------------------------------------------------------------------------- |
| deviceid | String   | N                | Device ID                                                                                              |
| from     | Long     | Y                | Timestamp, accurate to milliseconds. The time from which to get logs. The default is the current time. |
| num      | Int      | Y                | The maximum number of logs to obtained. 1<= num <= 30. If not offered, the default is 30.              |

Response data parameters:

| **Name**  | **Type** | **Allows empty** | **Description**                  |
| :-------- | :------- | :--------------- | :------------------------------- |
| histories | Array    | N                | The list of device activity logs |

histories item description:

| **Name**   | **Type** | **Allows empty** | **Description**                                                                                                                                                |
| :--------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceid   | String   | N                | Device ID                                                                                                                                                      |
| userAgent  | String   | Y                | Used to distinguish whether the action is done in the app or on the device.                                                                                    |
| opsSwitchs | String   | Y                | The channels of the device that have performed actions in the log. If the device has only one channel, then there is only one element whose value is "switch". |
| request    | String   | N                | Original request                                                                                                                                               |
| opsAccount | String   | Y                | If the action was requested in the app, the account of the requesting user (who may also be a shared user) will be returned.                                   |
| opsTime    | Long     | N                | Timestamp of the action, accurate to milliseconds.                                                                                                             |

### Clean Device Operating History

URL: /v2/device/history

Request method: DELETE

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description** |
| :------- | :------- | :--------------- | :-------------- |
| deviceid | String   | N                | Device ID       |

Response data parameter: None

### Get Device OTA Update Information

URL: /v2/device/ota/query

Request method：POST

Authorization parameter: Token

Request parameters

| **Name**       | **Type**        | **Allows empty** | **Description**                                                                                         |
| :------------- | :-------------- | :--------------- | :------------------------------------------------------------------------------------------------------ |
| deviceInfoList | Array\<Object\> | N                | List of devices to check. The length of the list should be greater than 0 and less than or equal to 30. |

deviceInfoList items:

| **Name** | **Type** | **Allows empty** | **Description**                            |
| :------- | :------- | :--------------- | :----------------------------------------- |
| deviceid | String   | N                | Device ID                                  |
| model    | String   | N                | Module model of the device                 |
| version  | String   | N                | The firmware version of the current device |

Response data parameter：

| **Name**    | **Type**        | **Allows empty** | **Description**                                                                              |
| :---------- | :-------------- | :--------------- | :------------------------------------------------------------------------------------------- |
| otaInfoList | Array\<Object\> | N                | List of new firmwares. Any new firmware available for upgrade will be included in this list. |

otaInfoList items:

| **Name**  | **Type**        | **Allows empty** | **Description**         |
| :-------- | :-------------- | :--------------- | :---------------------- |
| deviceid  | String          | N                | Device ID               |
| version   | String          | N                | Latest firmware version |
| binList   | Array\<Object\> | N                | List of bin files       |
| type      | String          | N                | (reserved word)         |
| forceTime | String          | N                | (reserved word)         |

binList items:

| **Name**    | **Type** | **Allows empty** | **Description**                              |
| :---------- | :------- | :--------------- | :------------------------------------------- |
| name        | String   | N                | The name of the file available for download. |
| downloadUrl | String   | N                | Download URL                                 |
| digest      | String   | Y                | HASH digest of the file(SHA256)              |

Firmware upgrade:

After the app obtains the firmware information, it displays a message to notify the user of new firmware available. As soon as the user taps the upgrade button, and the app should issue an OTA command through the persistent connection:

```json
{
  "action": "upgrade",
  "deviceid": "device ID",
  "apikey": "User APIKEY",
  "userAgent": "app",
  "sequence": "timestamp in milliseconds",
  "params": {
    "model": "Device Model",
    "version": "firmware version to upgrade to",
    "binList": [
      {
        "downloadUrl": " Bin file 1 download URL",
        "digest": "File HASH digest (SHA256)",
        "name": "user1.bin"
      },
      {
        "downloadUrl": "bin file 2 download URL",
        "digest": "File HASH digest (SHA256)",
        "name": "user2.bin"
      }
    ]
  }
}
```

When the device confirms that the file is fine, it will respond (based on different firmware version, it may not respond but rather disconnect and download OTA directly):

```json
{
  "userAgent": "device",
  "apikey": "User APIKEY",
  "deviceid": "device ID",
  "error": 0,
  "sequence": " timestamp in millisecond (same as what is sent by app)"
}
```

Then the app prompts "Upgrade in progress" (unable to confirm the real OTA progress) and save the information of the original firmware version. In the process of device OTA upgrade, the device will reboot. After rebooting, it will report the new firmware version. When the app receives the new version, it compares with the original version. If the new is greater than the old, then firmware upgrade is successful, otherwise failure occured.

## Homes and Rooms

### Get Homes and Rooms

URL: /v2/family

Request method: GET

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                        |
| :------- | :------- | :--------------- | :----------------------------------------------------- |
| lang     | String   | Y                | cn returns Chinese, and en returns English, default en |

Response data parameters:

| **Name**        | **Type** | **Allows empty** | **Description**            |
| :-------------- | :------- | :--------------- | :------------------------- |
| familyList      | Array    | N                | Home list                  |
| currentFamilyId | String   | N                | The ID of the current home |

FamilyList items:

| **Name** | **Type** | **Allows empty** | **Description**                                       |
| :------- | :------- | :--------------- | :---------------------------------------------------- |
| id       | String   | N                | Home ID                                               |
| apikey   | String   | N                | User apikey                                           |
| name     | String   | N                | Home name                                             |
| index    | Int      | N                | Sequence number of the home, which could be negative. |
| roomList | Array    | Y                | Room list                                             |

RoomList items:

| **Name** | **Type** | **Allows empty** | **Description**                                       |
| :------- | :------- | :--------------- | :---------------------------------------------------- |
| id       | String   | N                | Room ID                                               |
| name     | String   | N                | Room name                                             |
| index    | Int      | N                | Sequence number of the room, which could be negative. |

### Add a Home

URL: /v2/family

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name**     | **Type** | **Allows empty** | **Description**                                                                                           |
| :----------- | :------- | :--------------- | :-------------------------------------------------------------------------------------------------------- |
| name         | String   | N                | Home name                                                                                                 |
| sort         | Int      | N                | The way to assign sequence number to the home. 1=smaller sequence number 2=larger sequence number         |
| roomNameList | Array    | Y                | List of room names. The server will create and sort rooms in the home based on the sequence of this list. |

Response data parameters:

| **Name** | **Type**        | **Allows empty** | **Description**                                                                                    |
| :------- | :-------------- | :--------------- | :------------------------------------------------------------------------------------------------- |
| id       | String          | N                | Home ID                                                                                            |
| name     | String          | N                | Home name                                                                                          |
| index    | Int             | N                | Sequence number of home                                                                            |
| roomList | Array\<Object\> | Y                | For the room list, please refer to the description of [Get the list of homes and rooms] interface. |

### Add a Room

URL: /v2/family/room

Request method: POST

Authorization parameter: Token

Note: 100 rooms can be added to each home at most.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                   |
| :------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------ |
| familyid | String   | N                | Home ID to which the room belongs                                                                 |
| name     | String   | N                | Room name                                                                                         |
| sort     | Int      | N                | The way to assign sequence number to the room. 1=smaller sequence number 2=larger sequence number |

Response data parameters:

| **Name** | **Type** | **Allows empty** | **Description**             |
| :------- | :------- | :--------------- | :-------------------------- |
| id       | String   | N                | Room ID                     |
| name     | String   | N                | Room name                   |
| index    | Int      | N                | Sequence number of the room |

### Change Home Name

URL: /v2/family

Request method: PUT

Authorization parameter: Token

Note: Currently this endpoint can only change home name.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                               |
| :------- | :------- | :--------------- | :------------------------------------------------------------ |
| id       | String   | Y                | Home ID, if not offered, it means to modify the current home. |
| name     | String   | N                | New home name                                                 |

Response data parameter: None

### Change Room Name

URL: /v2/family/room

Request method: PUT

Authorization parameter: Token

Note: Currently this endpoint can only change room name.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description** |
| :------- | :------- | :--------------- | :-------------- |
| id       | String   | N                | Room ID         |
| name     | String   | N                | New room name   |

Response data parameter: None

### Sort Rooms

URL: /v2/family/room/index

Request method: POST

Authorization parameter: Token

Note: The client must pass all the rooms in the home to sort them as a whole.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                                                          |
| :------- | :------- | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------- |
| familyid | String   | Y                | Home ID, if not offered, it means to modify the current home.                                                                                            |
| idList   | Array    | N                | List of room IDs. The server sort room IDs based on their sequence numbers. For example, the room with sequence number, 0 will be in the poisition of 0. |

Response data parameter: None

### Delete Home

URL: /v2/family

Request method: DELETE

Authorization parameter: Token

Request parameters:

| **Name**     | **Type** | **Allows empty** | **Description**                                                                         |
| :----------- | :------- | :--------------- | :-------------------------------------------------------------------------------------- |
| id           | String   | N                | Home ID                                                                                 |
| deviceFamily | String   | N                | The ID of the new home to which the things will be moved after current home is deleted. |
| switchFamily | String   | N                | The ID of the home to switch to after current home is deleted.                          |

Response data parameter: None

### Delete Room

URL: /v2/family/room

Request method: DELETE

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description** |
| :------- | :------- | :--------------- | :-------------- |
| id       | String   | N                | Room ID         |

Response data parameter: None

### Sort Things in a Home

URL: /v2/family/thing/sort

Request method: POST

Authorization parameter: Token

Note: The client must pass all devices and groups in the home to sort them all as a whole.

Request parameters:

| **Name**  | **Type**        | **Allows empty** | **Description**                                                                                                                                                                          |
| :-------- | :-------------- | :--------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| familyid  | String          | Y                | Home ID. If not offered, the device and groups of the current home will be sorted.                                                                                                       |
| thingList | Array\<Object\> | N                | Thing list. The server sorts the IDs of the things in the home based on their sequence numbers. For example, a thing/device of the sequence number, 0, will be put in the position of 0. |

thingList items:

| **Name** | **Type** | **Allows empty** | **Description**                                                            |
| :------- | :------- | :--------------- | :------------------------------------------------------------------------- |
| itemType | Int      | N                | Item type 1=user’s own device 2=device shared by others 3=user's own group |
| id       | String   | N                | Device ID/Group ID                                                         |

Response data parameter: None

### Move things

URL: /v2/family/room/thing

Request method: POST

Authorization parameter: Token

Explanation: The client passes in the original thing list and the adjusted thing list in the room, and the server calculates the things to be deleted from the room and the things to be added to the room based on this.The client should ensure the correctness of the oldThingList. If there are any missing items, it may cause the deletion to fail. If one of the items does not belong to the room ID, the server will return an error.

Request parameters:

| **Name**     | **Type** | **Allows empty** | **Description**                                                                                                                                                                                                                      |
| :----------- | :------- | :--------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| roomid       | String   | N                | Room ID                                                                                                                                                                                                                              |
| oldThingList | Array    | N                | The thing list of the original room. If there are no things in the room, then an empty list [] is passed in. For the items of the list, please refer to the description of the thingList items in [Sort things in a home] interface. |
| newThingList | Array    | N                | The adjusted thing list of the room.                                                                                                                                                                                                 |

Response data parameter: None

### Switch Current Home

URL: /v2/family/current

Request method: POST

Authorization parameter: Token

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description** |
| :------- | :------- | :--------------- | :-------------- |
| id       | String   | N                | Home ID         |

Response data parameter: None

## Message Center

### Get the List of Messages

URL: /v2/message/read

Request method: GET

Authorization parameter: Token

Note: The list is sorted by time. If the client wants to obtain more data, it can call this interface again by adding the timestamp of the last item to the 'from' field.

Request parameters:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                         |
| :------- | :------- | :--------------- | :---------------------------------------------------------------------------------------------------------------------- |
| familyid | String   | Y                | Home ID. If left blank, it will default to the current home.                                                            |
| from     | Long     | Y                | Timestamp, accurate to milliseconds. The time from which to get notification messages. The default is the current time. |
| num      | Int      | Y                | The maximum number of messages to obtained. 1<= num <= 30. If not offered, the default is 30.                           |

Response data parameters:

| **Name**    | **Type** | **Allows empty** | **Description** |
| :---------- | :------- | :--------------- | :-------------- |
| messageList | Array    | N                | Message list    |

MessageList items:

| **Name** | **Type** | **Allows empty** | **Description**                                                                                                                                                                                                                                                              |
| :------- | :------- | :--------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| msgid    | String   | N                | Message ID                                                                                                                                                                                                                                                                   |
| msgType  | String   | N                | Message type. "shareNotify_v2": Share notification, "cancelShareNotify_v2": Cancel sharing notification, "opsNotify_v2": Device action notification, "pushNotify_v2": regular device push, "alarmNotify_v2": sensor/alarm alert push, "IOTCameraNotify_v2": IOT camera push. |
| message  | Object   | N                | Message content. The definition of this field differs from msgType.                                                                                                                                                                                                          |
| date     | Long     | N                | The timestamp of the message, accurate to milliseconds.                                                                                                                                                                                                                      |

Response data parameter: None

## Real Time Control Device

Complete process description:

The client (APP, applet, web page or other) requests to allocate a service interface and obtain the IP address + port for establishing the websocket.

Splicing WSS address: wss:// {domain or IP}:{port}/api/ws

After the connection is established, send websocket: handshake related parameters. After passing the authentication, the connection is successfully established, and then you can issue control instructions and report information to the receiving device or server.

### HTTP: DispatchService (APP)

Distributed address for persistent connection used by the app

- Mainland China: [https://cn-dispa.coolkit.cn/dispatch/app ](https://cn-dispa.coolkit.cn/dispatch/app)
- Americas: [https://us-dispa.coolkit.cc/dispatch/app ](https://us-dispa.coolkit.cc/dispatch/app)
- Europe: [https://eu-dispa.coolkit.cc/dispatch/app ](https://eu-dispa.coolkit.cc/dispatch/app)
- Asia: [https://as-dispa.coolkit.cc/dispatch/app ](https://as-dispa.coolkit.cc/dispatch/app)

Request method: GET

Authorization parameter: Token

Request parameters: none

Note: Please note that the domain name used for mainland China and the test region is coolkit **.cn** , while the domain name used in other regions is coolkit **.cc**

**Response parameters:**

| Name   | Type   | Allows empty | Description                                                                                                                                                                                                                                                                                                                      |
| :----- | :----- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IP     | string | N            | The IP address of the server for persistent connection                                                                                                                                                                                                                                                                           |
| port   | number | N            | The port of the server for persistent connection                                                                                                                                                                                                                                                                                 |
| domain | string | N            | The domain name of the persistent connection server.This domain name is used when the client establishes a long connection |
| error  | number | N            | "error:0": success                    |
| reason | string | N            | "OK": success                                                                                                                                                                                                                                                                                                                    |

Error code 0: success

**Response example:**

```json
{
  "port": 8080,
  "IP": "52.80.19.131",
  "reason": "ok",
  "domain": "cn-pconnect2.coolkit.cc",
  "error": 0
}
```

### WebSocket: handshake

The authorization happens when connection is established. There are two types of handshakes, respectively on client and device. This one is on the client.

Its parameters are as follows,

| Name      | Type   | Allows empty | Description                                       |
| :-------- | :----- | :----------- | :------------------------------------------------ |
| action    | string | N            | Fixed parameter: userOnline                       |
| at        | string | N            | AT obtained from the login interface              |
| apikey    | string | N            | User apikey (obtainable from the login interface) |
| appid     | string | N            | APPID                                             |
| nonce     | string | N            | 8-digit alphanumeric random string                |
| ts        | number | Y            | Timestamp accurate to seconds                     |
| userAgent | string | N            | Fixed parameter: app                              |
| sequence  | string | N            | Timestamp accurate to milliseconds                |
| version   | number | N            | Interface version: 8                              |

Example:

```json
{
  "action": "userOnline",
  "version": 8,
  "ts": 1571141259,
  "at": "AT obtained by login interface",
  "userAgent": "app",
  "apikey": "User APIKEY obtained by login interface",
  "appid": "McFJj4Noke1mGDZCR1QarGW7P9Ycp0Vr",
  "nonce": "2plz69ax",
  "sequence": "millisecond-level timestamp, example: 1571141530100"
}
// Need to remove space before compression, and do not incldue extra commas
```

**Response parameters:**

| Name     | Type   | Allows empty | Description                        |
| :------- | :----- | :----------- | :--------------------------------- |
| error    | number | N            | Error code                         |
| apikey   | string | N            | User apikey                        |
| config   | string | Y            | Configuration                      |
| sequence | string | N            | Timestamp accurate to milliseconds |

Config description:

| Name       | Type   | Allows empty | Description                                                                                                                                                                                               |
| :--------- | :----- | :----------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| hb         | number | Y            | Heartbeat, whether to send heartbeats to keep alive.0: No, 1: Yes                                                                                                                                         |
| hbInterval | number | Y            | Heartbeat interval, in seconds. The client needs to add 7 to this value as the interval to send keep the ping heartbeat alive.If it is not offered, the heartbeat interval will be 90 seconds by default. |

Error code

0: success

**Response example:**

```json
{
  "error": 0,
  "apikey": "User APIKEY",
  "config": {
    "hb": 1,
    "hbInterval": 145
  },
  "sequence": "Millisecond-level timestamp , Example: 1571141530100" // Same as sent
}
```

### WebSocket: device online and offline notification (passively received by the app)

When the server detects a device going online or offline, it will send a notification to the app. The notification is sent to the app passively. There is no need for the client to request actively.

Parameters:

| Name     | Type   | Allows empty | Description                                                                                                                                          |
| :------- | :----- | :----------- | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
| nonce    | string | N            | 8-digit alphanumeric random string                                                                                                                   |
| apikey   | string | N            | Current User apikey (available from the login interface) or the apikey of the master account (available from the interface for obtaining Thing list) |
| deviceid | string | N            | Device ID                                                                                                                                            |
| action   | string | N            | Fixed parameter: sysmsg                                                                                                                              |
| params   | object | N            | Parameters: {k:v}                                                                                                                                    |
| ts       | number | Y            | Timestamp accurate to seconds                                                                                                                        |

Example:

```json
{
  "action": "sysmsg",
  "deviceid": "1000000001",
  "apikey": "Current user APIKEY",
  "ts": 15452192511,
  "params": {
    "online": false
  }
}
```

### WebSocket: Update device status

**After device status changes and sends the 'update' command, as long as the client has a persistent connection, it will receive a notification. Therefore, it is recommended that the client keep the persistent connection alive to monitor device status or send queries to check the status of a single device, instead of checking device status periodically by requesting the HTTP interface, to reduce the burden on the server.**

This is to change the statuses of a device, such as timers, sharing, on/off, etc.

Parameters:

| Name      | Type   | Allows empty | Description                                                                                                                                                                                 |
| :-------- | :----- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| action    | string | N            | Fixed parameter: update                                                                                                                                                                     |
| apikey    | string | N            | Current user apikey (available from the login interface) or the apikey of the master account (available from the interface for obtaining Thing list)                                        |
| selfApikey    | string | Y       | Receiver's apikey. Required when the receiver updates its device status. It cannot be empty. |
| deviceid  | string | N            | Device ID                                                                                                                                                                                   |
| params    | object | N            | The server applies transparent transmission for the params, which may be an object or an array of objects. Just make sure you send the parameters of all the statuses you desire to change. |
| userAgent | string | N            | app or device                                                                                                                                                                               |
| sequence  | string | N            | Timestamp accurate to milliseconds                                                                                                                                                          |

Example:

```json
{
  "action": "update",
  "deviceid": "100000001",
  "apikey": "Current user APIKEY",
  "userAgent": "app",
  "sequence": "1585297259553",
  "params": {
    "switch": "on" // single-channel device
  }
}
```

If you update the device status shared by other users:

```json
{
  "action": "update",
  "deviceid": "100000001",
  "apikey": "APIKEY of the master account",
  "selfApikey":"Receiver's apikey",
  "userAgent": "app",
  "sequence": "1585297259553",
  "params": {
    "switch": "on" // single-channel device
  }
}
```

params description:

The details of this field come from the protocol document. Different devices have different protocols. For example, a single-channel switch has only one "switch" field, but a multi-channel device must have more than one "switch" fields. For the lamps, you can also adjust their color and brightness, which makes their parameters different as well.

Please consult your salesperson for the protocol document. If you intend to use the eWeLink app for an unsupported product( which has no existing UIs) , additional customization fee may apply. Please contact your salesperson for details.

**Response parameters:**

| Name     | Type   | Allows empty | Description                        |
| :------- | :----- | :----------- | :--------------------------------- |
| error    | number | N            | Error code                         |
| apikey   | string | Y            | User apikey                        |
| deviceid | string | Y            | Device ID                          |
| sequence | string | N            | Timestamp accurate to milliseconds |

Example:

```json
{
  "error": 0,
  "deviceid": "1000000001",
  "apikey": "***************",
  "sequence": "1585297259553"
}
```

Error code

504: The device does not respond (offline or command error)

**Timer settings**

In general, the device can add multiple timers. Every time a new timer is added, modified, or deleted, the timer array must be submitted in full.

For example, there are currently two timers, if you add another one, the submitted timer array must contain the data of the previous two timers in addition to the new timer.

Timers parameters:

| Name               | Type   | Allows empty | Description                                                                                                                                      |
| :----------------- | :----- | :----------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| enabled            | number | N            | Enabled or not: 0 means disabled; 1 means enabled                                                                                                |
| mId                | string | N            | Used to identify the timer, in UIID format.                                                                                                      |
| type               | string | N            | Timer type used by the device. "once": a non-repeating timer; "repeat": a repeating timer; "duration": a loop timer.                             |
| coolkit_timer_type | string | N            | Timer type used by the client. "once": a non-repeating timer; "repeat": a repeating timer; "duration": a loop timer; "delay": a countdown timer. |
| at                 | string | N            | Execution time: Greenwich Mean Time, or the UTC time can also be used.                                                                           |
| do                 | object | Y            | Action to be performed                                                                                                                           |
| startDo            | object | Y            | Dedicated to the loop timer: the action to be executed at the beginning of the loop.                                                             |
| endDo              | object | Y            | Dedicated to the loop timer: the action to alternate with the first action.                                                                      |
| period             | string | Y            | Dedicated to countdown timer: countdown duration, in minutes.                                                                                    |

Example:

Non-repeating timer, which executes once only.

```json
"params":{
        "timers":[
            {
                "enabled":1, //1 means enabled
                "mId":"c102f00f-db6f-fef0-f296-9dd10fdc2193", //random, for app to identify the timer
                "type":"once", //dedicated to device. "once" means non-repeating, "repeat" means repeating
                "at":"2017-07-24T08:28:00.000Z", //execution time, which is the GTM time, in 0 timezone.
                "do":{ //The action to be performed
                    "switch":"on" //It is the action to turn on the single-channel switch in this example.For multi-channel devices, the "switch" values of different channels should be placed here.
                },
                "coolkit_timer_type":"once" //app dedicated
            }
        ]
}
```

Repeating timer:

```json
"params":{
        "timers":[
            {
                "enabled":1,
                "mId":"847b296e-9043-ac94-ca37-aa5f91d22338",
                "type":"repeat", //a repeating timer
                "at":"36 8 * * 1,3",//For time expression, refer to "cron"
                "do":{
                    "switch":"on"
                },
                "coolkit_timer_type":"repeat" //repeat Execute
            }
        ]
}
```

Loop timer:

```json
"params":{
        "timers":[
            {
                "enabled":1,
                "mId":"847b296e-9043-ac94-ca37-aa5f91d22338",
                "type":"duration",
                "at" :"2018-11-21T10:24:00.980Z 10 5",//The time when the loop starts. Wait 10 minutes to take 1st action and wait 5 minutes to take 2nd action.
                "startDo":{
                    "switch":"on" //First execution of the loop
                },
                "endDo":{
                    "switch":"off" //Next execution
                },
                "coolkit_timer_type":"duration" //Keep repeating
            }
        ]
}
```

Countdown timer (This timer waits for specified minutes until the action is performed, which executes once only. The purpose of it is to set up a timer quickly.)

```json
"params":{
        "timers":[
            {
                "enabled":1,
                "mId":"95303c64-fbb4-f497-1341-c592432d1d0d",
                "type":"once",
                "at" :"2017-07-24T09:10:43.223Z",
                "do":{
                    "switch":"on"
                },
                "period":"30",
                "coolkit_timer_type":"delay" // countdown timer
            }
        ]
}
```

### WebSocket: check for device status

This is to check for the statuses of a device, such as timers, sharing, on/off, etc.

Parameters:

| Name      | Type   | Allows empty | Description                                                                                                                                  |
| :-------- | :----- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------- |
| action    | string | N            | Fixed parameter: query                                                                                                                       |
| apikey    | string | N            | User apikey (available from the login interface) or the apikey of the master account (available from the interface for obtaining Thing list) |
| deviceid  | string | N            | Device ID                                                                                                                                    |
| params    | array  | N            | String array, which specify the parameters to be checked for. If it is empty, all the parameteres of the device will be checked for.         |
| userAgent | string | N            | app or device                                                                                                                                |
| sequence  | string | N            | Timestamp accurate to milliseconds                                                                                                           |

Example:

```json
{
  "action": "query",
  "deviceid": "1000000001",
  "apikey": "User APIKEY",
  "sequence": "1585297259553",
  "params": ["switch", "timers "], // If the returned value is empty, you can use [] to query the statuses of all fields
  "from": "app",
  "userAgent": "app"
}
```

If you query the device status shared by other users:

```json
{
    "action":"query",
    "userAgent":"app",
    "apikey":"APIKEY of the master account",
    "deviceid":"1000000001",
    "params":["switch","timers"],
    "sequence":"1585297259553",
    "selfApikey":"Current user APIKEY"}
}
```

params description:

The details of this field come from the protocol document. Different devices have different protocols. For example, a single-channel switch has only one "switch" field, but a multi-channel device must have more than one "switch" fields. For the lamps, you can also adjust their color and brightness, which makes their parameters different as well.

Please consult your salesperson for the protocol document. If you intend to use the eWeLink app for an unsupported product( which has no existing UIs) , additional customization fee may apply. Please contact your salesperson for details.

**Response parameters:**

| Name     | Type   | Allows empty | Description                                                                           |
| :------- | :----- | :----------- | :------------------------------------------------------------------------------------ |
| error    | number | N            | Error code                                                                            |
| apikey   | string | N            | User apikey                                                                           |
| deviceid | string | N            | Device ID                                                                             |
| params   | object | N            | Parameters which will be passed transparently. The server will not verify this filed. |

Example:

```json
{
    "error":0,
    "deviceid":"1000000001",
    "apikey":"***************",
    "params":{
        "switch" :"on",
      ...
    }
}
```

## Error codes

### General error codes

| **Error code** | **Description**                                                                                                                                                                                               |
| :------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 400            | Parameter error, usually caused by the lack of some parameters required by the interface, or because the type or value of the parameter is wrong.                                                             |
| 401            | Authentication error with access token, usually happens when the account is logged in by someone else, causing the current access token to become invalid.                                                    |
| 402            | Access token expired.                                                                                                                                                                                         |
| 403            | Cannot find the interface, usually because the interface url is wrong.                                                                                                                                        |
| 405            | The resource cannot be found, usually because the required data cannot be found in the back-end database.                                                                                                     |
| 406            | Access denied. You do not have the permission to take this action or access this resource.                                                                                                                    |
| 407            | The appid has no permission for this action. |
| 412        | APPID calls exceed the limit, you can upgrade to the enterprise version by contacting bd@coolkit.cn. |
| 500            | Internal server error, usually due to errors on server programs.                                                                                                                                              |
| 4002       | Device control failure (Check control parameter transmission or device online status). |

### [User] error codes

| **Error code** | **Description**                                                      |
| :------------- | :------------------------------------------------------------------- |
| 10001          | Incorrect login password                                             |
| 10002          | Incorrect verification code                                          |
| 10003          | User does not exist.                                                 |
| 10004          | The user to log in is not in current region.                         |
| 10009          | You are creating an account for an existing user email/phone number. |
| 10010          | You are sending verification code too fast.                          |

### [Home and room] error codes

| **Error code** | **Description**                                                                        |
| :------------- | :------------------------------------------------------------------------------------- |
| 20001          | Failed to create a home for the first time.                                            |
| 20002          | You are creating more homes or rooms than you can with your current subscription plan. |
| 20003          | There is only one home in the account, so the server refused to delete it.             |

### [Device] error codes

| **Error code** | **Description**                                                                                               |
| :------------- | :------------------------------------------------------------------------------------------------------------ |
| 30003          | Failed to notify the device to disconnect from the temporary persistent connection, when adding a GSM device. |
| 30007          | Failed to add the GSM device, because it has been added by another user before.                               |
| 30008          | When you are sharing devices, the shared user does not exist.                                                 |
| 30009          | You have exceeded the limit of groups you can have for your current subscription plan.                        |
| 30010          | The device ID format is wrong for the device being added.                                                     |
| 30011          | The factory data cannot be found in the device being added.                                                   |
| 30012          | The "extra" field of factory data cannot be found in the device being added.                                  |
| 30013          | The brand info of factory data cannot be found.                                                               |
| 30014          | There is an error with the chipid.                                                                            |
| 30015          | There is a digest error when a device is being added.                                                         |
| 30016          | The appid could not be found when a device is being added.                                                    |
| 30017          | This appid is not allowed to add the devices of the current brand.                                            |
| 30018          | No device can be found with current deviceid.                                                                 |
| 30019          | The product model of factory data cannot be found.                                                            |
| 30022          | the device is offline and the operation fails. It will appear in batch updating the device status             |
