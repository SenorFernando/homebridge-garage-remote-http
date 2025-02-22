# homebridge-garage-remote-http

[![npm](https://img.shields.io/npm/v/homebridge-garage-remote-http.svg)](https://www.npmjs.com/package/homebridge-garage-remote-http) [![npm](https://img.shields.io/npm/dt/homebridge-garage-remote-http.svg)](https://www.npmjs.com/package/homebridge-garage-remote-http)

This work is forked from https://github.com/jmaferreira/homebridge-garage-remote-http.

Fixed a bug, where calling "close the garagedoor" on already closed door actually opens them

## Description

This [homebridge](https://github.com/nfarina/homebridge) plugin exposes a web-based garage opener to Apple's [HomeKit](http://www.apple.com/ios/home/). Using simple HTTP requests, the plugin allows you to open/close the garage.

## Installation

1. Install [homebridge](https://github.com/nfarina/homebridge#installation-details)
2. Install this plugin: `npm install -g homebridge-garage-remote-http`
3. Update your `config.json`

## Configuration

```json
"accessories": [
     {
       "accessory": "GarageDoorOpener",
       "name": "Garage",
       "openURL": "http://myurl.com/open",
       "closeURL": "http://myurl.com/close",
       "openTime": "30",
       "closeTime": "30",
       "autoLock": "true",
       "autoLockDelay": "30",
       "switchOff": "true",
       "switchOffDelay": "5"
     }
]
```

### Core
| Key | Description | Default |
| --- | --- | --- |
| `accessory` | Must be `GarageDoorOpener` | N/A |
| `name` | Name to appear in the Home app | N/A |
| `openURL` | URL to trigger the opening of your garage | N/A |
| `closeURL` | URL to trigger the closing of your garage | N/A |

### Optional fields
| Key | Description | Default |
| --- | --- | --- |
| `openTime` | Time (in seconds) to simulate your garage opening | `10` |
| `closeTime` | Time (in seconds) to simulate your garage closing | `10` |
| `autoLock` | Whether your garage should auto-close after being opened | `false` |
| `autoLockDelay` | Time (in seconds) until your garage will automatically close (if enabled) | `20` |
| `switchOff` | Closes the garage immediately without animation. For IR remote control use. | `false` |
| `switchOffDelay` | Time (in seconds) until your garage will automatically close without animation (if enabled) | `2` |
| `polling` | Whether the state should be polled at intervals | `false` |
| `pollInterval` | Time (in seconds) between device polls (if `polling` is enabled) | `120` |
| `statusURL` | URL to retrieve state on poll (should return `0` or `1`) | N/A |

### Additional options
| Key | Description | Default |
| --- | --- | --- |
| `timeout` | Time (in milliseconds) until the accessory will be marked as _Not Responding_ if it is unreachable | `3000` |
| `http_method` | HTTP method used to communicate with the device | `GET` |
| `username` | Username if HTTP authentication is enabled | N/A |
| `password` | Password if HTTP authentication is enabled | N/A |
| `model` | Appears under the _Model_ field for the accessory | plugin |
| `serial` | Appears under the _Serial_ field for the accessory | version |
| `manufacturer` | Appears under the _Manufacturer_ field for the accessory | author |
| `firmware` | Appears under the _Firmware_ field for the accessory | version |

## State key
| State | Description |
| --- | --- |
| `0` | Open |
| `1` | Closed |
