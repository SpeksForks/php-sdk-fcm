# PHP Firebase Cloud Messaging Helper
Quickly and easily send a push notification using Firebase to a client using cordova-plugin-fcm on a mobile device from your PHP backend.

## Methods
Set the title, message, and recipient as shown below

|Property    |Method      | Parameter | Note                      |
|------------|------------|-----------|---------------------------|
| `+` title     | withTitle  |  string   |                           |
| `+` message   | withMessage|  string   |                           |
| `~` recipient |  to        |  string   | user device token         |
| `~` recipient |  topic     |  string   | messge topic (user group) |
|  data      |  withData* |  array    | Data to attach to message |
`+` Required  
`~` Only one needed  
`*` All other method calls starting with 'with' will be added to the data i.e. `withFoo('bar')` sets `data['foo'] = 'bar'`


## Setup
1. Copy `src/config.ini.sample` to `src/config.ini`
2. Set your API Key.  
Found under the `Cloud messaging` tab in your Firebase dashboard settings.

## Usage
1. Set the data field implicitly

```php
$push = new PushNotification();
$push->to('adsfasdf:adsfadsfadf')
     ->withTitle('hello')
     ->withMessage('there')
     ->withLink('/msgevents')
     ->send();
```

2. Set the data field explicitly

```php
$push->to('adsfasdf:adsfadsfadf')
     ->withTitle('hello')
     ->withMessage('there')
     ->withData(['link' => '/msgevents'])
     ->send();
```

3. Without data

```php
$push->to('adsfasdf:adsfadsfadf')
     ->withTitle('hello')
     ->withMessage('there')
     ->send();
```