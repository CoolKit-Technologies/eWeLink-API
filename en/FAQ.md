# FAQ

## Authentication Error

Response status 406： Failed to pass authorization.
Please check for any problem below:

- General parameter is not passed
- Authentication header is not set
- Incorrect method to pass parameter
- Incorrect signature value

Potential Cause：

- Incorrect signature algorithm causes incorrect signature value.
- Signature algorithm is correct, but the order of parameters for signature algorithm disagrees with the order of Interface parameter,causing authorization failure.

For details, please click "general reference" to check.

## Verification code

Not receiving verification code：

- Check if the account was entered correctly.
- Check if the phone number used is in blacklist. For email, please check for blocking or spam.
- When creating an account, double check if the account has been taken. Verification code won’t be sent to existing account.
- When resetting password, check if the account has been registered. Unregistered account will not receive any verification code.

If you have gone through the questions above and still can not get a verification code, please submit a feedback in eWeLink app. We will try to help as soon as possible. Thanks

## Account Issues

Account Issues：

- Login failed with "wrong account or password" error. Check if you have input the correct account and password.
- Login failed due to login on multiple device.Please check if the account has been use to login on another device. One account can not be signed in on multiple devices simultaneously.
- Can not share devices between accounts: Possible situation: account is not in the same area (accounts between different areas cannot be shared) or the shared account is offline.

## Device Issues

Device Issues：

- Device can not be found after being added. Please check if the device belongs to your brand.
- After being added, app prompts "Device does not exist". This is because the data was not added to test environment.Send the device ID to the tech support in Wechat Group.
- Device offline.Please make sure your network is good.Restart the device and see if it will go online.If problem persist after multiple attempts, contact tech support in WeChat group.

## Device management issues

How to implement one account to manage devices in different regions?

Solution:

Each region is given an Yiweilian account, and the headquarters has the passwords of all accounts, so that the background can manage the devices of all accounts.