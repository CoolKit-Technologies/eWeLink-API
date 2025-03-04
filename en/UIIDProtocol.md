<!--
 * @Descripttion:
 * @version:
 * @Author: Carl
 * @Date: 2021-12-23 13:58:08
 * @LastEditors: Carl
 * @LastEditTime: 2022-01-06 11:43:15
-->

# CoolKit UIID Protocol (Basic Version)

**Description: Some complex device are not open for licensing, so they are not listed in the documentation.The content of the basic control commands will be added in succession, please wait patiently. In addition, detailed and complete device control protocol documentation is only available to paid APPID users. Please contact our staff to bd@coolkit.cn for more details.**

## List of main stream device types (UIID Lists)

Please wait patiently as the documents are released and updated in succession.

<div class="table-center">

|                                          UI                                          |                                     Description                                      | UIID |
| :----------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------: | :--: |
|                                Single-Channel Plug                                 |                                Single-Channel Plug                                 |  1   |
|                                 Dual-Channel Plug                                  |                                 Dual-Channel Plug                                  |  2   |
|                                 Three-channel Plug                                 |                                 Three-channel Plug                                 |  3   |
|                                 Four-channel Plug                                  |                                 Four-channel Plug                                  |  4   |
|                        Power Detection Single-Channel Plug                         |                        Power Detection Single-Channel Plug                         |  5   |
|                                Single-Channel Switch                                 |                                Single-Channel Switch                                 |  6   |
|                                 Dual-Channel Switch                                  |                                 Dual-Channel Switch                                  |  7   |
|                                 Three-channel Switch                                 |                                 Three-channel Switch                                 |  8   |
|                                 Four-channel Switch                                  |                                 Four-channel Switch                                  |  9   |
|                                Switch Retrofit Module                                |                                Switch Retrofit Module                                |  14  |
|                              Thermostat Retrofit Parts                               |                              Thermostat Retrofit Parts                               |  15  |
|                            Cold and Warm Dual Tone Light                             |                            Cold and Warm Dual Tone Light                             |  16  |
|                                Three-Speed Smart Fan                                 |                                Three-Speed Smart Fan                                 |  17  |
|                                      Sensor Hub                                      |        With temperature, humidity, brightness, noise, air quality sensor data        |  18  |
|                                Three-Speed Humidifier                                |                                Three-Speed Humidifier                                |  19  |
|                               RGBCW LED Bulb Light                               |                               RGBCW LED Bulb Light                              |  22  |
|                                          -                                           |                                          -                                           |  23  |
|                              GSM/4G Single-Channel Switch                               |                              GSM/4G Single-Channel Switch                               |  24  |
|                                    Aroma Diffuser                                    |                                    Aroma Diffuser                                    |  25  |
|                     GSM/4G Single-Channel Switching Packet Traffic                      |                     GSM/4G Single-Channel Switching Packet Traffic                      |  27  |
|                                       RFBridge                                       |                        WiFi to RF Wireless Remote Control UI                         |  28  |
|                            GSM/4G Dual-Channel Switch or Plug                            |                            GSM/4G Dual-Channel Switch or Plug                            |  29  |
|                            GSM/4G Four-Channel Switch or Plug                            |                            GSM/4G Four-Channel Switch or Plug                            |  31  |
|                        Power detection Plug overload alarm                         |             Power detection Plug Overload protection alarm can be set              |  32  |
|                                 RGB Strip Controller                                 |              RGB Strip Controller based on Transponder Module Protocol               |  33  |
|                                   Smart Fan Light                                    |           Three-Speed Fan Light - Based on Four-channel switching protocol           |  34  |
|                                          -                                           |                                          -                                           |  35  |
|                                 Single Dimmer Switch                                 |   Single Dimmer Switch Based on RGB Strip Controller Transmission Module Protocol    |  36  |
|                                          -                                           |                                          -                                           |  38  |
|                                 Single Dimmer Light                                  |                 Single dimmer light based on PSF-BLD module protocol                 |  44  |
|                            Downlight & New Ceiling Light                             |                            Downlight & New Ceiling Light                             |  45  |
|                       Dimmable Color Temperature Ceiling Light                       |                       Dimmable Color Temperature Ceiling Light                       |  52  |
|                                RGBC LED Bulb Light                                  |                                RGBC LED Bulb Light Light                                |  56  |
|                               Single-Color Bulb Light                                |                               Single-Color Bulb Light                                |  57  |
|                                     Light Strip                                      |                                     Light Strip                                      |  59  |
|                                     Smart Router                                     |                                     Smart Router                                     |  61  |
|                                          -                                           |                                          -                                           |  62  |
|                                          -                                           |                                          -                                           |  63  |
|                                          -                                           |                                          -                                           |  65  |
|                                    Zigbee Gateway                                    |                                    Zigbee Gateway                                    |  66  |
|                                    -                                    |                                    -                                    |  68  |
|                                 -                                  |                                 -                                  |  69  |
|                            -                            |                            -                            |  76  |
|                     Single-Channel Plug-Multi-channel version                      |                     Single-Channel Plug-Multi-channel version                      |  77  |
|                     Single-Channel Switch-Multi-channel version                      |                     Single-Channel Switch-Multi-channel version                      |  78  |
|                     GSM/4G Single-Channel Plug-No traffic version                     |                     GSM/4G Single-Channel Plug-No traffic version                     |  81  |
|                      GSM/4G Dual-Channel Plug-No traffic version                      |                      GSM/4G Dual-Channel Plug-No traffic version                      |  82  |
|                     GSM/4G Three-Channel Plug-No traffic version                      |                     GSM/4G Three-Channel Plug-No traffic version                      |  83  |
|                      GSM/4G Four-Channel Plug-No traffic version                      |                      GSM/4G Four-Channel Plug-No traffic version                      |  84  |
|                                          -                                           |                                          -                                           |  86  |
|                                          -                                           |                                          -                                           |  87  |
|                                          -                                           |                                          -                                           |  88  |
|                                     GSM-RFBridge                                     |                                 GSM Version RFBridge                                 |  90  |
|                                 Smart Roller Shutter                                 |                                 Smart Roller Shutter                                 |  91  |
|                                          -                                           |                                          -                                           |  92  |
|                                 RF Doorbell Gateway                                  |                                 RF Doorbell Gateway                                  |  98  |
|                                   WiFi Door Sensor                                   |                                   WiFi Door Sensor                                   | 102  |
|            Dual-Color Cold and Warm Light_Support with tuning and scenes             |            Dual-Color Cold and Warm Light_Support with tuning and scenes             | 103  |
|                 RGBCW LED Light_Support with tuning and scenes                  |                 RGBCW LED Light_Support with tuning and scenes                  | 104  |
|                 GSM Single-Channel Plug - Multi-channel protocols                  |      GSM Single-Channel Plug - Multi-channel protocol with traffic device use      | 107  |
|                              eWelink WiFi to IR Gateway                              |                              eWelink WiFi to IR Gateway                              | 109  |
|                          GSM Electricity Statistics Plug                           |                                       GSB-D67                                        | 110  |
|                    Single-Channel Switch Microwave Radar Version                     |                    Single-Channel Switch Microwave Radar Version                     | 112  |
|                     Dual-Channel Switch Microwave Radar Version                      |                     Dual-Channel Switch Microwave Radar Version                      | 113  |
|                     Three-Channel Switch Microwave Radar Version                     |                     Three-Channel Switch Microwave Radar Version                     | 114  |
|                      2.4G Single-Channel Switch Remote Control                       |                      2.4G Single-Channel Switch Remote Control                       | 118  |
|                 Multi-Functional Dual-Channel Power Detection Switch                 |                 Multi-Functional Dual-Channel Power Detection Switch                 | 126  |
|                                    Switch Station                                    |                                    Switch Station                                    | 128  |
|                   Switch Station Four-Channel Switching Sub-Device                   |                   Switch Station Four-Channel Switching Sub-Device                   | 130  |
|                                   HMI Wall Switch                                    |                                   HMI Wall Switch                                    | 133  |
|              Dual-Color Cold and Warm Light_Support 2.4G eWeLink-Remote              |              Dual-Color Cold and Warm Light_Support 2.4G eWeLink-Remote              | 135  |
|                   RGBCW LED Light_Support 2.4G eWeLink-Remote                   |                   RGBCW LED Light_Support 2.4G eWeLink-Remote                   | 136  |
|                                Light Strip-Bluetooth                                 |                                Light Strip-Bluetooth                                 | 137  |
|                  Single-Channel Plug_Support 2.4G eWeLink-Remote                   |                  Single-Channel Plug_Support 2.4G eWeLink-Remote                   | 138  |
|                   Dual-Channel Plug_Support 2.4G eWeLink-Remote                    |                   Dual-Channel Plug_Support 2.4G eWeLink-Remote                    | 139  |
|                   Three-Channel Plug_Support 2.4G eWeLink-Remote                   |                   Three-Channel Plug_Support 2.4G eWeLink-Remote                   | 140  |
|                   Four-Channel Plug_Support 2.4G eWeLink-Remote                    |                   Four-Channel Plug_Support 2.4G eWeLink-Remote                    | 141  |
|                                Midea Air Conditioner                                 |                                Midea Air Conditioner                                 | 142  |
|             eWeLink-Remote Dual-Color Cold and Warm Light Remote Control             |             eWeLink-Remote Dual-Color Cold and Warm Light Remote Control             | 148  |
|                                eWeLink-Remote Gateway                                |                                eWeLink-Remote Gateway                                | 149  |
|                                 New WiFi Door Sensor                                 |                                 New WiFi Door Sensor                                 | 154  |
|                                          -                                           |                                          -                                           | 156  |
|                Rhythmic RGBCW LED Light_Support 2.4G eWeLink-Remote                 |                Rhythmic RGBCW LED Light_Support 2.4G eWeLink-Remote                 | 157  |
|                                          -                                           |                                          -                                           | 158  |
|                             Illumination Strip-Bluetooth                             |                             Illumination Strip-Bluetooth                             | 159  |
|                  Single-Channel Switch_Support 2.4G eWeLink-Remote                   |                  Single-Channel Switch_Support 2.4G eWeLink-Remote                   | 160  |
|                   Dual-Channel Switch_Support 2.4G eWeLink-Remote                    |                   Dual-Channel Switch_Support 2.4G eWeLink-Remote                    | 161  |
|                   Three-Channel Switch_Support 2.4G eWeLink-Remote                   |                   Three-Channel Switch_Support 2.4G eWeLink-Remote                   | 162  |
|                   Four-Channel Switch_Support 2.4G eWeLink-Remote                    |                   Four-Channel Switch_Support 2.4G eWeLink-Remote                    | 163  |
|               Multi-Functional Dual-Channel Switch_Support Motor Mode                |               Multi-Functional Dual-Channel Switch_Support Motor Mode                | 165  |
|                                ZigBee Beeping Gateway                                |                                ZigBee Beeping Gateway                                | 168  |
|                                  2.4G AC Fan Light                                   |                                  2.4G AC Fan Light                                   | 169  |
|                                    Camera Gateway                                    |                                    Camera Gateway                                    | 170  |
|                              Camera Gateway Sub-Device                               |                              Camera Gateway Sub-Device                               | 171  |
|                          Sceme Panel-eWeLink-Remote Gateway                          |                          Sceme Panel-eWeLink-Remote Gateway                          | 172  |
|                              Illumination Strip-Sonoff                               |                              Illumination Strip-Sonoff                               | 173  |
|                              Scene Switch (Six buttons)                              |                              Scene Switch (Six buttons)                              | 174  |
|                                     Switch Mate                                      |                                     Switch Mate                                      | 177  |
| Dual-Color Cold and Warm Light_Support Mechanical Switch Segmentation and Night Mode | Dual-Color Cold and Warm Light_Support Mechanical Switch Segmentation and Night Mode | 179  |
|            Power Detection Plug Overload Alarm-Multi-Channel Protocols             |            Power Detection Plug Overload Alarm-Multi-Channel Protocols             | 182  |
|                                Zigbee Wireless Button                                |                                Zigbee Wireless Button                                | 1000 |
|                             Zigbee Single-Channel Plug                             |                             Zigbee Single-Channel Plug                             | 1009 |
|                             Zigbee Single-Channel Switch                             |                             Zigbee Single-Channel Switch                             | 1256 |
|                               Zigbee Monochrome Light                                |                               Zigbee Monochrome Light                                | 1257 |
|                               Zigbee Dual-color Light                                |                               Zigbee Dual-color Light                                | 1258 |
|                        Zigbee Temperature and Humidity Sensor                        |                        Zigbee Temperature and Humidity Sensor                        | 1770 |
|                                 Zigbee Motion Sensor                                 |                                 Zigbee Motion Sensor                                 | 2026 |
|                              Zigbee Dual-Channel Switch                              |                              Zigbee Dual-Channel Switch                              | 2256 |
|                            Zigbee Door and Window Sensor                             |                            Zigbee Door and Window Sensor                             | 3026 |
|                             Zigbee Three-Channel Switch                              |                             Zigbee Three-Channel Switch                              | 3256 |
|                               Zigbee RGBCW LED Light                                |                               Zigbee RGBCW LED Light                                | 3258 |
|                              Zigbee Water Flood Sensor                               |                              Zigbee Water Flood Sensor                               | 4026 |
|                              Zigbee Four-Channel Switch                              |                              Zigbee Four-Channel Switch                              | 4256 |
|                                 Zigbee Smoke Sensor                                  |                                 Zigbee Smoke Sensor                                  | 5026 |
|                         Zigbee Human Body Sensor_Support OTA                         |                         Zigbee Human Body Sensor_Support OTA                         | 7002 |
|                            Zigbee Door Sensor_Support OTA                            |                            Zigbee Door Sensor_Support OTA                            | 7003 |
|                      Zigbee Single-Channel Switch ­_Support OTA                      |                    Zigbee Single-Channel Switch ­\_Support OTA                     | 7004 |

</div>

## Description of the control command pass-through parameters

Description: For APP side, the cloud platform mode is that APP establishes a long connection through WebSocket  to send "update" messages to control the device, and the following control commands are the content (protocol) of "params" (parameter).

For example, a complete WebSocket  updated command from the APP side is

```json
{
  "action": "update",
  "deviceid": "100000001",
  "apikey": "User apikey",
  "userAgent": "app",
  "sequence": "1585297259553",
  "ts": 1585297259,
  "params": {
    // Put here
    "switches": [
      {
        "switch": "on",
        "outlet": 0
      },
      {
        "switch": "on",
        "outlet": 1
      },
      {
        "switch": "on",
        "outlet": 2
      },
      {
        "switch": "on",
        "outlet": 3
      }
    ]
  }
}
```

Or use the interface method to control the device with the following parameters:

```json
{
  "type": 1,
  "id": "100000001",
  "params": {
    // Put here
    "switches": [
      {
        "switch": "on",
        "outlet": 0
      },
      {
        "switch": "on",
        "outlet": 1
      },
      {
        "switch": "on",
        "outlet": 2
      },
      {
        "switch": "on",
        "outlet": 3
      }
    ]
  }
}
```

Example of the full message of the APP control command return value received by the device via WebSocket , except for the standard format of the interface return parameters (see API Center v2):

```json
{
  "error": 0, // or 400
  "apikey": "User apikey",
  "deviceid": "100000001",
  "userAgent": "device",
  "sequence": "1585297259553" // It needs to be the same as the one sent from the APP side
}
```

A fully reported status message sent by the device via WebSocket  is:

```json
{
  "action": "update",
  "userAgent": "device",
  "apikey": "User apikey",
  "deviceid": "100000001",
  "params": {
    "switch": "on"
  }
}
```

"params" will be stored in the server, and the APP can get the last reported status parameters of the current device through the interface.

## General parameter description

| Parameter Name | Data Type      | Value Range | Parameter Description                                                                |
| -------------- | -------------- | ----------- | ------------------------------------------------------------------------------------ |
| sledOnline     | String         | on,off      | Network Indicator Switch,turn on (on), turn off (off)                                |
| fwVersion      | String         |             | The current firmware version number, e.g. "3.4.0"                                    |
| chipid         | String         |             | Chip id, generally considered to be a fixed parameter of a chip. Each chip is unique |
| rssi           | String         |             | WiFi signal strength, Unit: dBm,e.g. -55                                             |
| timers         | Array\<Object> |             | Timer object, the execution action will be different for each device type            |

Description of the reported parameters for the networking of devices on line:

Each time a device comes online, it needs to report its own status and parameters, including but not limited to switching parameters, inching, power-on state, interlock, signal strength, etc.

rssi Description:

Define RSSI as four levels with the following ranks:

- Level 1: rssi < -92
- Level 2: rssi < -77 and rssi > -92
- Level 3: rssi < -62 and rssi > -77
- Level 4: rssi > -62

When the rssi value of the current connected route or base station is detected across the ranks, the rssi value should be reported.

For specific instructions on timers, see below:

## Timer Rules

Note: All times need to be converted to UTC time for transmission, for example, if the phone time is 18:00, the transmission to the server should be changed to 10:00.

### Timer Parameters

Parameter Description:

| Name               | Type   | Allows Empty                                                                 | Description                                                                                                                           |
| :----------------- | :----- | :--------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------ |
| enabled            | Number | N                                                                            | Enabled or not: 0 means disabled; 1 means enabled                                                                                     |
| mId                | String | N                                                                            | Timer tag, which can be interpreted as the ID of the timer, cannot be repeated, UUID format, which can be generated using the library |
| type               | String | N                                                                            | For Device users, Single Timer and delay (once); Repeat timer (repeat); Loop timer(duration)                                          |
| coolkit_timer_type | String | N                                                                            | For APP users,Single Timer and delay (once); Repeat timer (repeat); Loop timer(duration); delay timer (delay)                         |
| at                 | String | N                                                                            | Execution time: Greenwich Time, also available in UTC time                                                                            |
| do                 | Object | Y                                                                            | Action to be performed                                                                                                                |
| startDo            | Object | Y | Loop timer Exclusive: Action to be performed at the beginning of the cycle|
| endDo              | Object | Y                                                                            | Loop timer Exclusive: subsequent actions to be performed                                                                              |
| period             | String | Y                                                                            | Delay timer Exclusive: time of delay, unit in minutes                                                                                 |

### Timer Type

The following is an example of single-channel devices:

#### Single Timer(UTC)

    // Year-Month-Date T Hour:Minutes:Second.Millisecond Z

    "at":"2020-10-15T07:05:00.279Z" // Run at 7:05 minutes and 0 seconds

Example:

```json
{
  "timers": [
    {
      "mId": "baf5e0d4-a268-cbfb-fd3e-92892cd35029",
      "type": "once",
      "at": "2020-10-15T07:05:00.279Z",
      "coolkit_timer_type": "once",
      "enabled": 1,
      "do": {
        "switch": "on"
      }
    }
  ]
}
```

#### Repeat Timer

    // Minute Hour Day Month Week

    "at": "0 10 * * 0,1,2" // Time expression reference cron, representing 10:00 every Sunday, Monday and Tuesday execution

Value Range

- Minute: 0-59
- Hour: 0-23
- Day: 1-31 (Current default is\*,Represents every day)
- Month: 1-12 (Current default is\*,Represents all months)
- Week: 0-6 (Sunday is 0)

Example:

```json
{
  "timers": [
    {
      "mId": "ab5116e0-e651-9366-16e5-7c3f4332f0d2",
      "type": "repeat",
      "at": "0 10 * * 0,1,2",
      "coolkit_timer_type": "repeat",
      "enabled": 1,
      "do": {
        "switch": "on"
      }
    }
  ]
}
```

#### Loop Timer (alternate)

    // Year-Month-Date T Hour:Minutes:Second.Millisecond Z Cycle Period (min),Interval Time (min)

    "at":"2020-05-31T17:00:00.433Z 10 5", //Loop timerRunning Time, Cycle Period 10 min, Run for another 5 minutes

Example:

```json
{
  "timers": [
    {
      "mId": "87bc1e7f-81f4-ac48-6f34-3f225edefb9a",
      "type": "duration",
      "at": "2020-05-31T17:00:00.433Z 10 5",
      "coolkit_timer_type": "duration",
      "enabled": 1,
      "startDo": {
        "switch": "off",
        "outlet": 0
      },
      "endDo": {
        "switch": "on"
      }
    }
  ]
}
```

#### Loop Timer (repeat)

    // Year-Month-Date T Hour:Minute:Second.Millisecond Z Cycle Period (min)

    "at":"2020-11-13T08:02:00.759Z 30",//Loop timerRunning Time, Repeat for 30 minutes

Example:

```json
{
  "timers": [
    {
      "mId": "75144f1f-1a0a-96c9-b15c-b5411a81d1a9",
      "type": "duration",
      "at": "2020-11-13T08:02:00.759Z 30",
      "coolkit_timer_type": "duration",
      "enabled": 1,
      "do": {
        "switch": "off"
      }
    }
  ]
}
```

#### Delay(UTC)

    // Year-Month-Date T Hour:Minute:Second.Millisecond Z

    "at":"2021-06-28T11:39:00.891Z" // Run at 11:39 minutes and 0 seconds. The same level parameter should be accompanied by a "period", indicating that it is actually the time after the delay.

Example:

```json
{
  "timers": [
    {
      "mId": "18d76d8a-39a1-3346-455e-115dc948822f",
      "type": "once",
      "at": "2021-06-28T11:39:00.891Z", // Time after delay
      "coolkit_timer_type": "delay",
      "enabled": 1,
      "do": {
        "switch": "off"
      },
      "period": "17" // The delay time is 17 minutes
    }
  ]
}
```

## Specific Control Protocols

### UIID1 Single-Channel Plug

#### Parameter Description:


| Parameter Name | Data Type      | Value Range                                                        | Parameter Description                                                                                                                                             |
| -------------- | -------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| switch         | String         | on,off                                                             | Switches of channels: turn on (on), turn off (off)                                                                                                                |
| startup        | String         | on,stay,off                                                        | Settings of power-on state: power on(on), power on hold (stay), power off (off)                                                                                   |
| pulse          | String         | on,off                                                             | Settings of inching: turn on (on), turn off (off)                                                                                                                 |
| pulseWidth     | Number         | [500,3600000] (Unit: millisecond,Supports setting integers of 500) | Duration of Inching,Value Range: 500-3600000 (Unit: milliseconds: 0.5 s-3600 s), Only supports setting an integer multiple of 500 millisecond (i.e., 0.5 seconds) |
| timers         | Array\<Object> |                                                                    | Timer object, the execution action will be different for each device type                                                                                         |

#### Control Command:

1. Turn on device

```json

{
  "switch": "on"
}

```

2. Turn on the switch of the single-channel Plug's indicator, turn on the indicator.

```json
{
  "sledOnline": "on"
}
```

3. Set the single-channel Plug to automatically turn off for 1 second after each operation to turn on the single-channel Plug.

```json
{
  "pulse": "on",
  "pulseWidth": 1000
}
```

4. Set the device to power cycle and turn on the switch 

```json
{
  "startup": "on"
}
```

See the Timer Rules example for timer settings.

### UIID2 Dual-Channel Plug

#### Parameter Description:

| Parameter Name | Data Type      | Value Range | Parameter Description                                                                                                                                                                                                             |
| -------------- | -------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| switches       | Array\<Object> |             | Switch status of all channels                                                                                                                                                                                                     |
| pulses         | Array\<Object> |             | Inching status for all channels                                                                                                                                                                                                   |
| configure      | Array\<Object> |             | Power-up hold status for all channels                                                                                                                                                                                             |
| timers         | Array\<Object> |             | Timer object, the execution action will be different for each device Type, dual-channel Plugs do not support Loop timer (repeat or alternate), **Execution action only supports setting the status of a single channel for now** |

switches Parameter Description:

| Name   | Type   | Allows Empty | Description                                                             |
| :----- | :----- | :----------- | :---------------------------------------------------------------------- |
| switch | String | on,off       | Switches of channels,turn on (on), turn off (off)                       |
| outlet | Number | [0,3]        | Value Range 0-3,Indicates channels 1-4 respectively, cannot be repeated |

configure Parameter Description:

| Name    | Type   | Allows Empty | Description                                                                                     |
| :------ | :----- | :----------- | :---------------------------------------------------------------------------------------------- |
| startup | String | on,stay,off  | Power-up hold status for specific channels, power on(on), power on hold (stay), power off (off) |
| outlet  | Number | [0,3]        | Value Range 0-3,Indicates channels 1-4 respectively, cannot be repeated                         |

pulses Parameter Description:

| Name       | Type   | Allows Empty                                                        | Description                                                                                                                                                           |
| :--------- | :----- | :------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pulse      | String | on,off                                                              | Inching swtich: turn on (on), turn off (off)                                                                                                                          |
| pulseWidth | Number | [500,3600000] (Unit: Millisecond, Supports setting integers of 500) | Inching Duration: Value Range 500-3600000(Unit: Millisecond: 0.5s-3600s),Only set values are supported 500 Milliseconds (That is, an integer multiple of 0.5 seconds) |
| outlet     | Number | [0,3]                                                               | Value Range 0-3, indicates channels 1-4 respectively, cannot be repeated                                                                                              |

#### Control Command:

1. Turn on the switch for channel 1

```json
{
  "switches": [
    {
      "switch": "on",
      "outlet": 0
    },
    {
      "switch": "off",
      "outlet": 1
    },
    {
      "switch": "off",
      "outlet": 2
    },
    {
      "switch": "off",
      "outlet": 3
    }
  ]
}
```

2. Set the dual-channel Plug with channel one to open the switch when the power is turned on after a power failure, and channel two to keep the switch before the power failure when the power is turned on after a power failure.

```json
{
  "configure": [
    {
      "startup": "on",
      "outlet": 0
    },
    {
      "startup": "stay",
      "outlet": 1
    },
    {
      "startup": "off",
      "outlet": 2
    },
    {
      "startup": "off",
      "outlet": 3
    }
  ]
}
```

3. Turn on the switch for the single-channel Plug's indicator, turn on indicator light.

```json
{
  "sledOnline": "on"
}
```

4. Set each operation to turn on channel one of the dual-channel Plug and then automatically turn off for the next 2 seconds.

```json
{
  "pulses": [
    {
      "pulse": "on",
      "width": 2000,
      "outlet": 0
    },
    {
      "pulse": "off",
      "width": 2000,
      "outlet": 1
    },
    {
      "pulse": "off",
      "width": 2000,
      "outlet": 2
    },
    {
      "pulse": "off",
      "width": 2000,
      "outlet": 3
    }
  ]
}
```

5. Timer Settings

5.1 Single Timer(UTC)

    // Year-Month-Date T Hour:Minute:Second.Millisecond Z

    "at":"2020-10-15T07:05:00.279Z" // Run at 7:05 minutes and 0 second

Example:

```json
{
  "timers": [
    {
      "mId": "baf5e0d4-a268-cbfb-fd3e-92892cd35029",
      "type": "once",
      "at": "2020-10-15T07:05:00.279Z",
      "coolkit_timer_type": "once",
      "enabled": 1,
      "do": {
        "switch": "on",
        "outlet": 0
      }
    }
  ]
}
```

5.2 Repeat timer

Minute Hour Day Month Week

    "at":"0 10 * * 0,1,2" // Time expression reference cron, representing 10:00 every Sunday, Monday and Tuesday execution

Value Range:

- Minute:0-59
- Hour: 0-23
- Day:1-31 (Current default is\*,Represents every day)
- Month:1-12 (Current default is\*,Represents all months)
- Week:0-6 (Sunday is 0)

Example:

```json
{
  "timers": [
    {
      "mId": "ab5116e0-e651-9366-16e5-7c3f4332f0d2",
      "type": "repeat",
      "at": "0 10 * * 0,1,2",
      "coolkit_timer_type": "repeat",
      "enabled": 1,
      "do": {
        "switch": "on",
        "outlet": 0
      }
    }
  ]
}
```

5.3 Delay(UTC)


    // Year-Month-Date T Hour:Minute:Second.Millisecond Z

    "at":"2021-06-28T11:39:00.891Z" // Run at 11:. 39: 0 seconds, with a "period" parameter at the same level, indicates that it is actually the time after delay

Example:

```json
{
  "timers": [
    {
      "mId": "18d76d8a-39a1-3346-455e-115dc948822f",
      "type": "once",
      "at": "2021-06-28T11:39:00.891Z", // Time after delay
      "coolkit_timer_type": "delay",
      "enabled": 1,
      "do": {
        "switch": "off",
        "outlet": 0
      },
      "period": "17" // The time delay is 17 minutes
    }
  ]
}
```

### UIID3 Three-Channel Plug

#### Parameter Description:

| Parameter Name | Data Type      | Value Range | Parameter Description:                                                                                                                         |
| -------------- | -------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| switches       | Array\<Object> |             | Switch status of all channels                                                                                                                  |
| pulses         | Array\<Object> |             | Inching status for all channels                                                                                                                |
| configure      | Array\<Object> |             | Power-up hold status for all channels                                                                                                          |
| timers         | Array\<Object> |             | Timerobject,the execution action will be different for each device Type, three-Channel Plugs do not support loop timer (repeat or alternate) |

switches Parameter Description:

| Name   | Type   | Allows Empty | Description                                                              |
| :----- | :----- | :----------- | :----------------------------------------------------------------------- |
| switch | String | on,off       | Switches of channels,turn on (on), turn off (off)                        |
| outlet | Number | [0,3]        | Value Range 0-3, indicates channels 1-4 respectively, cannot be repeated |

configure Parameter Description:

| Name    | Type   | Allows Empty | Description                                                                                    |
| :------ | :----- | :----------- | :--------------------------------------------------------------------------------------------- |
| startup | String | on,stay,off  | Power-up hold status for specific channels,power on(on), power on hold (stay), power off (off) |
| outlet  | Number | [0,3]        | Value Range 0-3, indicates channels 1-4 respectively, cannot be repeated                       |

pulses Parameter Description:

| Name       | Type   | Allows Empty                                                      | Description                                                                                                                                                          |
| :--------- | :----- | :---------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pulse      | String | on,off                                                            | Inching switch: turn on (on), turn off (off)                                                                                                                         |
| pulseWidth | Number | [500,3600000] (Unit:Millisecond,Supports setting integers of 500) | Inching Duration: Value Range 500-3600000 (Unit: milliseconds: 0.5s-3600s). Only supports setting an integer multiple of 500 milliseconds (i.e., 0.5 seconds).   |
| outlet     | Number | [0,3]                                                             | Value Range 0-3, indicates channels 1-4 respectively, cannot be repeated                                                                                             |

#### Control Command:


1. Turn on the switches for channels 1, 2 and 3

```json
{
  "switches": [
    {
      "switch": "on",
      "outlet": 0
    },
    {
      "switch": "on",
      "outlet": 1
    },
    {
      "switch": "on",
      "outlet": 2
    },
    {
      "switch": "off",
      "outlet": 3
    }
  ]
}
```

Other features include timers, consistent with UIID2

### UIID4 Four-Channel Socekt

#### Parameter Description:

| Parameter Name | Data Type      | Value Range | Parameter Description:                                                                                                                         |
| -------------- | -------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| switches       | Array\<Object> |             | Switch status of all channels                                                                                                                  |
| pulses         | Array\<Object> |             | Inching status for all channels                                                                                                                |
| configure      | Array\<Object> |             | Power-up hold status for all channels                                                                                                          |
| timers         | Array\<Object> |             | Timer object,the execution action will be different for each device Type,four-Channel Socekt does not support loop timer (repeat or alternate) |

switches Parameter Description:

| Name   | Type   | Allows Empty | Description                                                             |
| :----- | :----- | :----------- | :---------------------------------------------------------------------- |
| switch | String | on,off       | Switches of channels,turn on (on), turn off (off)                       |
| outlet | Number | [0,3]        | Value Range 0-3,indicates channels 1-4 respectively, cannot be repeated |

configure Parameter Description:

| Name    | Type   | Allows Empty | Description                                                                                    |
| :------ | :----- | :----------- | :--------------------------------------------------------------------------------------------- |
| startup | String | on,stay,off  | Power-up hold status for specific channels,power on(on), power on hold (stay), power off (off) |
| outlet  | Number | [0,3]        | Value Range 0-3,indicates channels 1-4 respectively, cannot be repeated                        |

pulses Parameter Description:

| Name       | Type   | Allows Empty                                                        | Description                                                                                                                                                            |
| :--------- | :----- | :------------------------------------------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pulse      | String | on,off                                                              | Inching switch, turn on (on), turn off (off)                                                                                                                           |
| pulseWidth | Number | [500,3600000] (Unit: Millisecond, Supports setting integers of 500) | Inching Duration: Value Range 500-3600000 (Unit: milliseconds: 0.5s-3600s). Only supports setting an integer multiple of 500 milliseconds (i.e., 0.5 seconds).   |
| outlet     | Number | [0,3]                                                               | Value Range 0-3, indicates channels 1-4 respectively, cannot be repeated                                                                                               |

#### Control Command:

1. Turn off the switches for channels 1, 2, 3 and 4

```json
{
  "switches": [
    {
      "switch": "off",
      "outlet": 0
    },
    {
      "switch": "off",
      "outlet": 1
    },
    {
      "switch": "off",
      "outlet": 2
    },
    {
      "switch": "off",
      "outlet": 3
    }
  ]
}
```

Other features include timers, consistent with UIID2

### UIID5 Power Detection Single-Channel Plug

#### Parameter Description:

| Parameter Name     | Data Type      | Value Range                              | Parameter Description                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------ | -------------- | ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| switch             | String         | on,off                                   | Total switch: turn on (on), turn off (off)                                                                                                                                                                                                                                                                                                                                                   |
| power              | String         | Positive numbers with two decimal places | Power, Unit: W,e.g. 1800.01                                                                                                                                                                                                                                                                                                                                                                  |
| voltage            | String         | Positive numbers with two decimal places | Voltage, Unit: V,e.g. 220.00                                                                                                                                                                                                                                                                                                                                                                 |
| current            | String         | Positive numbers with two decimal places | Current, Unit: A,e.g. 1.00                                                                                                                                                                                                                                                                                                                                                                   |
| oneKwh             | String         | start,stop,get                           | Counting the electricity consumption: Start counting (start), stop counting(stop), refresh (get), Unit: KW.H                                                                                                                                                                                                                                                                                 |
| startTime          | Datetime       |                                          | Start time for counting the current electricity consumption, Zero Time Zone                                                                                                                                                                                                                                                                                                                  |
| endTime            | Datetime       |                                          | Stop time for counting the current electricity consumption, Zero Time Zone                                                                                                                                                                                                                                                                                                                   |
| hundredDaysKwh     | String         | get                                      | Get historical electricity consumption for the past 100 days, Unit: Kwh                                                                                                                                                                                                                                                                                                                      |
| hundredDaysKwhData | String         |                                          | 100 days of daily electricity consumption in hexadecimal, expressed as an all lowercase string, 600 bytes, to two decimal places. Unit: KW.H. If the total daily electricity consumption for 100 days is: "25.11, 25.31, 0.00, 0.00 ................ (Total 100 days)" -> "190101190301000000000000 ..... The time order is that the current day is at the top, and the others go backwards. |
| sledOnline         | String         | on,off                                   | Indicator switch, turn on (on), turn off (off)                                                                                                                                                                                                                                                                                                                                               |
| timeZone           | Int            |                                          | Get the time zone where the current phone is located, East zone is positive, West zone is negative                                                                                                                                                                                                                                                                                           |
| uiActive           | Int            |                                          | Indicates the valid time for this UI activation, unit: S (default 60s). Not sent when UI is off or running in the background. This field is only used for long connections and does not need to be supported under LAN.                                                                                                                                                                      |
| oneKwhData         | Float          | [0‐50000]                                | The current electricity consumption value is expressed as a decimal string, accurate to 2 decimal places. Unit: KW.H,Value Range: [0‐50000], e.g. 110.32                                                                                                                                                                                                                                     |
| timers             | Array\<Object> |                                          | Timer object,the execution action will be different for each device Type                                                                                                                                                                                                                                                                                                                     |

#### Control Command:

1. Turn on device

```json

{
  "switch": on
}

```

2. Activation command

The device reports its status if the power change exceeds 2W, or the voltage exceeds 5V, or the current exceeds 0.03A during the activation period, and does not report to the server if it is outside the activation period.

```json
{
  "uiActive": 60
}
```

App needs to send the command to activate UI again within 60s activation period, currently APP sends the command every 50 seconds after launching, and after the device side receives the command, it will report when the conditions are met.

```json
{
  "power":"300.00",
  "voltage":"220.00",
  "current":"5.00"
}
```

3. Start counting the current electricity consumption, start counting (start), stop counting (stop).

Click start to send the command:

```json
{
  "onKwh": "start",
  "endTime": "",
  "startTime": "2019-06-06T03:37:05.064Z"
}
```

Clicking stop requires a stop command to be issued first:

```json
{
  "onKwh": "stop",
  "endTime": "2019-06-06T03:57:05.064Z",
  "startTime": "2019-06-06T03:37:05.064Z"
}
```

Then send the command to get the current electricity consumption

```json
{
  "oneKwh": "get"
}
```

Refresh electricity consumption:

```json
{
  "oneKwh": "get"
}
```

- The device returns "oneKwhData": The current electricity consumption value is expressed as a decimal string, accurate to 2 decimal places,Unit: KW.H,Value Range: [0-50000],e.g. 110.32

4. To view historical electricity consumption

```json
{
  "hundredDaysKwh": "get"
}
```

The device returns "hundredDaysKwhData": 100 days of daily electricity consumption in hexadecimal, expressed as an all lowercase string, 600 bytes, to two decimal places. Unit: KW.H. If the total daily electricity consumption for 100 days is: "25.11, 25.31, 0.00, 0.00 ................ (Total 100 days)" -> "190101190301000000000000 ..... The time order is that the current day is at the top, and the others go backwards.

Parsing Example: [CoolKit_Analyze_Power_Consumption_Demo.zip](https://raw.githubusercontent.com/CoolKit-Technologies/eWeLink-API/main/media/files/CoolKit_Analyze_Power_Consumption_Demo.zip)


5. Turn on the switch of power detection single-channel Plug's indicator, turn on indicator light

```json
{
  "sledOnline": "on"
}
```

6. Set power detection single-channel Plug to turn off automatically for 1 second after each operation.

```json
{
  "pulse": "on",
  "pulseWidth": 1000
}
```

Note:

- pulse:Inching switch, set up each operation to turn on the single-channel Plug and then require the device to be turned off at a subsequent time.
- pulseWidth:Set Inching's time, Unit: millisecond. Minimum 500 milliseconds, maximum 3600000 milliseconds, only integer multiples of 500 are supported.
  Timer Setting, consistent with UIID1, only turning the device on and off is supported.

### UIID6 Single-Channel Switch

Consistent with UIID1

### UIID7 Dual-Channel Switch

Consistent with UIID2

### UIID8 Three-Channel Switch

Consistent with UIID3

### UIID9 Four-Channel Switch

Consistent with UIID4

### UIID14 Switch Retrofit Module

Consistent with UIID1.

### UIID15 Thermostat Retrofit Parts

#### Parameter Description:

| Parameter Name     | Data Type | Value Range                                                        | Parameter Description                                                                                                                                                                                                                                                                                  |
| ------------------ | --------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| switch             | String    | on,off                                                             | Switches of channels, turn on (on), turn off (off)                                                                                                                                                                                                                                                     |
| startup            | String    | on,stay,off                                                        | Settings of power-on state: power on(on), power on hold (stay), power off (off)                                                                                                                                                                                                                        |
| pulse              | String    | on,off                                                             | Inching switch, turn on (on), turn off (off)                                                                                                                                                                                                                                                           |
| pulseWidth         | Number    | [500,3600000] (Unit: Millisecond,Supports setting integers of 500) | Inching Duration: Value Range 500-3600000 (Unit: milliseconds: 0.5s-3600s). Only supports setting an integer multiple of 500 milliseconds (i.e., 0.5 seconds).                                                                                                                                   |
| mainSwitch         | String    | on,off                                                             | Thermostat switch                                                                                                                                                                                                                                                                                      |
| deviceType         | String    | normal,temperature,humidity                                        | Control mode status of the device: temperature control (temperature), humidity control (humidity), normal (normal),that is, manual control of the switch state, disable inching function under automatic control function                                                                              |
| sensorType         | String    | DHT11/DS18B20/AM2301/MS01/errorType                                | Sensor Model, DHT11:Humidity Range[20,90], Temperature Range[0,50]; DS18B20: Humidity unavailable, Temperature Range[-55,125]; AM2301: Humidity Range[0,100], Temperature Range[-40,80]; MS01: Soil moisture sensor,Humidity Range[0,100], Temperature unavailable; errorType: Unsupported Sensor Type |
| currentHumidity    | String    |                                                                    | Current humidity value, when humidity is not available currentHumidity is unavailable                                                                                                                                                                                                                  |
| currentTemperature | String    |                                                                    | Current temperature value, when temperature is not available, currentTemperature is unavailable;                                                                                                                                                                                                       |
| targets            | Array     |                                                                    | Automatic mode execution conditions and target response, when the temperature or humidity reaches the preset value (targetHigh/targetLow), the target response is triggered                                                                                                                            |
| targetHigh         | String    | Temperature Range[-999,999],Humidity Range[0,100]                  | Target upper limit value,targetHigh value must be greater than targetLow value                                                                                                                                                                                                                         |
| targetLow          | String    | Temperature Range[-999,999],Humidity Range[0,100]                  | Target lower limit value,temperature control (temperature), humidity control (humidity), normal (normal)                                                                                                                                                                                               |
| reaction           | Object    |                                                                    | Execute the action after the preset value is reached, prohibit the upper threshold trigger response from being the same as the lower threshold trigger response, That is, two trigger responses cannot be turned on or off at the same time                                                            |

#### Control Command:

1. Turn on device

```json
{
  "switch": "on",
  "mainSwitch": "on",
  "deviceType": "normal"
}
```

2. Turn off device

```json
{
  "switch": "off",
  "mainSwitch": "off"
}
```

3. Device reports real-time temperature, humidity, sensor Type

```json
{
  "currentTemperature": "15",
  "currentHumidity": "50",
  "sensorType": "DS18B20"
}
```

The temperature accuracy (reporting threshold) is 0.5 degrees, the humidity accuracy (reporting threshold) is 5 percent, the temperature resolution is 0.1 degrees, and the humidity resolution is 1 percent. Whether it conforms to the data upload strategy is judged every 5S. Each time the temperature value and humidity value are uploaded together, and the detection interval is shared. At the same time, upload the temperature and humidity when online.

4. Turn on auto control mode

```json
//Set to automatic temperature control, Close if greater than 25°C, open if less than 24°C
{
  "deviceType": "temperature",
  "mainSwitch": "on",
  "targets": [
    {
      "targetHigh": "25",
      "reaction": {
        "switch": "off"
      }
    },
    {
      "targetLow": "24",
      "reaction": {
        "switch": "on"
      }
    }
  ]
}
```

Note:

After entering auto mode, the device will enter a temporary manual state when it is physically turned off at this time, and will enter auto mode again when it is turned on by the APP or physically.

- Manual mode: deviceType == normal && mainSwitch == off || deviceType == normal && mainSwitch == on
- Temporary manual mode: deviceType != normal && mainSwitch == off
- Auto control mode: deviceType != normal && mainSwitch == on

5. Turn off auto control

```json
{
  "mainSwitch": "off",
  "deviceType": "normal"
}
```

6. Set the power-on state (power-up state)

```json
{
  "startup": "on"
}
```

7. Set Timer

```json
{
  "timers": [
    {
      //delay
      "mId": "6bdfc96c-0962-ad75-c430-15d9eb351154",
      "type": "once",
      "at": "2020-12-16T18:37:00.761Z",
      "coolkit_timer_type": "delay",
      "enabled": 1,
      "do": {
        "switch": "on",
        "mainSwitch": "on"
      },
      "period": "390"
    },
    {
      //Single Timer
      "mId": "c5601da9-aa5f-0946-a1fd-2a2a35daf59a",
      "type": "once",
      "at": "2020-12-16T13:11:00.974Z",
      "coolkit_timer_type": "once",
      "enabled": 1,
      "do": {
        "switch": "on",
        "mainSwitch": "on"
      }
    },
    {
      //Repeat timer
      "mId": "870262af-4f9c-7d23-318b-f65d5a79d3eb",
      "type": "repeat",
      "at": "6 15 * * 0,1,2,3,4,5,6",
      "coolkit_timer_type": "repeat",
      "enabled": 1,
      "do": {
        "switch": "on",
        "mainSwitch": "on"
      }
    },
    {
      //Loop timer-repeat Perform a turn-on every 30 minutes from the start time until the device is turned on
      "mId": "fcfd83d5-4c8c-50c6-73e8-aeadeac5abdc",
      "type": "duration",
      "at": "2020-12-16T15:23:00.140Z 30",
      "coolkit_timer_type": "duration",
      "enabled": 1,
      "do": {
        "switch": "on",
        "mainSwitch": "on"
      }
    },
    {
      //Loop timer-alternate Every 60 minutes cycle, from start time to turn off the device, 30 minutes to turn on the device, 30 minutes to turn off the device...
      "mId": "fcfd83d5-4c8c-50c6-73e8-aeadeac5abdc",
      "type": "duration",
      "at": "2020-12-16T15:23:00.140Z 60 30",
      "coolkit_timer_type": "duration",
      "enabled": 1,
      "startDo": {
        "switch": "off",
        "mainSwitch": "off"
      },
      "endDo": {
        "switch": "on",
        "mainSwitch": "on"
      }
    }
  ]
}
```

8. Inching Setting

```json
{
  "pulseWidth": 1500,
  "pulse": "on"
}
```

9. Device reporting version, signal strength:

```json
{
  "fwVersion": "3.4.1",
  "rssi": -46
}
```

### UIID16 Cold and Warm Dual Tone Light

#### Parameter Description:

| Parameter Name   | Data Type       | Value Range                  | Parameter Description                                                                                                                                                                                                         |
| -------- | -------------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| state    | String         | on,off                    | Switch, turn on (on), turn off (off)                                                                                                                                                                                      |
| channel0 | String         | [25,255], there are 21 modes, | Brightness of cold light, there are 21 modes: ['25', '38', '40', '61', '85', '103', '117', '130', '141', '150', '159', '167', '174', '180', '186', '192', '197', '202', '207', '211', '255' ] warm light is 0, the value of neutral light is the same as channel 1 |
| channel1 | String         | [25,255], there are 21 modes  | Brightness of warm light, 21 modes as above, cold light is 0                                                                                                                                                                              |
| type     | Number         | cold,middle,warm          | cold and warm light type value, used on the App side, used to separate the cold and warm light type, the device side does not handle this field                                                                                                                                             |
| timers   | Array\<Object> |                           | Timer object, the execution action will be different for each device type                                                                                                                                                                         |

#### Control Command:

1. Turn on device

```json
{
  "state": "on"
}
```

2. Set cold light

```json
{
  "channel0": "40",
  "channel1": "0",
  "type": "cold"
}
```

3. set warm light

```json
{
  "channel0": "0",
  "channel1": "40",
  "type": "warm"
}
```

4. set neutral light

```json
{
  "channel0": "40",
  "channel1": "40",
  "type": "middle"
}
```

5. Set single/repeat timer

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "once",
      "at": "2019-05-30T10:57:00.776Z",
      "type": "once",
      "do": {
        "state": "off"
      },
      "mId": "96c0f48e-ce4a-3656-1c1c-2568a2eb1991"
    },
    {
      "enabled": 1,
      " coolkit_timer_type": "repeat",
      "at": "7 15 * * 1,2,3,4,6,0",
      "type": "repeat",
      "do": {
        "state": "off"
      },
      "mId": "22c944b2-5794-8fdc-e8a4-1fc8d05922f3"
    }
  ]
}
```

6. Set delay

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "delay",
      "at": "2019-08-09T16:37:00.768Z",
      "period": "13530",
      "type": "once",
      "do": {
        "switch": "on"
      },
      "mId": "eb1c1aed-070c-4e5c-f1c6-a78ea4bac09c"
    }
  ]
}
```

Note:

-  coolkit_timer_type: timer's type, delay is a type of delay, only single execution, can be enabled/disabled.
- do: The action that needs to be performed by the device, the action that can be performed by Cold and Warm Dual Tone Light delay is the light switch, state: turn on (on), turn off (off)

### UIID17 Three-Speed Smart Fan

#### Parameter Description:

| Parameter Name | Data Type | Value Range             | Parameter Description                                                |
| ------ | -------- | -------------------- | ------------------------------------------------------- |
| fan    | String   | on,off               | Switch of Fan, turn on (on), turn off (off)                           |
| speed  | String   | slow,moderate,fast   | Speed, slow speed (slow); moderate speed (moderate); fast speed (fast)              |
| mode   | String   | normal,natural,sleep | Mode, normal mode (normal); natural mode (natural) ; sleep mode (sleep) |
| shake  | String   | on,off               | Shake,  turn on (on), turn off (off)                                |

#### Control Command:

1. Turn on Fan

```json
{
  "fan": "on"
}
```

2. Adjust speed to fast

```json
{
  "speed": "fast"
}
```

3. Adjust mode to sleep mode

```json
{
  "mode": "sleep"
}
```

4. Turn on Shake

```json
{
  "shake": "on"
}
```

### UIID18 Sensor Hub

#### Parameter Description:

| Parameter Name      | Data Type | Value Range                | Parameter Description                                                    |
| ----------- | -------- | ----------------------- | ----------------------------------------------------------- |
| dusty       | Number   | [1,10]                  | Air Quality, [1,3] Excellent; [4,6] Good ; [7,10] Poor                   |
| noise       | String   | [1,10]                  | Noise,  [1,2] Quiet ; [3,5] Normal; [6,10] Noisy                 |
| light       | String   | [1,10]                  | Brightness, [1,3] Bright ;  [4,7] Normal; [8,10] Dark                 |
| temperature | String   | [-Infinity, Infinity] | Temperature, [-Infinity, 15] Cold; [16, 28] Comfy;  [29, Infinity] Hot |
| humidity    | String   | [0,100]                 | Humidity, [0,30] Dry ;  [31,70] Normal ; [71,100] Moist             |

#### Control Command:

None, all by Device Report.

### UIID19 Three-Speed Humidifier

#### Parameter Description:

| Parameter Name      | Data Type       | Value Range | Parameter Description                                        |
| ----------- | -------------- | -------- | ----------------------------------------------- |
| switch      | String         | on,off   | Switch, turn on (on), turn off (off)                   |
| mode        | String         | normal,  | Mode, normal mode (normal). Send the switch command with this field |
| state       | Number         | 1,2,3    | Level, 3 levels                             |
| water       | Number         | 0,1      | Capacity, 0 Shortage; 1 Normal                            |
| temperature | Number         | [0,50]   | Current Temp., Device Report, Unit: Degrees Celsius                  |
| humidity    | Number         | [20,90]  | Current Humidity Percentage, Device Report                        |
| timers      | Array\<Object> |          | Timer object, the execution action will be different for each device type        |

#### Control Command:

1. Turn on device:

```json
{
  "switch": "on"
}
```

2. Adjust Levels

```json
{
  "switch": "on",
  "state": 1
}
```

3. Device reports status

```json
{
  "water": 1,
  "temperature": 31,
  "humidity": 50
}
```

4. Set single/repeat timer

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "once",
      "at": "2019-05-30T10:57:00.776Z",
      "type": "once",
      "do": {
        "switch": "off"
      },
      "mId": "96c0f48e-ce4a-3656-1c1c-2568a2eb1991"
    },
    {
      "enabled": 1,
      " coolkit_timer_type": "repeat",
      "at": "7 15 * * 1,2,3,4,6,0",
      "type": "repeat",
      "do": {
        "switch": "off"
      },
      "mId": "22c944b2-5794-8fdc-e8a4-1fc8d05922f3"
    }
  ]
}
```

### UIID22 RGBCW LED Bulb Light

#### Parameter Description:

| Parameter Name | Data Type | Value Range      | Parameter Description                                                                                                                              |
| -------------- | --------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| state          | String    | on,off           | Switching of lights: turn on (on), turn off (off)                                                                                                  |
| channel0       | String    | [25,255]         | Bulb Lamp Channel 1: Indicates cold light, Value Range 25-255                                                                                      |
| channel1       | String    | [25,255]         | Bulb Lamp Channel 2: Indicates warm light, Value Range 25-255                                                                                      |
| type           | String    | cold,middle,warm | When channel0>channel1, it's cold light (cold); When channel0=channel1, it's middle light (middle); When channel0<channel1, it's warm light (warm) |
| channel2       | String    | [0,255]          | R value, red channel range 0-255                                                                                                                   |
| channel3       | String    | [0,255]          | G value, green channel range 0-255                                                                                                                 |
| channel4       | String    | [0,255]          | B value, blue channel range 0-255                                                                                                                  |
| zyx_mode       | Number    | [1,6]            | Bulb light mode/scene: 1 White Light Mode; 2 Color Light Mode; 3 Good Night Scene; 4 Reading Scene; 5 Party Scene; 6 Leisure Scene                 |
| timers         | Array     |                  | TimerType, timer: once (Single execution); repeat (repeat execution); delay: delay (Single execution only)                                         |

Note: Lights can only be turned on when the lights are off, and can not adjust the color temperature, brightness.

#### Control Command:

1. Turn on the bulb light

Turn on (on), turn off (off), If the light is turned on locally for the first time in the current phone, the default is white light mode (neutral light, brightness value 159), and the light is turned on locally for the first time in the non-current phone, the default is the light state when the light was turned off last time (such as red in color light mode when the light was turned off last time, the default is also red in color light mode when the light is turned on again)

```json
{
  "state": "on"
}
```

2. Turn on the white light mode of the bulb light.

When first added, the default color temperature is neutral (type=middle, channel0=channel1), brightness value 159, and zyx_mode=1 for white light mode.

```json
{
  "channel0": "159",
  "channel1": "159",
  "channel2": "0",
  "channel3": "0",
  "channel4": "0",
  "zyx_mode": 1,
  "type": "middle"
}
```

3. In white light mode, the brightness of neutral light is adjusted to 60.

```json
{
  "type": "middle",
  "channel0": "60",
  "channel1": "60"
}
```

4. In white mode, the initial adjustment of the color temperature of the bulb light for cool light, brightness value default 159.

When channel0>channel1, it is cold light (cold), when channel0=channel1, it is neutral light (middle), and when channel0<channel1, it is warm light (warm).

```json
{
  "type": "cold",
  "channel0": "159",
  "channel1": "0"
}
```

5. In white light mode, the brightness of the cool light is adjusted to 85.

```json
{
  "type": "cold",
  "channel0": "85",
  "channel1": "0"
}
```

6. In white light mode, the initial adjustment of the color temperature of the bulb light for warm light, brightness value default 159.

```json
{
  "type": "warm",
  "channel0": "0",
  "channel1": "159"
}
```

7. In white light mode, adjust the color temperature of the bulb light to cool light.

The brightness value is not the default 159, but the 85 that existed locally after the last adjustment

```json
{
  "type": "cold",
  "channel0": "85",
  "channel1": "0"
}
```

8. Open the color light mode of the bulb light

Default display: red (channel2 indicates R value, channel3 indicates G value, channel4 indicates B value, RGB value of red is[255,0,0]), also channel0 and channel1 are 0 by default, type=middle means neutral light, zyx_mode=2 means color light mode.

```json
{
  "channel0": "0",
  "channel1": "0",
  "channel2": "255",
  "channel3": "0",
  "channel4": "0",
  "zyx_mode": 2,
  "type": "middle"
}
```

9. Adjust the color of bulb light to blue

RGB is [0,0,255], that is, R value: channel2=0, G value: channel3=0, B value: channel4=255, channel0 and channel1 are 0 by default,zyx_mode=2 means color light mode.

```json
{
  "channel0": "0",
  "channel1": "0",
  "channel2": "0",
  "channel3": "0",
  "channel4": "255",
  "zyx_mode": 2
}
```

10. Adjust the scene of bulb light for goodnight

Non-editable, pre-defined values in advance, RGB value is [189,118,0], that is, R value: channel2=189, G value: channel3=118, B value: channel4=0, channel0 and channel1 are 0 by default, zyx_mode=3 means good night scene, type=middle means neutral light.

```json
{
  "channel0": "0",
  "channel1": "0",
  "channel2": "189",
  "channel3": "118",
  "channel4": "0",
  "zyx_mode": 3,
  "type": "middle"
}
```

11. Adjust the scene of bulb light for reading

Non-editable, pre-defined values in advance, RGB value is [255,255,255], that is, R value: channel2=255, G value: channel3=255, B value: channel4=255, channel0 and channel1 are 0 by default, zyx_mode=4 means reading scene, type=middle means neutral light.

```json
{
  "channel0": "0",
  "channel1": "0",
  "channel2": "255",
  "channel3": "255",
  "channel4": "255",
  "zyx_mode": 4,
  "type": "middle"
}
```

12. Adjust the scene of bulb light for party

Non-editable, pre-defined values in advance, RGB value is [207,56,3], that is, R value: channel2=207, G value: channel3=56, B value: channel4=3, channel0 and channel1 are 0 by default, zyx_mode=5 means party scene, type=middle means neutral light.

```json
{
  "channel0": "0",
  "channel1": "0",
  "channel2": "207",
  "channel3": "56",
  "channel4": "3",
  "zyx_mode": 5,
  "type": "middle"
}
```

13. Adjust the scene of bulb light for leisure

Non-editable, pre-defined values in advance, RGB value is [56,85,179], that is, R value: channel2=56, G value: channel3=85, B value: channel4=179, channel0 and channel1 are 0 by default, zyx_mode=6 means leisure scene, type=middle means neutral light.

```json
{
  "channel0": "0",
  "channel1": "0",
  "channel2": "56",
  "channel3": "85",
  "channel4": "179",
  "zyx_mode": 6,
  "type": "middle"
}
```

14. Single Timer

Set the bulb light to turn on at 11:26 a.m. on June 27, 2019, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      "coolkit_timer_type": "once",
      "at": "2019-06-27T03:26:00.387Z",
      "type": "once",
      "do": {
        "state": "on"
      },
      "mId": "09c41897-605c-2cce-6ab9-7c58b7f3c221"
    }
  ]
}
```

15. delay

Set the bulb light to turn off at 11:26 pm on June 27, 2019 with a delay of 4 Minute at 11:30 pm without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      "coolkit_timer_type": "delay",
      "at": "2019-06-27T03:30:00.552Z",
      "period": "4",
      "type": "once",
      "do": {
        "state": "off"
      },
      "mId": "1778f364-ae92-43b6-33d0-9a5ff531e1bc"
    }
  ]
}
```

coolkit_timer_type:timer's type, delay is a type of delay, only single execution, can be enabled/disabled.
do: The action that needs to be performed by the device, the action that can be performed by the bulb light delay is the light switch, state: turn on (on), turn off (off)


### UIID24 GSM/4G Single-Channel Switch

#### Parameter Description:

| Parameter Name     | Data Type       | Value Range                                         | Parameter Description                                                                                                        |
| ---------- | -------------- | ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| switch     | String         | on,off                                           | Switch: turn on (on), turn off (off)                                                                                   |
| startup    | String         | on,stay,off                                      | Settings of power-on state: power on(on), power on hold (stay), power off (off)                                                                |
| pulse      | String         | on,off                                           | Settings of inching: turn on (on), turn off (off)                                                                                 |
| pulseWidth | Number         | [500,3600000] (Unit: millisecond,Supports setting integers of 500) | Inching Duration: Value Range 500-3600000 (Unit: milliseconds: 0.5s-3600s). Only supports setting an integer multiple of 500 milliseconds (i.e., 0.5 seconds).   |
| timers     | Array\<Object> |                                                  | Timer object, the execution action will be different for each device type                                                                        |

#### Control Command:

1. Turn on device:

```json
{
  "switch": "on"
}
```

2. Set the GSM/4G Single-Channel Switch to automatically turn off for 1 second after each operation to turn on the GSM/4G Single-Channel Switch:

```json
{
  "pulse": "on",
  "pulseWidth": 1000
}
```

3.Set the device to power cycle and turn on the switch 

```json
{
  "startup": "on"
}
```

See the <Timer Rules> example for timer settings, consistent with single-channel Plug's timer (Single/repeat timer and delay).

### UIID25 Aroma Diffuser

#### Parameter Description:

| Parameter Name      | Data Type | Value Range            | Parameter Description                                                                             |
| ----------- | -------- | ------------------- | ------------------------------------------------------------------------------------ |
| switch      | String   | on,off              | Total switch: turn on (on), turn off (off)                                                           |
| state       | Number   | 1,2(default 1)       | Mist Level, 1 small, 2 big, default small, Memorable                                                 |
| water       | Number   | 0,1(read only)         | Water Capacity, 0 Shortage, 1 Normal                                                                 |
| lightswitch | Number   | 0,1                 | Light Switch, 0 turn off, 1 turn on                                                             |
| lightmode   | Number   | 1,2,3               | Light Mode, 1 7-color light, 2 Specify a color, 3 Night Light                                           |
| lightRcolor | Number   | [0,255]             | Light Color, R Channel, Non-negative integer, Value Range 0-255                                           |
| lightGcolor | Number   | [0,255]             | Light Color, G Channel, Non-negative integer, Value Range 0-255                                           |
| lightBcolor | Number   | [0,255]             | Light Color, B Channel, Non-negative integer, Value Range 0-255                                           |
| lightbright | Number   | [0,100](default 100) | Light Brightness, Value Range 0-100, default brightness is 100 when adjusting color                                     |
| timers      | Array    |                     | Timer Type, timer: once (Single execution); repeat (repeat execution); delay: delay (Single execution only) |
| sledOnline  | String   | on,off              | Always-off Switch, turn on (on), turn off (off)                                                          |

#### Control Command:

Note: e.g. Turn off the Aroma Diffuser in the night light mode, when the Aroma Diffuser is turned on again, the light mode will return to one of the light mode states (including light color and brightness) before the night light mode..

If you turn on the Aroma Diffuser and set the light mode to 7-color light first and then set the mode to night light, turn off and then turn on the Aroma Diffuser, the light of the Aroma Diffuser will return to the 7-color light; 

If you turn on the Aroma Diffuser and adjust the light mode to the specified color [2,19,0] and the light brightness to 43, then turn off the Aroma Diffuser and turn on the Aroma Diffuser again, the light of the Aroma Diffuser will return to the specified color [2,19,0] mode and the light brightness to 43.

1. Turn on Aroma Diffuser, turn on (on), turn off (off)

```json
{
  "switch": "on"
}
```

2. Adjust the mist level, 1 small, 2 big

```json
{
    "state": 1
}
```

3. turn on light switch, 0 turn off, 1 turn on

```json
{
    "lightswitch": 1
}
```

4. set Light Mode to 7-color light

Note: Debugging found that after the mode is adjusted to 7-color light, a command will be sent at the same time to adjust the light brightness to 100, but the UI interface of 7-color light does not have an entrance to adjust the light brightness

The first command:

```json
{
  "lightmode": 1
}
```

The second command:

```json
{
  "lightbright": 100
}
```

5. set Light Mode to specific light (RGB: 0,3,255)

Note: Debugging found that after the mode is adjusted to the specified color, the light brightness will be adjusted to 100 by default at the same time, and then manually adjusted according to demand

The first command: 

```json
{
    "lightmode":2
    "lightRcolor":0
    "lightGcolor":3
    "lightBcolor":255
}
```

The second command: 

```json
{
  "lightbright": 100
}
```

6. Set Light Color to night light

Note: Debugging found that after the mode is adjusted to night light, the light brightness will be adjusted to 100 by default at the same time, and then manually adjusted according to demand

The first command: 

```json
{
  "lightmode": 3
}
```

The second command: 

```json
{
  "lightbright": 100
}
```

7. Set light brightness to 30

```json
{
  "lightbright": 30
}
```

8. Single Timer

Set Aroma Diffuser to turn on at 14:31 on May 21, 2019, without repeating in a single execution.

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "once",
      "at": "2019-05-21T06:31:00.795Z",
      "type": "once",
      "do": {
        "switch": "on"
      },
      "mId": "7f28b51c-04a5-85f3-1ecf-9530f1164d1a"
    }
  ]
}
```

9. Delay Settings

Delay in turning off the Aroma Diffuser at 14:54 on May 21, 2019, without repeating in a single execution.

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "delay",
      "at": "2019-05-21T06:54:00.589Z",
      "period": "1",
      "type": "once",
      "do": {
        "switch": "off"
      },
      "mId": "d0129874-1f23-cd8a-77ea-d1356128eeb6"
    }
  ]
}
```

Note:

-  coolkit_timer_type: timer's type, delay is a type of delay, only single execution, can be enabled/disabled.
- do: The action that needs to be performed by the device, the action that can be performed by Aroma Diffuser delay is the light switch,  state: turn on (on), turn off (off)

10. Indicator's Always-off Switch Setting

Turn on Always-off Switch of aroma diffuser's indicator, turn off indicator

```json
{
  "sledOnline": "on"
}
```

- sledOnline: Always-on indicator on the device, turn off indicator (on), turn on indicator (off)

### UIID27 GSM/4G Single-Channel Switching Packet Traffic

Consistent with UIID1

### UIID28 RFBridge

#### Parameter Description:

| Parameter Name | Data Type | Value Range                                 | Parameter Description                                                                                                                                                                     |
| -------------- | --------- | ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| remote_type    | String    | 1,2,3,4,5,6                                 | Remote Control Type: 1 Single button; 2 Dual button; 3 Three buttons; 4 Four buttons; 5 Curtain; 6 Alarm                                                                                  |
| cmd            | String    | capture,captureCancel,edit,transmit,trigger | Instruction, Enter button learning mode (capture); Exit learning mode (captureCancel); Edit channel list (edit); Trigger buttons (transmit); Trigger notifications from devices (trigger) |
| rfChl          | Number    |                                             | The serial number of the button, which needs to be incremented when adding                                                                                                                |

Note: Adding an RF gateway device is no different than adding a regular WiFi device, which typically supports quick pairing and compatible pairing modes.

There is a limit to the number of remote controls that can be added to a device, so check: The devConfig configuration item in the device information (deviceList lists item Description). Usually only 4 remote control groups can be added, some product models can support 16 remote control groups.

devConfig Parameter Description:

For example, the following example means the firmware version is greater than or equal to 2.7.0 to support the addition of 16 remote controls, without this parameter only 4 remote control groupss are allowed to be added by default.

```json
{
  "devConfig": {
    "remoteInfos": [
      {
        "numberOfRemote": 16,
        "fwVersion": "2.7.0"
      }
    ]
  }
}
```

APP adds single remote control (Unlearned):

Request Set the device label interface (/v2/device/tags)

Example:

```shell
curl --location --request POST 'https://as-apia.coolkit.cc/v2/device/tags' \
--header 'X-CK-Nonce: {{nonce}}' \
--header 'Authorization: Bearer {{accessToken}}' \
--header 'Content-Type: application/json' \
--data-raw '{"deviceid":"1000xxxx","type":"merge","tags":{"zyx_info": [{"remote_type":"1","name":"My Remote","buttonName":[{"0":"Button1"}]}]}}'
```

APP adds multi-channel remote control (Unlearned):

```shell
curl --location --request POST 'https://as-apia.coolkit.cc/v2/device/tags' \
--header 'X-CK-Nonce: {{nonce}}' \
--header 'Authorization: Bearer {{accessToken}}' \
--header 'Content-Type: application/json' \
--data-raw '{"deviceid":"1000xxxx","type":"merge","tags":{"zyx_info": {"remote_type":"2","name":"My Remote","buttonName":[{"1":"Button1"},{"2":"Button2"}]}]}}'
```

APP adds Alarm (Unlearned):

```shell
curl --location --request POST 'https://as-apia.coolkit.cc/v2/device/tags' \
--header 'X-CK-Nonce: {{nonce}}' \
--header 'Authorization: Bearer {{accessToken}}' \
--header 'Content-Type: application/json' \
--data-raw '{"deviceid":"1000xxxx","type":"merge","tags":{"zyx_info": {"remote_type":"6","name":"My Remote","buttonName":[{"4":"Button1"}]}]}}'
```

#### Control Command:

1. APP puts the device into learn button mode

```json
{
  "action": "update",
  "deviceid": "1000xxxx",
  "apikey": "User apikey",
  "selfApikey": "User apikey",
  "params": { "cmd": "capture", "rfChl": 0 },
  "sequence": "1574303626706",
  "userAgent": "app"
}
```

APP receives server message:

```json
{
  "error": 0,
  "deviceid": "xxx",
  "apikey": "User apikey",
  "sequence": "1574303626706"
}
```

After successful learning, the app will also receive a message that the contents of the long connection params are the buttons that have finally been learned (The rfChl value is used for subsequent control), tags just stores information such as Name, which indicates that some remote control has been added.

APP receives server message:

```json
{
  "action": "update",
  "deviceid": "xxx",
  "apikey": "User apikey",
  "userAgent": "device",
  "d_seq": 1574303644676,
  "ts": 0,
  "params": {
    "rfList": [
      { "rfChl": 0, "rfVal": "29EA015E04245575C0" },
      { "rfChl": 1, "rfVal": "29A4015E0424557530" },
      { "rfChl": 3, "rfVal": "29AE015E041A557503" }
    ]
  },
  "from": "device"
}
```

Take the device out of learning mode:

```json
{
  "action": "update",
  "deviceid": "1000xxxx",
  "apikey": "User apikey",
  "selfApikey": "User apikey",
  "params": { "cmd": "captureCancel" },
  "sequence": "1574303626706",
  "userAgent": "app"
}
```

2. APP Update Channel List

When users modify (learn, delete) the channel list via APP, they need to update the new list to the device.

APP sends commands to the device

```json
{
  "action": "update",
  "deviceid": "1000xxxx",
  "apikey": "User apikey",
  "selfApikey": "User apikey",
  "params": {
    "cmd": "edit",
    "rfList": [
      { "rfChl": 0, "rfVal": "29EA015E04245575C0" },
      { "rfChl": 1, "rfVal": "29A4015E0424557530" },
      { "rfChl": 3, "rfVal": "29AE015E041A557503" }
    ]
  },
  "sequence": "1574303626706",
  "userAgent": "app"
}
```

APP sends trigger key command:

```json
{
  "action": "update",
  "deviceid": "xxx",
  "apikey": "User apikey",
  "selfApikey": "User apikey",
  "params": { "cmd": "transmit", "rfChl": 1 },
  "sequence": "1574305990342",
  "userAgent": "app"
}
```

3. APP receives a trigger notification (alarm) from the device

```json
{
  "action": "update",
  "deviceid": "xxx",
  "apikey": "User apikey",
  "userAgent": "device",
  "ts": 0,
  "params": { "cmd": "trigger", "rfTrig0": "2020-09-21T02:34:14.000Z" },
  "from": "device"
}
```

### UIID29 GSM/4G Dual-Channel Switch or Plug

Consistent with UIID2

### UIID31 GSM/4G Four-Channel Switch or Plug

Consistent with UIID4

### UIID32 Power Detection Plug Overload Alarm

The basic function remains the same as UIID5, but UIID32 adds the overload protection function.

Set overload protection to automatically shut down the device, e.g. minimum real-time power 200W, maximum real-time power 1500W, current 20A, voltage 240V.

```json
{
  "alarmType": "pcv",
  "alarmVValue": [-1, 240],
  "alarmCValue": [-1, 20],
  "alarmPValue": [200, 1500]
}
```

Field Description:

1. alarmType: String Type, Type of overload protection setting, mandatory, The value range is, "p" that is power protection, "v" that is voltage protection, "c" that is current protection any combination of the three, it can contain one of them, two of them, or three of them, depending on the settings of the other three fields.For example, if the user has set only current overload protection and no voltage and power settings (i.e., default values), the alarmType takes the value "c"; If the user has set power overload protection and voltage overload protection, but no current overload protection is set (i.e., the default value), the alarmType takes the value "pv"; If the user sets the power overload protection, current overload protection and voltage overload protection, the alarmType takes the value "pcv".
2. alarmVValue: Array Type, mandatory, The internal element is number Type, which indicates the setting value of the voltage protection, Unit is V, The first element is the lower threshold of voltage protection and the second element is the upper threshold of voltage protection.
3. alarmCValue: Array Type, mandatory, The internal element is number Type, which indicates the setting value of the current protection, Unit is A, The first element is the lower threshold of current protection and the second element is the upper threshold of current protection.
4. alarmPValue: Array Type, mandatory, The internal element is number Type, which indicates the setting value of the power protection, Unit is W, The first of these elements is the lower threshold limit for power protection.

Note:

1. The upper threshold limit for voltage protection, current protection, and power protection must be greater than the lower threshold limit, except in the case where neither the upper nor lower threshold limit is set.
2. By default, current protection, voltage protection, and power protection are not set, and their default lower and upper thresholds are -1.
3. It is possible to set only the upper threshold or the lower threshold, while the value of the unset upper or lower threshold is -1 .
4. The upper and lower thresholds for current-voltage power take the following ranges:
   - Current: The upper threshold Value Range is [0.10 , 15.00] and there is no lower threshold.
   - Voltage: The upper threshold Value Range is [0.10 , 300.00] and there is no lower threshold value.
   - Power: The upper threshold Value Range is [10.00 , 3300.00] and the lower threshold Value Range is [0.10 , 3300.00].
5. Up to 2 decimal places are supported on the device side for all the above threshold protection setting values.

### UIID33 RGB Strip Controller

#### Parameter Description:

| Parameter Name     | Data Type | Value Range | Parameter Description                                                                            |
| ---------- | -------- | -------- | ----------------------------------------------------------------------------------- |
| switch     | String   | on,off   | Switch, turn on (on), turn off (off)                                                   |
| light_type | Number   | 1,2      | Type, 1 color light, 2 white light                                                    |
| bright     | Number   | [10,100] | Brightness, Range: 10-100, The higher the value, the brighter it is                                                   |
| colorR     | Number   | [0,255]  | R value, Red Outlet Range 0-255                                                            |
| colorG     | Number   | [0,255]  | G value, Green Outlet Range 0-255                                                            |
| colorB     | Number   | [0,255]  | B value, Blue Outlet Range 0-255                                                            |
| mode       | Number   | [1,3]    | Mode, there are 3 modes: 1 static, 2 gradual, 3 jump                               |
| speed      | Number   | [0,100]  | Speed, range:  0-100, The higher the value, the faster the speed                                |
| timers     | Array    |          | Timer Type, timer: once (Single execution); repeat (repeat execution); delay: delay (Single execution only) |

#### Control Command:

**Note: With the lights off, you can only turn on the lights, not by adjusting the color temperature and brightness to turn on the lights.**

1. turn on light strip

```json
{
  "switch":"on" // turn on (on), turn off (off)
}
```

Select a color RGB value [255,63,0] on the color palette, light_type is 1 means color light, at this time the default mode (mode 1)'s light is static display, if drag and drop to adjust the color temperature progress bar will exit the color palette color selection state

```json
{
  "mode":1,
  "colorR":255,
  "colorB":63,
  "colorG":0,
  "light_type":1
}
```

2. Adjust Brightness

Adjust brightness to 55, light_type 1 color light or 2 adjust brightness under white light, brightness Value Range: 10-100, the higher the value, the bright it is, default mode 1 is static mode

```json
{
  "mode":1,
  "bright":55
}
```

3. Adjust Color Temperature

Adjust the color temperature of light strip to warm light, with RGB channel value to indicate the color temperature value, RGB value corresponds to the color temperature 142 steps (see list), light_type is 2 means that the white light can be adjusted to color temperature (warm and cold), at this time the default mode 1 is static mode

```json
{
  "mode": 1,
  "colorR": 255,
  "colorB": 11,
  "colorG": 141,
  "light_type": 2
}
```

The color temperature values are listed below:

```
["#d6e1ff", "#d9e1ff", "#d7e2ff", "#dae2ff", "#d8e3ff", "#dbe2ff", "#d9e3ff", "#dce3ff", "#dae4ff", "#dde4ff", "#dce5ff", "#dfe5ff", "#dde6ff", "#e0e6ff", "#dee6ff", "#e1e7ff", "#e0e7ff", "#e3e8ff", "#e1e8ff", "#e4e9ff", "#e3e9ff", "#e5e9ff", "#e4eaff", "#e7eaff", "#e6ebff", "#e9ecff", "#e7ecff", "#eaedff", "#e9edff", "#eceeff", "#ebeeff", "#eeefff", "#edefff", "#eff0ff", "#eff0ff", "#f1f1ff", "#f0f1ff", "#f3f3ff", "#f3f2ff", "#f5f4ff", "#f5f3ff", "#f7f5ff", "#f7f5ff", "#faf7ff", "#f9f6ff", "#fcf8ff", "#fcf7ff", "#fefaff", "#fef9ff", "#fff9fd", "#fff9fd", "#fff9fb", "#fff8fb", "#fff8f8", "#fff6f8", "#fff7f5", "#fff5f5", "#fff6f3", "#fff4f2", "#fff5f0", "#fff3ef", "#fff4ed", "#fff2ec", "#fff3ea", "#fff0e9", "#fff1e7", "#ffefe6", "#fff0e4", "#ffeee3", "#ffefe1", "#ffece0", "#ffeede", "#ffebdc", "#ffedda", "#ffe9d9", "#ffebd7", "#ffe8d5", "#ffead3", "#ffe6d2", "#ffe8d0", "#ffe4ce", "#ffe7cc", "#ffe3ca", "#ffe5c8", "#ffe1c6", "#ffe4c4", "#ffdfc2", "#ffe2c0", "#ffddbe", "#ffe1bc", "#ffdbba", "#ffdfb8", "#ffd9b6", "#ffddb4", "#ffd7b1", "#ffdbaf", "#ffd5ad", "#ffd9ab", "#ffd3a8", "#ffd7a6", "#ffd1a3", "#ffd5a1", "#ffce9f", "#ffd39c", "#ffcc99", "#ffd097", "#ffc994", "#ffce92", "#ffc78f", "#ffcb8d", "#ffc489", "#ffc987", "#ffc184", "#ffc682", "#ffbe7e", "#ffc37c", "#ffbb78", "#ffc076", "#ffb872", "#ffbd6f", "#ffb46b", "#ffb969", "#ffb165", "#ffb662", "#ffad5e", "#ffb25b", "#ffa957", "#ffae54", "#ffa54f", "#ffaa4d", "#ffa148", "#ffa645", "#ff9d3f", "#ffa23c", "#ff9836", "#ff9d33", "#ff932c", "#ff9829", "#ff8e21", "#ff921d", "#ff8912", "#ff8d0b"]
```

4. Set light Strip Mode

Set light strip mode to gradual mode, Default speed is 50, mode 1 static, 2 gradual, 3 jump

```json
{
  "mode": 2,
  "speed": 50
}
```

Under gadual mode, set the speed to 100, range: 0-100, The higher the value, the faster the speed

```json
{
  "mode": 2,
  "speed": 100
}
```

5. Single Timer

Set light strip to turn on at 15:32 on July 2, 2019, without repeating in a single execution


```json
{
  "timers":[
            {
                "enabled":1,
                " coolkit_timer_type":"once",
                "at":"2019-07-02T07:32:00.689Z",
                "type":"once",
                "do":{
                    "switch":"on"
                },
                "mId":"a824f44b-af76-ff8d-6fcc-6d897d93810f"
            }
        ]
}
```

Note:

-  coolkit_timer_type: timer's type, delay is a type of delay, only single execution, can be enabled/disabled.
- do: The action that needs to be performed by the device, the action that can be performed by RGB Strip Controller is the light switch,  state: turn on (on), turn off (off)

Set light strip to turn off at 15:40 on July 2, 2019, with an 8 minute delay at 15:32, without repeating in a single execution

6. Delay

```json
{
  "timers":[
            {
                "enabled":1,
                " coolkit_timer_type":"delay",
                "at":"2019-07-02T07:40:00.057Z",
                "period":"8",
                "type":"once",
                "do":{
                    "switch":"off"
                },
                "mId":"2b02614d-e5fd-ec3b-ad44-9637b06511a4"
            }
        ]
}
```

### UIID34 Smart Fan Light

#### Parameter Description:

| Parameter Name   | Data Type | Value Range | Parameter Description                                                                                                                                                                                                                                                                                 |
| -------- | -------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| switches | Array    |          | Switch status of all channels                                                                                                                                                                                                                                                                       |
| switch   | String   | on,off   | Switches of channels: turn on (on), turn off (off)                                                                                                                                                                                                                                                            |
| outlet   | Number   | [0,3]    | Value Range 0-3, Indicates channel 1-4 respectively, cannot be repeated. Turn on light: turn on channel 1; Turn off light: turn off channel 1; Low speed: turn on channel 2, turn off channel 3 and 4; Middle speed: turn on channel 2 and 3, turn off channel 4; high level: turn on channel 2 and 4, turn off channel 3; turn off fan: turn off channel 2;  Schedule to turn on: turn on channel 1 (Supports lights on only);  Schedule to turn off: turn off channel 1 (Supports lights off only) |
| timers   | Array    |          | Timer Type, timer: once (Single execution); repeat (repeat execution); delay: delay (Single execution only)                                                                                                                                                                                                      |

#### Control Command:

1. Turn on light, turn on channel 1

```json
{
  "switches": [
    {
      "switch": "on",
      "outlet": 0
    },
    {
      "outlet": 1,
      "switch": "off"
    },
    {
      "outlet": 2,
      "switch": "off"
    },
    {
      "outlet": 3,
      "switch": "off"
    }
  ]
}
```

2. Turn off light, turn off channel 1

```json
{
  "switches": [
    {
      "switch": "off",
      "outlet": 0
    },
    {
      "outlet": 1,
      "switch": "off"
    },
    {
      "outlet": 2,
      "switch": "off"
    },
    {
      "outlet": 3,
      "switch": "off"
    }
  ]
}
```

3. Set the fan light to low speed, turn on channel 2, turn off channel 3 and 4 and adjust the fan speed i.e. turn on the fan

```json
{
  "switches": [
    {
      "switch": "off",
      "outlet": 0
    },
    {
      "outlet": 1,
      "switch": "on"
    },
    {
      "outlet": 2,
      "switch": "off"
    },
    {
      "outlet": 3,
      "switch": "off"
    }
  ]
}
```

4. Set the fan light to medium speed, turn on channel 2 and 3, turn off channel 4 and adjust the fan speed i.e. turn on the fan

```json
{
  "switches": [
    {
      "switch": "off",
      "outlet": 0
    },
    {
      "outlet": 1,
      "switch": "on"
    },
    {
      "outlet": 2,
      "switch": "on"
    },
    {
      "outlet": 3,
      "switch": "off"
    }
  ]
}
```

5. Set the fan light to high speed, turn on channel 2 and 4, turn off channel 3 and adjust the fan speed i.e. turn on the fan

```json
{
  "switches": [
    {
      "switch": "off",
      "outlet": 0
    },
    {
      "outlet": 1,
      "switch": "on"
    },
    {
      "outlet": 2,
      "switch": "off"
    },
    {
      "outlet": 3,
      "switch": "on"
    }
  ]
}
```

6. Turn off Fan, turn off channel 2

```json
{
  "switches": [
    {
      "switch": "off",
      "outlet": 0
    },
    {
      "outlet": 1,
      "switch": "off"
    },
    {
      "outlet": 2,
      "switch": "off"
    },
    {
      "outlet": 3,
      "switch": "on"
    }
  ]
}
```

7. Single Timer

Set the light to turn on at 19:10 on May 31, 2019, turn on channel 1, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "once",
      "at": "2019-05-31T11:10:00.297Z",
      "type": "once",
      "do": {
        "switch": "on",
        "outlet": 0
      },
      "mId": "86cbee4b-a824-0709-cdef-c0a632daf49e"
    }
  ]
}
```

Note:

-  coolkit_timer_type: timer's type, once in timer type means single execution, repeat is repeat execution, can be enabled/disabled.
- do: The action that needs to be performed by the device, the action that can be performed by fan light delay is the light switch, turn on (on), turn off (off)

8. Delay Setting

Set the light to turn off at 19:11 on May 31, 2019, turn off channel 1, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "delay",
      "at": "2019-05-31T11:11:00.856Z",
      "period": "1",
      "type": "once",
      "do": {
        "switch": "off",
        "outlet": 0
      },
      "mId": "c8194956-97c3-79bb-5510-00e0a89b6f68"
    }
  ]
}
```

### UIID36 Single Dimmer Switch

#### Parameter Description:

| Parameter Name     | Data Type | Value Range | Parameter Description                                                                            |
| ---------- | -------- | -------- | ----------------------------------------------------------------------------------- |
| switch     | String   | on,off   | Switch, turn on (on), turn off (off)                                           |
| bright     | Number   | 10,100   | Brighness Adjustment, Value Range 10-100, The higher the value, the brighter it is                           |
| sledOnline | String   | on,off   | Always-off switch, turn on (on), turn off (off)                                                         |
| timers     | Array    |          | Timer Type, timer: once (Single execution); repeat (repeat execution); delay: delay (Single execution only) |

#### Control Command:

Note: With the lights off, only the lights can be turned on and the color temperature and brightness cannot be adjusted.

1. Turn on Single Dimmer Switch, turn on (on), turn off (off)

```json
{
  "switch": "on"
}
```

2. Adjust the brightness to 57, Value Range 10-100

```json
{
  "bright": 57
}
```

3. Set the Always-off switch to turn off, turn on (on), turn off (off)

```json
{
  "sledOnline": "off"
}
```

4. Set the Single Dimmer Switch to turn on at 12:06 pm, on June 18, 2019, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "once",
      "at": "2019-06-18T04:06:00.102Z",
      "type": "once",
      "do": {
        "switch": "on"
      },
      "mId": "56aa6c9e-5bcc-6e4a-2333-f6f2f16808ac"
    }
  ]
}
```

Note:

-  coolkit_timer_type: timer's type, once in timer type means single execution, repeat is repeat execution, can be enabled/disabled.
- do: The action that needs to be performed by the device, the action that can be performed by Single Dimmer Switch delay is the light switch, turn on (on), turn off (off)

5. Set the single dimmer switch to close at 12.11 pm on 18 June 2019, with a delay of 5 minutes at 12.06 pm, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "delay",
      "at": "2019-06-18T04:11:00.268Z",
      "period": "5",
      "type": "once",
      "do": {
        "switch": "off"
      },
      "mId": "df96f3d4-0729-135d-2fe9-6b0bfce065eb"
    }
  ]
}
```

### UIID52 Dimmable Color Temperature Ceiling Light

#### Parameter Description:

| Parameter Name   | Data Type | Value Range  | Parameter Description                                                                            |
| -------- | -------- | --------- | ----------------------------------------------------------------------------------- |
| state    | String   | on,off    | Switch, turn on (on), turn off (off)                                                 |
| channel0 | String   | [10,255]  | Brightness Adjustment, Value Range 10-255, 10 is white light, 255 is yellow light                      |
| channel1 | String   | [0,255]   | Color Temperature Adjustment, Value Range 0-255, The higher the value, the warmer it is                                  |
| timers   | Array    |           | Timer Type, timer: once (Single execution); repeat (repeat execution); delay: delay (Single execution only) |
| timeZone |          | [-12,+14] | "-" represents Western Time Zone, "+" represents Eastern Time Zone                                                            |

#### Control Command:

Note: With the lights off, only the lights can be switched on and the color temperature and brightness cannot be adjusted; 

If you need to adjust the ceiling light as a night light, adjust the ceiling light brightness value (channel 0) to 10 and the ceiling light color temperature value (channel 1) to 255

1. Turn on ceiling light, turn on (on), turn off (off)

```json
{
  "state": "on"
}
```

2. Set the brightness to 132, Value Range 10-255

```json
{
  "channel0": "132"
}
```

3. set color temperature to 57, Value Range 0-255

```json
{
  "channel1": "57"
}
```

4. Adjust ceiling light to night light

```json
{
  "channel0": "10",
  "channel1": "255"
}
```

5. Set the ceiling light to turn on at 17:08 on May 29, 2019, without repeating in a single execution

```json
{
"timers":[
            {
                "enabled":1,
                " coolkit_timer_type":"once",
                "at":"2019-05-29T09:08:00.315Z",
                "type":"once",
                "do":{
                    "state":"on"
                },
                "mId":"91959d3b-5885-718d-13c5-e69cd48de862"
            }
        ]
```

Note:

-  coolkit_timer_type: timer's type, once in timer type means single execution, repeat is repeat execution, can be enabled/disabled.
- do: The action that needs to be performed by the device, the action that can be performed by Ceiling Light delay is the light switch, turn on (on), turn off (off)

6. Set the ceiling light to turn off at 17:16 on 29 May 2019, with a delay of 6 minutes at 17:10, without repeating in a single execution

```json
{
"timers":[
            {
                "enabled":1,
                " coolkit_timer_type":"delay",
                "at":"2019-05-29T09:16:00.384Z",
                "period":"1",
                "type":"once",
                "do":{
                    "state":"off"
                },
                "mId":"e4777ab0-a74e-ed60-aeac-1ea23b112069"
            }
        ]
```

### UIID57 Single-Color Bulb Light

#### Parameter Description:

| Parameter Name   | Data Type | Value Range     | Parameter Description                                                                            |
| -------- | -------- | ------------ | ----------------------------------------------------------------------------------- |
| state    | String   | on,off       | Switch, turn on (on), turn off (off)                                             |
| channel0 | String   | ["25","255"] | Brightness Adjustment, Value Range 25-255, The higher the value, the brighter it is                             |
| timers   | Array    |              | Timer Type, timer: once (Single execution); repeat (repeat execution); delay: delay (Single execution only) |

#### Control Command:

Note: With the lights off, only the lights can be switched on and the color temperature and brightness cannot be adjusted.

1. Turn on Single-Color Bulb Light, turn on (on), turn off (off)

```json
{
  "state":"on"
}
```

2. Adjust brightness to 87, Value Range 25-255

```json
{
  "channel0":"132"
}
```

3. Set the Single-Color Bulb Light to turn on at 14:45 on June 14, 2019, without repeating in a single execution

```json
{
  "timers":[
            {
                "enabled":1,
                " coolkit_timer_type":"once",
                "at":"2019-06-14T09:45:00.495Z",
                "type":"once",
                "do":{
                    "state":"on"
                },
                "mId":"9be975c2-353f-3fbb-0f92-8a5cb0824389"
            }
        ]
}
```

Note:

-  coolkit_timer_type: timer's type, once in timer type means single execution, repeat is repeat execution, can be enabled/disabled.
- do: The action that needs to be performed by the device, the action that can be performed by Single-Color Bulb Light delay is the light switch, turn on (on), turn off (off)

4. Set the Single-Color Bulb Light to turn off at 17:50 on June 14, 2019, with a delay of 5 minutes at 17:45, without repeating in a single execution

```json
{
"timers":[
            {
                "enabled":1,
                " coolkit_timer_type":"delay",
                "at":"2019-06-14T09:50:00.959Z",
                "period":"5",
                "type":"once",
                "do":{
                    "state":"off"
                },
                "mId":"0b145b7c-a7f8-c98a-825b-b8586f335899"
            }
        ]
```

### UIID59 Light Strip

#### Parameter Description:

| Parameter Name     | Data Type | Value Range | Parameter Description                                                                                                                                                                                |
| ---------- | -------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| switch     | String   | on,off   | Switch, turn on (on), turn off (off)                                                                                                                                                       |
| light_type | Number   | 1,2      | Light Type, 1 color light(Color Plate), 2 white light(color temperature)                                                                                                                                        |
| bright     | Number   | [1,100]  | Brightness, Range 1-100, The higher the value, the brighter it is                                                                                                                                                        |
| colorR     | Number   | [0,255]  | R value, Red Outlet Range 0-255                                                                                                                                                                |
| colorG     | Number   | [0,255]  | G value, Green Outlet Range 0-255                                                                                                                                                                |
| colorB     | Number   | [0,255]  | B value, Blue Outlet Range 0-255                                                                                                                                                                |
| mode       | Number   | [1,12]   | There are 12 modes: 1 Colorful (normal), 2 Colorful Gradient, 3 Colorful Breath, 4 DIY Gradient, 5 DIY Pulse, 6 DIY Breath, 7 DIY Strobe, 8 RGB Gradient, 9 RGB Pulse, 10 RGB Breath, 11 RGB Strobe, 12 Music Visualization |
| speed      | Number   | [1,100]  |Fast and slow speed of change of light strip between different colors, Value Range 1-100, The higher the value, the faster the speed                                                                                                                        |
| sensitive  | Number   | [1,10]   | The sensitivity of the light changes in Music Visualization mode, Value Range 1-10, The higher the value, the higher the sensitivity                                                                                                                 |
| timers     | Array    |          | Timer Type, timer: once (Single execution); repeat (repeat execution); delay: delay (Single execution only)                                                                                                     |
| timeZone   | Number   | [-12,12] | Time zone, The time zone of the phone is sent to the device when the app is launched (LumiDock and LumiCharge3 models of aithinker brand only)                                                                                      |

#### Control Command:

Note: With the lights off, you can only turn on the lights, not by adjusting the color temperature and brightness to turn on the lights.

1. Turn on light strip, turn on (on), turn off (off)

```json
{
  "switch": "on"
}
```

2. Select a color RGB value [255,16,0] on the color palette, light_type is 1 means color light, at this time the default mode 1 is colorful mode, if drag and drop to adjust the color temperature, progress bar will exit the color palette color selection state

```json
{
  "mode": 1,
  "colorR": 255,
  "colorB": 16,
  "colorG": 0,
  "light_type": 1
}
```

3. Adjust the brightness of light strip to 53, brightness in light_type of either 1 color light or 2 white light can be adjusted, brightness Value Range is 1-100, the higher the value, the brighter it is, Mode 1 default is colorful mode

```json
{
  "mode": 1,
  "bright": 53
}
```

4. Adjust the color temperature of light strip to warm light, with RGB channel value to indicate the color temperature value, RGB value corresponds to the color temperature 142 steps (see list), light_type is 2 means the white light can be adjusted, color temperature (warm and cold), at this time the default mode 1 is colorful mode

```json
{
  "mode": 1,
  "colorR": 255,
  "colorB": 11,
  "colorG": 141,
  "light_type": 2
}
```

The color temperature values are listed below:

```
["#d6e1ff", "#d9e1ff", "#d7e2ff", "#dae2ff", "#d8e3ff", "#dbe2ff", "#d9e3ff", "#dce3ff", "#dae4ff", "#dde4ff", "#dce5ff", "#dfe5ff", "#dde6ff", "#e0e6ff", "#dee6ff", "#e1e7ff", "#e0e7ff", "#e3e8ff", "#e1e8ff", "#e4e9ff", "#e3e9ff", "#e5e9ff", "#e4eaff", "#e7eaff", "#e6ebff", "#e9ecff", "#e7ecff", "#eaedff", "#e9edff", "#eceeff", "#ebeeff", "#eeefff", "#edefff", "#eff0ff", "#eff0ff", "#f1f1ff", "#f0f1ff", "#f3f3ff", "#f3f2ff", "#f5f4ff", "#f5f3ff", "#f7f5ff", "#f7f5ff", "#faf7ff", "#f9f6ff", "#fcf8ff", "#fcf7ff", "#fefaff", "#fef9ff", "#fff9fd", "#fff9fd", "#fff9fb", "#fff8fb", "#fff8f8", "#fff6f8", "#fff7f5", "#fff5f5", "#fff6f3", "#fff4f2", "#fff5f0", "#fff3ef", "#fff4ed", "#fff2ec", "#fff3ea", "#fff0e9", "#fff1e7", "#ffefe6", "#fff0e4", "#ffeee3", "#ffefe1", "#ffece0", "#ffeede", "#ffebdc", "#ffedda", "#ffe9d9", "#ffebd7", "#ffe8d5", "#ffead3", "#ffe6d2", "#ffe8d0", "#ffe4ce", "#ffe7cc", "#ffe3ca", "#ffe5c8", "#ffe1c6", "#ffe4c4", "#ffdfc2", "#ffe2c0", "#ffddbe", "#ffe1bc", "#ffdbba", "#ffdfb8", "#ffd9b6", "#ffddb4", "#ffd7b1", "#ffdbaf", "#ffd5ad", "#ffd9ab", "#ffd3a8", "#ffd7a6", "#ffd1a3", "#ffd5a1", "#ffce9f", "#ffd39c", "#ffcc99", "#ffd097", "#ffc994", "#ffce92", "#ffc78f", "#ffcb8d", "#ffc489", "#ffc987", "#ffc184", "#ffc682", "#ffbe7e", "#ffc37c", "#ffbb78", "#ffc076", "#ffb872", "#ffbd6f", "#ffb46b", "#ffb969", "#ffb165", "#ffb662", "#ffad5e", "#ffb25b", "#ffa957", "#ffae54", "#ffa54f", "#ffaa4d", "#ffa148", "#ffa645", "#ff9d3f", "#ffa23c", "#ff9836", "#ff9d33", "#ff932c", "#ff9829", "#ff8e21", "#ff921d", "#ff8912", "#ff8d0b"]

```

5. Select colorful mode, mode 1, Mode default is 1

Mode Value Range 1-12: 1 Colorful, 2 Colorful Gradient, 3 Colorful Breath, 4 DIY Gradient, 5 DIY Pulse, 6 DIY Breath, 7 DIY Strobe, 8 RGB Gradient, 9 RGB Pulse, 10 RGB Breath, 11 RGB Strobe, 12 Music Visualization, Just select different modes and send different mode values

```json
{
  "mode": 1,
  "switch": "on"
}
```

6. Select colorful Gradient mode, mode 2

```json
{
  "mode": 2,
  "switch": "on"
}
```

7. Select Colorful Breath mode, mode 3

```json
{
  "mode": 3,
  "switch": "on"
}
```

8. Chosse DIY Gradient mode, mode 4

```json
{
  "mode": 4,
  "switch": "on"
}
```

Press and hold the "DIY Gradient" button to enter edit mode and adjust the speed of light change for different colors to 67, speed, Value Range 1-100, The higher the value, the faster the speed

```json
{
  "speed": 67,
  "mode": 4
}
```

In DIY gradient mode editing state, select the red gradient, RGB Value[255,0,0], mode 4, DIY Gradient mode, light_type 1 color light

```json
{
  "mode": 4,
  "colorR": 255,
  "colorG": 0,
  "colorB": 0,
  "light_type": 1,
  "switch": "on"
}
```

9. Select DIY Pulse mode, mode 5

```json
{
  "mode": 5,
  "switch": "on"
}
```

Long press the "DIY Pulse" button to enter editing mode and adjust the speed of different color light changes to 25, speed, Value Range 1-100, The higher the value, the faster the speed

```json
{
  "speed": 25,
  "mode": 5
}
```

In DIY Pulse mode enditing state, Select the Pulse color of RGB value [28,44,255] in the color palette, mode 5, DIY Pulse mode, light_type 1 color light

```json
{
  "mode": 5,
  "colorR": 28,
  "colorG": 44,
  "colorB": 255,
  "light_type": 1,
  "switch": "on"
}
```

10. Select DIY Breath mode, mode 6

```json
{
  "mode": 6,
  "switch": "on"
}
```

Press and hold the "DIY Breath" button to enter edit mode and adjust the speed of light change between colors to 100, speed, Value Range 1-100, The higher the value, the faster the speed

```json
{
  "speed": 100,
  "mode": 6
}
```

In the DIY breath mode editing state, select the jump color of RGB value [255,0,230] in the color palette, mode 6 DIY Breath mode, light_type 1 color light

```json
{
  "mode": 6,
  "colorR": 255,
  "colorG": 0,
  "colorB": 230,
  "light_type": 1,
  "switch": "on"
}
```

11. Select DIY Strobe mode, mode 7

```json
{
  "mode": 7,
  "switch": "on"
}
```

Press and hold the "DIY strobe" button to enter edit mode and adjust the speed of different color light changes to 1, speed, Value Range 1-100, The higher the value, the faster the speed

```json
{
  "speed": 1,
  "mode": 6
}
```

In DIY strobe mode edit state, select the strobe color with RGB value [255,136,0] in the color palette, mode 7, DIY Strobe mode, light_type 1 color light

```json
{
  "mode": 7,
  "colorR": 255,
  "colorG": 136,
  "colorB": 0,
  "light_type": 1,
  "switch": "on"
}
```

12. Select RGB Gradient mode, mode 8

```json
{
  "mode": 8,
  "switch": "on"
}
```

13. Select RGB Pulse mode, mode 9

```json
{
  "mode": 9,
  "switch": "on"
}
```

14. Select RGB Breath mode, mode 10

```json
{
  "mode": 10,
  "switch": "on"
}
```

15. Select RGB Strobe mode, mode 11

```json
{
  "mode": 11,
  "switch": "on"
}
```

16. Select Music Visualization mode, mode 12

```json
{
  "mode": 12,
  "switch": "on"
}
```

Press and hold the "Music Visualization" button to enter editing mode, use the device controller to listen to the music being played and adjust the color and brightness of the lights according to the speed of the music, at a speed of 47, speed, Value Range 1-100, The higher the value, the faster the speed

```json
{
  "speed": 47,
  "mode": 6
}
```

"In the "Music Visualization" mode editing state, adjust the color shift level to 10, sensitive, Value Range 1-10, The higher the value, the faster the color transition

```json
{
  "mode": 12,
  "sensitive": 10
}
```

17. Set light strip to turn on at 12:15 pm on July 2, 2019, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "once",
      "at": "2019-07-02T04:15:00.278Z",
      "type": "once",
      "do": {
        "switch": "on"
      },
      "mId": "4d5fbdaf-d1c3-caf1-1b34-7c5f26dbdf0c"
    }
  ]
}
```

Note:

-  coolkit_timer_type: timer's type, once in timer type means single execution, repeat is repeat execution, can be enabled/disabled.
- do: The action that needs to be performed by the device, the action that can be performed by light strip delay is the light switch, turn on (on), turn off (off)

18. Set the light strip to turn off at 12:21 pm on July 2, 2019, with a 6 minute delay of 12:15 pm, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      " coolkit_timer_type": "delay",
      "at": "2019-07-02T04:21:00.934Z",
      "period": "6",
      "type": "once",
      "do": {
        "switch": "off"
      },
      "mId": "5e91ffd7-716f-21c3-8458-6931c442b88a"
    }
  ]
}
```

### UIID66 Zigbee Gateway

The sub-device management process is not listed here, please contact technical support for complete documentation, which is not available to unpaid developers.

#### Parameter Description:

<div class="table-center">

| Parameter Name | Data Type      | Value Range | Parameter Description                                                                                                                                                                                 |
| -------------- | -------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| battery        | Number         | [0,100]     | Battery level                                                                                                                                                                                         |
| trigTime       | String         |             | The 13-bit timestamp of the last reported status, accurate to Millisecond. the device needs to guarantee the accuracy of the time, and the server and APP history are stored according to this value. |
| smoke          | Number         | [0,1]       | Smoke or no smoke status is detected. 0 no smoke, 1 Smoke                                                                                                                                             |
| motion         | Number         | [0,1]       | Detects occupied or unoccupied states. 0 unoccupied, 1 occupied                                                                                                                                       |
| lock           | Number         | [0,1]       | Open or closed door is detected. 0 closed, 1 Open                                                                                                                                                     |
| water          | Number         | [0,1]       | Water is detected or not. 0 no water, 1 water                                                                                                                                                         |
| key            | Number         | [0,2]       | Key triggering on behalf of wireless keys, 0 Click, 1 Double click, 2 Long press                                                                                                                      |
| switches       | Array\<Object> | [1-4]       | The set of switch states of all channels, in the range of the number of elements[1-4]                                                                                                                 |
| brightness     | Number         | [1-100]     | Brightness, the range of values expressed as a percentage of brightness                                                                                                                               |
| rgbBrightness  | Number         | [1-100]     | Brightness percentage in RGBCW LED Light color light mode                                                                                                                                            |
| cctBrightness  | Number         | [1-100]     | Brightness percentage in white light mode of five-color - RGBCW                                                                                                                                           |
| colorTemp      | Number         | [1-100]     | Color temperature, the range of values expressed as a percentage of the color temperature range that can be supported by the sub device (0: warm yellow minimum; 100: white light maximum)            |
| hue            | Number         | [0-359]     | Hue, using the standard hue ring, 3 o'clock direction is 0 (red), counterclockwise by 1° increments                                                                                                   |
| saturation     | Number         | [1-100]     | Color saturation, Value Range indicates saturation percentage                                                                                                                                         |
| colorMode      | Number         | "cct","rgb" | Target color mode, cct means white light mode, rgb means color light mode                                                                                                                             |

</div>

#### UIID1000 Zigbee Wireless Button

```json
{
  "key": 0, // 0 click, 1 double click, 2 long press
  "battery": 50, //0-100 represents the electricity division ratio
  "trigTime": "1234567890123" //13-bit string, Timestamp, consistent with server time
}
```

Parameter Description:

- key: Types of key-triggered events, Number type. Value Range: [0,2], 0 click, 1 double click, 2 long press
- battery: Battery Power Ratio, Number type. Value Range[0,100]
- trigTime: trigger time, String type. Takes the value of the 13-bit timestamp of the last reported status, accurate to the millisecond.

Usage Scenario:

When the device creates a keypress event, it pushes the relevant update command to the cloud. app receives the command and displays a list of events.

#### UIID1009 Zigbee Single-Channel Plug

```json
{
  "switch": "on"
}
```

Parameter Description:

switch: Channel Status, String type. Take value: on/off, Indicates channel on/off, The default is on when the addition is complete.

Usage Scenario:

- Device updates its own status;
- Set device state via the app

Set timer:

```json
{
  "timers": [
    {
      //delay
      "mId": "6bdfc96c-0962-ad75-c430-15d9eb351154",
      "type": "once",
      "at": "2020-12-16T18:37:00.761Z",
      "coolkit_timer_type": "delay",
      "enabled": 1,
      "do": {
        "switch": "on"
      },
      "period": "390"
    },
    {
      //Single Timer
      "mId": "c5601da9-aa5f-0946-a1fd-2a2a35daf59a",
      "type": "once",
      "at": "2020-12-16T13:11:00.974Z",
      "coolkit_timer_type": "once",
      "enabled": 1,
      "do": {
        "switch": "on"
      }
    },
    {
      //Repeat timer
      "mId": "870262af-4f9c-7d23-318b-f65d5a79d3eb",
      "type": "repeat",
      "at": "6 15 * * 0,1,2,3,4,5,6",
      "coolkit_timer_type": "repeat",
      "enabled": 1,
      "do": {
        "switch": "on"
      }
    },
    {
      //Loop timer-repeat Perform a turn-on every 30 minutes from the start time until the device is turned on
      "mId": "fcfd83d5-4c8c-50c6-73e8-aeadeac5abdc",
      "type": "duration",
      "at": "2020-12-16T15:23:00.140Z 30",
      "coolkit_timer_type": "duration",
      "enabled": 1,
      "do": {
        "switch": "on"
      }
    },
    {
      //Loop timer-alternate Every 60 minutes cycle, from start time to turn off the device, 30 minutes to turn on the device, 30 minutes to turn off the device...
      "mId": "fcfd83d5-4c8c-50c6-73e8-aeadeac5abdc",
      "type": "duration",
      "at": "2020-12-16T15:23:00.140Z 60 30",
      "coolkit_timer_type": "duration",
      "enabled": 1,
      "startDo": {
        "switch": "off"
      },
      "endDo": {
        "switch": "on"
      }
    }
  ]
}
```

#### UIID1256 Zigbee Single-Channel Switch

The protocol and functions are basically the same as those of the UIID1009.

#### UIID1257 Zigbee Monochrome Light

Turn on/off device:

```json
{
  "switch": "on" // turn on (on), turn off (off)
}
```

Parameter Description:

switch: Channel Status, String type. Take value: on/off, Indicates channel on/off, The default is on when the addition is complete.

Usage Scenario:

- APP Sets sub-device channel status
- Report any change in the local status of sub-device
- Synchronize sub-device channel status to APP when the device is online

Set brightness:

```json
{
  "switch": "on",
  "brightness": 100 // Brightness percentage
}
```

Parameter Description:

- switch: Channel status, mandatory, String type, The value must be on;
- brightness: Brightness percentage, mandatory, Number type, Value Range: [1 - 100]; Sub-device is added. Brightness is 100% by default.

Usage Scenario:

APP Sets sub-device brightness

#### UIID1258 Zigbee Dual-Color Light

Turn on/off light:

```json
{
  "switch": "on" // turn on (on), turn off (off)
}
```

Parameter Description:

switch: Channel status, mandatory, String type, takes the value on/off, indicate channel on/off, the default is on when the addition is complete.

Usage Scenario:

- APP Sets sub-device channel status
- Report any change in the local status of sub-device
- Synchronize sub-device channel status to APP when the device is online

Set brightness:

```json
{
  "switch": "on",
  "brightness": 100 // Brightness percentage
}
```

Parameter Description:

- switch: Channel status, mandatory, String type, The value must be on;
- brightness: Brightness percentage, mandatory, Number type, Value Range[1 - 100]; Sub-device is added, brightness is 100% by default.

Usage Scenario: APP Sets sub-device brightness

Set color temperature:

```json
{
  "switch": "on",
  "colorTemp": 100
}
```

Parameter Description:

- switch: Channel status, mandatory, String type, The value must be on;
- colorTemp: Color temperature, mandatory, Number type, Value Range: [0 - 100]; When sub-device is added, the default color temperature is cold, and the default value is 100.

Usage Scenario:

APP Sets sub-device color temperature

#### UIID1770 Zigbee Temperature and Humidity Sensor

```json
{
  "temperature": "2558",
  "humidity": "5211",
  "battery": 100,
  "trigTime": "1576348190529"
}
```

Parameter Description:

- temperature: Temperature, Unit: Degrees Celsius. Value = actual temperature value x 100
- humidity: Humidity percentage, value = actual humidity value x 100
- battery: Battery level percentage, [0,100]
- trigTime: Trigger time, 13-bit timestamp of the last reported status, accurate to Millisecond

Usage Scenario:

Device updates its status

#### UIID2026 Zigbee Motion Sensor

Report a mobile event:

```json
{
  "motion": 1,
  "battery": 50,
  "trigTime": "1234567890123"
}
```

Parameter Description:

- motion: Mobile Events, Number Type. Value Range: [0,1], 0 no one, 1 someone
- battery: Battery level percentage, Number Type. Value Range[0,100]
- trigTime: Trigger time, String Type. Takes the value of the 13-bit timestamp of the last reported status, accurate to the millisecond

Usage Scenario:

When the device creates a mobile event, it pushes the relevant update command to the cloud. app receives the command and displays a list of events.

#### UIID2256 Zigbee Dual-Channel Switch

```json
{
  "switches": [
    { "switch": "off", "outlet": 0 },
    { "switch": "off", "outlet": 1 }
  ]
}
```

Parameter Description:

- switches: Channel list, when only one channel changes, only one channel value will be reported
- switch: Channel status, String type. takes the value on/off, indicate channel on/off, the default is on when the addition is complete.
- outlet: Channel No., 0 Channel 1, 1 Channel 2

Usage Scenario:

- Device updates its status
- Set device state via the app

Set Timer:

```json
{
  "timers": [
    {
      //delay
      "mId": "6bdfc96c-0962-ad75-c430-15d9eb351154",
      "type": "once",
      "at": "2020-12-16T18:37:00.761Z",
      "coolkit_timer_type": "delay",
      "enabled": 1,
      "do": {
        "switch": "on",
        "outlet": 0
      },
      "period": "390"
    },
    {
      //Single Timer
      "mId": "c5601da9-aa5f-0946-a1fd-2a2a35daf59a",
      "type": "once",
      "at": "2020-12-16T13:11:00.974Z",
      "coolkit_timer_type": "once",
      "enabled": 1,
      "do": {
        "switch": "on",
        "outlet": 1
      }
    },
    {
      //Repeat timer
      "mId": "870262af-4f9c-7d23-318b-f65d5a79d3eb",
      "type": "repeat",
      "at": "6 15 * * 0,1,2,3,4,5,6",
      "coolkit_timer_type": "repeat",
      "enabled": 1,
      "do": {
        "switch": "on",
        "outlet": 1
      }
    }
  ]
}
```

#### UIID3026 Zigbee Door and Window Sensor

Report switch events:

```json
{
  "battery": 50,
  "lock": 1,
  "trigTime": "1234567890123"
}
```

Parameter Description

- lock: Indicate the opening and closing status of the window, Number Type. Value Range: [0,1], 0 Close the door, 1 Open the door
- battery: Battery power percentage,Number Type. Value Range[0,100]
- trigTime: Trigger time, String Type. Take value: 13-bit timestamp of the last reported status, accurate to Millisecond

Usage Scenario:

When the device is turned on or off, the relevant update command is pushed to the cloud. The app displays a list of events when it receives a command.

#### UIID3256 Zigbee Three-Channel Switch

```json
{
  "switches": [
    { "switch": "off", "outlet": 0 },
    { "switch": "off", "outlet": 1 },
    { "switch": "off", "outlet": 2 }
  ]
}
```

Parameter Description:

- switches: Channel list, When there is only one channel change, only one channel value will be reported
- switch: Channel status, String type. Take value on/off, Indicates channel on/off, the default is on when added.
- outlet: Channel No., 0 Channel 1, 1 Channel 2, 2 Channel 3

Usage Scenario:

- Device updates its status
- Set device state via the app

Set Timer:

Similar to UIID2256 with one additional channel control parameter.

#### UIID3258 Zigbee RGBCW LED Light

Turn on/off light

```json
{
  "switch": "on" // turn on (on), turn off (off)
}
```

Parameter Description:

switch: Channel status, String type. Take value on/off, indicates channel on/off, the default is on when added.

Usage Scenario:

- Set sub device channel device state via the app
- Report when a change is created in the local status of the sub-device
- Synchronize sub-device channel status to APP when the device is online

Set brightness:

```json
{
  "switch": "on",
  "cctBrightness": 100,
  "rgbBrightness": 100
}
```

Parameter Description:

- switch: Channel status,mandatory, String type, The value must be on
- cctBrightness: The percentage of brightness in white light mode; Required when switching to white light mode, Must not be selected when switching to white color mode; Number type, Value Range[1 - 100]; Sub-device addition complete, default value 100
- rgbBrightness: The percentage of brightness in the color mode; Required when switching to color light mode, Must not be selected when switching to white light mode; Number type, Value Range[1 - 100]; Sub-device addition complete, default value 100

Usage Scenario: APP sets sub-device brightness

Set color temperature:

```json
{
  "switch": "on",
  "colorTemp": 100
}
```

Parameter Description:

- switch: Channel status, mandatory, String type, The value must be on
- colorTemp: color temperature, mandatory, Number type, Value Range[0 - 100]; The sub device is added, the color temperature is cold by default, the default value is 100

Usage Scenario: In white light mode, the APP sets the color temperature of the sub-device

Set the hue or saturation:

```json
{
  "switch": "on",
  "hue": 0,
  "saturation": 100
}
```

Parameter Description:

- switch: Channel status,mandatory, String type, The value must be on
- hue: Hue, mandatory, Number type, Value Range[0 - 359]; Sub-device added, hue default red, default value: 0
- saturation: Saturation, mandatory, Number type, Value Range[0 - 100]; Default value: 100

Usage Scenario:

- App sets sub-device hue in color light mode
- App setsg sub-device saturation in color light mode

Switch Modes:

```json
// Switch to white light mode:

{
    "colorMode": "cct",
    "switch": "on",
    "cctBrightness": 100,
    "colorTemp": 100
}

// Switch to color light mode:

{
    "colorMode": "rgb",
    "switch": "on",
    "rgbBrightness": 100,
    "hue": 0,
    "saturation": 100
}

```

Parameter Description:

- switch: Channel status,mandatory, String Type,The value must be on
- colorMode: Target color mode, mandatory, String Type, take value cct/rgb, cct White light mode, rgb Color Light Mode
- hue: Hue,Required when switching to color light mode, Must not be selected when switching to white light mode; Number Type, Value Range[0 - 359]; Sub-device added, hue default red, default value: 0
- saturation: Saturation, Required when switching to color light mode, Must not be selected when switching to white light mode; Number Type,Value Range[0 - 100]; Default value: 100;
- colorTemp: color temperature, Required when switching to white light mode, Must not be selected when switching to color light mode;Number Type,Value Range[0 - 100]; The sub device is added, the color temperature is cold by default, the default value is 100
- cctBrightness: The percentage of brightness in white light mode; Required when switching to white light mode, Must not be selected when switching to color light mode; Number Type,Value Range[1 - 100]; Sub-device addition complete, default value 100
- rgbBrightness: The percentage of brightness in the color mode; Required when switching to color light mode, Must not be selected when switching to white light mode; Number Type,Value Range[1 - 100]; Sub-device addition complete, default value 100

Usage Scenario: APP switch color mode

Description: If the sub-device is a newly added, if you need to switch to the target mode, you should issue a long connection command according to the default value of the target mode
The target mode has already been dimmed, when the mobile app switches to the target mode, it should send a long connection command based on the latest dimming record on the server

#### UIID 4026 Zigbee Water Flood Sensor

Report flooding events:

```json
{
  "water": 1,
  "battery": 50,
  "trigTime": "1234567890123"
}
```

Parameter Description:

- water: Indicates whether a flooding event has occurred, Number Type. Value Range: [0,1], 0 no water, 1 water
- battery:Battery power percentage, Number Type. Value Range[0,100]
- trigTime:Trigger time, String Type. Takes the value of the 13-bit timestamp of the last reported status, accurate to the millisecond

Usage Scenario: Push relevant update commands to the cloud after a device flooding event. The APP displays a list of events after receiving a command.

#### UIID4256 Zigbee Four-Channel Switch

Turn on/off

```json
{
  "switches": [
    { "switch": "on", "outlet": 0 },
    { "switch": "on", "outlet": 1 },
    { "switch": "off", "outlet": 2 },
    { "switch": "off", "outlet": 3 }
  ]
}
```

Parameter Description:

- switches:Channel list, When there is only one channel change, only one channel value will be reported
- switch: Channel status, String type, take value on/off, Indicates channel on/off, When added, the default is on
- outlet: Channel No., 0 Channel 1, 1 Channel 2, 2 Channel 3, 3 Channel 4

Usage Scenario:

- Device updates its status
- Set device state via the app

Set Timer:

Similar to the UIID2256 with two additional channel control parameters.

#### UIID5026 Zigbee Smoke Sensor

Report electricity information:

```json
{
  "battery": 50
}
```

Parameter Description:

battery: Sensor electricity information, Number type, Value Range[0,100]

Usage Scenario: Report when device electricity changes

Report smoke alarm status:

```json
{
  "trigTime": "1597648671620",
  "smoke": 0
}
```

Parameter Description:

- smoke: Smoke alarm events, mandatory, Number type. Value Range: [0,1], 0 no smoke, 1 smoke
- trigTime:Trigger time, mandatory, String type. Takes the value of the 13-bit timestamp of the last reported status, accurate to the millisecond

Usage Scenario: Report status changes when sub-device detects a change in status

#### UIID7002 Zigbee Human Body Sensor_Support OTA

The protocol and functions are basically the same as UIID2026, but with the addition of OTA support.

#### UIID7003 Zigbee Door Sensor_Support OTA

The protocol and functions are basically the same as UIID3026, but with the addition of OTA support.

#### UIID7004 Zigbee Single-Channel Switch ­_Support OTA

The protocol and functions are basically the same as UIID1009, but with the addition of OTA support.

### UIID77 Single-Channel Plug-Multi-Channel Version

#### Parameter Description:

| Parameter Name | Data Type      | Value Range | Parameter Description                                                                         |
| -------------- | -------------- | ----------- | --------------------------------------------------------------------------------------------- |
| switches       | Array\<Object> |             | Switch status of all channels, Single-channel Plugs can only be used with channel 1         |
| pulses         | Array\<Object> |             | Inching status for all channels, Single-channel Plugs can only be used with channel 1       |
| configure      | Array\<Object> |             | Power-up hold status for all channels, Single-channel Plugs can only be used with channel 1 |
| timers         | Array\<Object> |             | Timer object, the execution action will be different for each device Type                     |

switches Parameter Description:

| Name   | Type   | Allows Empty | Description                                                             |
| :----- | :----- | :----------- | :---------------------------------------------------------------------- |
| switch | String | on,off       | Switches of channels,turn on (on), turn off (off)                       |
| outlet | Number | [0,3]        | Value Range 0-3,Indicates channels 1-4 respectively, cannot be repeated |

configure Parameter Description:

| Name    | Type   | Allows Empty | Description                                                                                    |
| :------ | :----- | :----------- | :--------------------------------------------------------------------------------------------- |
| startup | String | on,stay,off  | Power-up hold status for specific channels,power on(on), power on hold (stay), power off (off) |
| outlet  | Number | [0,3]        | Value Range 0-3,Indicates channels 1-4 respectively, cannot be repeated                        |

pulses Parameter Description:

| Name       | Type   | Allows Empty                                                      | Description                                                                                                                                                                 |
| :--------- | :----- | :---------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pulse      | String | on,off                                                            | Inching switch,turn on (on), turn off (off)                                                                                                                                 |
| pulseWidth | Number | [500,3600000] (Unit:Millisecond,Supports setting integers of 500) | Inching Duration: Value Range 500-3600000 (Unit: milliseconds: 0.5s-3600s). Only supports setting an integer multiple of 500 milliseconds (i.e., 0.5 seconds).   |
| outlet     | Number | [0,3]                                                             | Value Range 0-3, indicates channels 1-4 respectively, cannot be repeated                                                                                                    |

#### Control Command:

1. Turn on Plug

```json
{
  "switches": [
    {
      "switch": "on",
      "outlet": 0
    },
    {
      "switch": "off",
      "outlet": 1
    },
    {
      "switch": "off",
      "outlet": 2
    },
    {
      "switch": "off",
      "outlet": 3
    }
  ]
}
```

2. Turn off Plug

```json
{
  "switches": [
    {
      "switch": "off",
      "outlet": 0
    },
    {
      "switch": "off",
      "outlet": 1
    },
    {
      "switch": "off",
      "outlet": 2
    },
    {
      "switch": "off",
      "outlet": 3
    }
  ]
}
```

Other functions including the timer remain the same as UIID2. It should be noted that this UIID77 single-channel Plug can only use the parameters of channel 1, other channel settings are not valid.

### UIID78 Single-Channel Switch-Multi-channel version

Consistent with UIID4, the parameters of switch are on channel 0.

### UIID82 GSM/4G Dual-Channel Plug-No traffic version

Consistent with UIID2

### UIID83 GSM/4G Three-Channel Plug-No traffic version

Consistent with UIID3

### UIID84 GSM/4G Four-Channel Plug-No traffic version

Consistent with UIID4

### UIID102 WiFi Door Sensor

This device does not support timers.

Function Description:

| Serial No. | Function             | Function (Description)                                                        | APP Support | Applet Support |
| ---------- | -------------------- | ----------------------------------------------------------------------------- | ----------- | -------------- |
| 1          | Power Display        | Displays the status of the Door Sensor power, sufficient power or low power | √           | √              |
| 2          | Door Sensor Status | Display Door Sensor status, open or closed                                  | √           | √              |
| 3          | OTA Upgrade          | Upgradeable when new firmware is available on the device side                 | √           | √              |

#### Parameter Description:

| Name                                             | Type   | Allows Empty | Description                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------ | ------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| switch                                           | String | N            | Switch Status: "on" means turn on,"off" means turn off                                                                                                                                                                                                                                                                                                             |
| battery                                          | String | N            | Current voltage value, ranging from 0-3V, with lowVolAlarm to determine whether the device is in low battery mode. Note: lowVolAlarm is the parameter in the devConfig object, When battery<lowVolAlarm, low battery , When battery>=lowVolAlarm, it shows full battery |
| type                                             | Number | N            | Type of Push, the server side determines whether to push notifications to the App based on this type, 1: Short press to trigger and push after exiting the hibernation state; 2: Push message after opening the door; 3: Push message after closing the door; 4: Push messages at regular intervals, e.g. every hour; 5: Short press twice (double click) to close |
| lastUpdateTime                                   | String | Y            | The last time reported by the device, the App side determines whether the device is offline based on the difference between the time recorded in this field and the current time, which is not reported by the device and is added by the server side.                                                                                                             |
| actionTime                                       | String | Y            | Time when the device last opened or closed the door, this field is not reported by the device and is added by the server.                                                                                                                                                                                                                                          |

On-line logic:

Note: APP check device on/offline status (The current time is greater than or equal to 2 hours and 5 minutes from the last Update Time (lastUpdateTime)or action Time (actionTime), otherwise it means online)

After the device sends a request to the server through the HTTP interface, the server adds the lastUpdateTime and actionTime parameters to the params field of the device.

### UIID103 Dual-Color Cold and Warm Light_Support with tuning and scenes

#### Parameter Description:

| Parameter Name | Data Type      | Value Range                           | Parameter Description                                                                                                                                                                 |
| -------------- | -------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pVer           | String         |                                       | Current protocol version number, capability negotiation. Consistent with the last version of the current protocol, e.g. {"pVer":"2.0"}. Once the device is online, you need to upload |
| white          | WhiteObject    |                                       | Value in white light mode                                                                                                                                                             |
| bright         | WhiteObject    |                                       |                                                                                                                                                                                       |
| read           | WhiteObject    |                                       |                                                                                                                                                                                       |
| computer       | WhiteObject    |                                       |                                                                                                                                                                                       |
| nightLight     | WhiteObject    |                                       |                                                                                                                                                                                       |
| timers         | Array\<Object> |                                       | Timer, the current dual-color cold and warm light's timer and delay action only supports on and off                                                                                   |
| ops_mode       | String         | DIY, ewelink                          | This field is common in long connection and DIY mode; DIY enters DIY mode; eweLink returns to eweLink mode                                                                            |
| switch         | String         | on,off                                | Light Switch: turn on (on), turn off (off)                                                                                                                                            |
| ltype          | Int            | white,bright,read,computer,nightLight | Light Mode|

WhiteObject Parameter Description:

| Parameter Name | Data Type | Value Range | Description                           |
| -------------- | --------- | ----------- | ------------------------------------- |
| br             | Number    | [1,100]     | Brightness (brighteness)              |
| ct             | Number    | [0,255]     | Color Temperature (color temperature) |

#### Control Command:

1. Turn on/off light

Example: APP send to turn on the light: on (turn on),off (turn off)

```json
{
  "switch": "on"
}
```

2. White light mode

Switching to white light mode or other light mode must be accompanied by a "switch": "on"

Example: in white light mode, the brightness value is adjusted to 50

When adjusting the brightness or color temperature, the two values should be sent down together.

```json
{
  "ltype": "white",
  "white": {
    "br": 50,
    "ct": 125
  }
}
```

When adjusting the brightness or color temperature, the two values should be sent down together.

3. Scene Mode Settings

Four fixed scene models: The app will display four fixed modes for the user to choose, and when the user clicks on a mode, it will be sent down to the device according to the fixed brightness value and color temperature value.

- bright：brightness value 100, color temperature value 255
- read：brightness value 50, color temperature value 0
- computer：brightness value 20, color temperature value 255
- nightLight：brightness value 5, color temperature value 0

For example, when the user selects "Reading Mode"

```json
{
  "ltype": "read",
  "read": {
    "br": 50,
    "ct": 0
  }
}
```

4. Single Timer

Set the light to turn on at 17:08 on May 29, 2020, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      "coolkit_timer_type": "once",
      "at": "2020-05-29T09:08:00.315Z",
      "type": "once",
      "do": {
        "switch": "on"
      },
      "mId": "91959d3b-5885-718d-13c5-e69cd48de862"
    }
  ]
}
```

5. Single Delay

Set the light to turn off at 17:10 on May 29, 2020 with a delay of 6 minutes at 17:16, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      "coolkit_timer_type": "delay",
      "at": "2020-05-29T09:16:00.101Z",
      "period": "6",
      "type": "once",
      "do": {
        "switch": "off"
      },
      "mId": "e4777ab0-a74e-ed60-aeac-1ea23b112069"
    }
  ]
}
```

### UIID104 RGBCW LED Light_Support with tuning and scenes

#### Parameter Description:

| Parameter Name | Data Type      | Value Range                                                              | Parameter Description                                                                                                                                                                      |
| -------------- | -------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| switch         | String         | on,off                                                                   | Light switch, turn on (on), turn off (off)                                                                                                                                                 |
| pVer           | String         |                                                                          | Current protocol version number, capability negotiation. Consistent with the last version of the current protocol, e.g. {"pVer":"2.0"}.Once the device is online, it needs to be uploaded. |
| ltype          | String         | white,color,bright,goodNight,read,nightLight,party,leisure,soft,colorful | Light Mode|
| white          | WhiteObject    |                                                                          | Value in white light mode                                                                                                                                                                  |
| color          | ColorObject    |                                                                          | Value in color light mode                                                                                                                                                                  |
| bright         | ModeObject     |                                                                          | Scene cannot be edited                                                                                                                                                                     |
| goodNight      | ModeObject     |                                                                          | Scene cannot be edited                                                                                                                                                                     |
| read           | ModeObject     |                                                                          | Scene cannot be edited                                                                                                                                                                     |
| nightLight     | ModeObject     |                                                                          | Scene cannot be edited                                                                                                                                                                     |
| party          | ModeObject     |                                                                          | Scene can be edited                                                                                                                                                                        |
| leisure        | ModeObject     |                                                                          | Scene can be edited                                                                                                                                                                        |
| soft           | ModeObject     |                                                                          | Scene can be edited                                                                                                                                                                        |
| colorful       | ModeObject     |                                                                          | Scene can be edited                                                                                                                                                                        |
| ops_mode       | String         | DIY, ewelink                                                             | This field is common in long connection and DIY mode; DIY enters DIY mode; eweLink returns to eweLink mode                                                                                 |
| timers         | Array\<Object> |                                                                          | Timer, the current RGBCW LED Light's timer and delay action only supports on and off                                                                                                  |

WhiteObject Parameter Description:

| Parameter Name | Data Type | Value Range | Description       |
| -------------- | --------- | ----------- | ----------------- |
| br             | Number    | [1,100]     | Brightness        |
| ct             | Number    | [0,255]     | Color temperature |

ColorObject Parameter Description:

| Parameter Name | Data Type | Value Range | Description |
| -------------- | --------- | ----------- | ----------- |
| br             | Number    | [1,100]     | Brightness  |
| r              | Number    | [0,255]     | Red value   |
| g              | Number    | [0,255]     | Green value |
| b              | Number    | [0,255]     | Blue value  |

ModeObject Description (Note that not every model has these fields):

| Parameter Name | Data Type | Value Range | Description                                                |
| -------------- | --------- | ----------- | ---------------------------------------------------------- |
| br             | Number    | [1,100]     | Brightness                                                 |
| ct             | Number    | [0,255]     | Color temperature                                          |
| r              | Number    | [0,255]     | Red value                                                  |
| g              | Number    | [0,255]     | Green value                                                |
| b              | Number    | [0,255]     | Blue value                                                 |
| name           | String    |             | Customized scene name                                      |
| tf             | Number    | [1,4]       | Color Mode: 1 Static; 2 Gradule; 3 Jump Changes; 4 Breathe |
| sp             | Number    | [1,100]     | Speed of color change                                      |

#### Control Command:

1. Turn on/off light

Example: APP send to turn on the light: on (turn on),off (turn off)

```json
{
  "switch": "on"
}
```

2. White Light Mode

Switching to white light mode or color light mode must be accompanied by a "switch":"on"

Example: in white light mode, the brightness value is adjusted to 50

When adjusting the brightness or color temperature, the two values should be sent down together.

```json
{
  "ltype": "white",
  "white": {
    "br": 50,
    "ct": 128
  }
}
```

When adjusting the brightness or color temperature, the two values should be sent down together.

3. Color Light Mode

Example: adjust color to red, brightness 50%

```json
{
  "ltype": "color",
  "color": {
    "r": 255,
    "g": 0,
    "b": 0,
    "br": 1
  }
}
```

4. Scene Mode Setting

Fixed 8 scene modes: The app will display 8 fixed modes for the user to choose, and when the user clicks on a mode, it will be sent to the device according to the fixed brightness value and color temperature value.

```json
//Bright
{
    "ltype":"bright",
    "bright":{
        "r":255,
        "g:":255,
        "b":255,
        "br":100
    }
}
//Good Night
{
    "ltype": "goodNight",
    "goodNight": {
        "r": 255,
        "g:": 254,
        "b": 127,
        "br": 25
    }
}
//Reading
{
    "ltype":"read",
    "read":{
        "r":255,
        "g:":255,
        "b":255,
        "br":60
    }
}
//Night Light
{
    "ltype":"nightLight",
    "nightLight":{
        "r":255,
        "g:":242,
        "b":226,
        "br":5
    }
}
//Party
{
    "ltype":"party",
    "party":{
        "r":254,
        "g:":132,
        "b":0,
        "br":45,
        "tf":1,
        "sp":1
    }
}
//Leisure
{
    "ltype":"leisure",
    "leisure":{
        "r":0,
        "g:":40,
        "b":254,
        "br":55,
        "tf":1,
        "sp":1
    }
}
//Soft
{
    "ltype":"soft",
    "soft":{
        "r":38,
        "g:":254,
        "b":0,
        "br":20,
        "tf":1,
        "sp":1
    }
}
//Colorful
{
    "ltype":"colorful",
    "colorful":{
        "r":255,
        "g:":0,
        "b":0,
        "br":100,
        "tf":1,
        "sp":1
    }
}
```

5. Single Timer

Example: Set the light to turn on at 17:08 on May 29, 2020, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      "coolkit_timer_type": "once",
      "at": "2020-05-29T09:08:00.315Z",
      "type": "once",
      "do": {
        "switch": "on"
      },
      "mId": "91959d3b-5885-718d-13c5-e69cd48de862"
    }
  ]
}
```

6. Single Delay

Example: Set the light to turn off at 17:10 on May 29, 2020 with a delay of 6 minutes at 17:16, without repeating in a single execution

```json
{
  "timers": [
    {
      "enabled": 1,
      "coolkit_timer_type": "delay",
      "at": "2020-05-29T09:16:00.101Z",
      "period": "6",
      "type": "once",
      "do": {
        "switch": "off"
      },
      "mId": "e4777ab0-a74e-ed60-aeac-1ea23b112069"
    }
  ]
}
```

### UIID107 GSM Single-Channel Plug Multi-channel protocols

Consistent with UIID77.







