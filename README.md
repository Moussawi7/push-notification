#  [![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Dependency Status][daviddm-image]][daviddm-url]

> push notification for apple push notification (APN) and google cloud messaging (GCM)


## Install

```sh
$ npm install --save push-notification
```


## Usage

```js
var PushNotification = require('push-notification');
var DeviceType = PushNotification.DeviceType;
var path = require('path');

PushNotification.init({
	apn: {
		gateway: 'gateway.sandbox.push.apple.com',
		cert: path.resolve('./keys/cert.pem'),
		key: path.resolve('./keys/key.pem')
	},
	gcm: {
		sender: ''
	}
});

var iosToken = 'iphone-device-token';
var androidToken = 'android-device-token';
var message = 'some text to push...';
var badge = null;
var sound = null;
var payload = null;

PushNotification.pushSingle(DeviceType.IOS, iosToken, message, badge, sound, payload);
PushNotification.pushSingle(DeviceType.ANDROID, androidToken, message, badge, sound, payload);

PushNotification.prepare(message, badge, sound, payload);
PushNotification.addTarget(DeviceType.IOS, iosToken);
PushNotification.addTarget(DeviceType.ANDROID, androidToken);
PushNotification.addTarget(DeviceType.ANDROID, anotherToken);
PushNotification.push();
```


## License

MIT © [Dongwon Lim]()


[npm-image]: https://badge.fury.io/js/push-notification.svg
[npm-url]: https://npmjs.org/package/push-notification
[travis-image]: https://travis-ci.org/idw111/push-notification.svg?branch=master
[travis-url]: https://travis-ci.org/idw111/push-notification
[daviddm-image]: https://david-dm.org/idw111/push-notification.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/idw111/push-notification