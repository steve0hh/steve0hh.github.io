---
layout: post
comments: true
---

Hi guys,

Sorry for the haitus, school work was pretty crazy for me.

Today's post, I am gonna tell you guys hows to send push notifications from your ESP8266 to your iPhone or Android using [Pushbullet](https://www.pushbullet.com/).

At this point of writing, Sunday, 4 December 2016, pushbullet allows free 500 push notifications for free users, which is more then enough for normal home automation use cases.

As stated on the api docs of pushbullet, we need to use https instead of http, luckily, the folks at [ESP8266 github](https://github.com/esp8266/Arduino) have implemented client requests using ssl. :D

# Prerequisites

- [pushbullet](https://www.pushbullet.com/) installed on the devices that you would like to have push notifications on.
- An [ESP8266](https://en.wikipedia.org/wiki/ESP8266) which can be bought on [Aliexpress](http://aliexpress.com) at a very cheap price.
- Configure your arduino IDE to be able to work with the ESP8266, [instructables link here](http://www.instructables.com/id/noobs-guide-to-ESP8266-with-Arduino-Mega-2560-or-U/).

# Variables that need to be declared

```arduino
#include <ESP8266WiFi.h>
#include <WiFiClientSecure.h>

const char* ssid     = "your SSID";
const char* password = "YOUR SSID password";

const char* host = "api.pushbullet.com";
const int httpsPort = 443;

const char* accessToken = "YOUR OWN ACCESS TOKEN HERE";
const char* fingerprint = "I'LL TELL YOU HOW TO FIND THE SHA1 FINGERPRINT LATER IN THIS POST";
```


In this post, I won't be going though how to connect the client to wifi etc, as I think the examples provided with the arduino IDEs are sufficient.

# How to find the SHA1 fingerprint of a https website?

These steps are only tested with OSX, however, for windows and linux, the steps should be similar.

Step 1. Using chrome, go to the website, in our case, it's `https://api.pushbullet.com/`

Step 2. Right click > Inspect > View certificate.

A pop up like the following should appear.

![Pop up on chrome](https://cloud.githubusercontent.com/assets/682923/20860772/31b082f2-b9bb-11e6-801d-9c0d96b809bd.png)


Step 3. Click "Details" in the pop up.

![Click details](https://cloud.githubusercontent.com/assets/682923/20860774/608880ac-b9bb-11e6-9f43-6c3bb2f4046c.png)


Step 4. Scroll all the way down and you'll see a item field called "SHA1" under the fingerprint section.

![SHA1 fingerprint](https://cloud.githubusercontent.com/assets/682923/20863544/e5439460-ba08-11e6-85fb-179c787b06c2.png)


## Send the push notifications

Now, the interesting part, crafting the request to be sent to the pushbullet api server. :)

```arduino
  String url = "/v2/pushes";
  Serial.print("requesting URL: "); Serial.println(url);

  client.print(String("POST ") + url + " HTTP/1.1\r\n" +
               "Host: " + host + "\r\n" +
               "User-Agent: ESP8266\r\n" +
               "Access-Token: " + accessToken + "\r\n" +
               "Content-length: 114\r\n"
               "Content-Type: application/json\r\n" +
               "Connection: close\r\n\r\n" +
               "{\"body\":\"Space Elevator, Mars Hyperloop, Space Model S (Model Space?)\",\"title\":\"Space Travel Ideas\",\"type\":\"note\"}"
              );
```

So, as stated in the docs, pushbullet api requests needs to be using POST, together with a access-token which we've defined earlier ahead.

Afterwhich, it's the body as stated in the [api docs](https://docs.pushbullet.com/#create-push).

*Note need the content-length in the header, in which I've manually counted the json body characters, you could use a function to count the bytes to make it more dynamic, I was lazy to do that. (I took 30 mins to figure this out, that's why I've wrote this post)*

So here's the overall code that is used to send the push notificatio to my iPhone.

# Overall code used

Note that those parts marked as TODO, are the things that you'll have to define yourself. :)

```arduino
#include <ESP8266WiFi.h>
#include <WiFiClientSecure.h>

const char* ssid     = "TODO";
const char* password = "TODO

const char* host = "api.pushbullet.com";
//https://api.pushbullet.com/v2/pushes
const int httpsPort = 443;

const char* accessToken = "TODO";
const char* fingerprint = "TODO";

void setup() {
  Serial.begin(115200);
  delay(10);

  // We start by connecting to a WiFi network

  Serial.println();
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);

  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

	Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());

  // Use WiFiClientSecure class to create TLS connection
  WiFiClientSecure client;
  Serial.print("connecting to ");
  Serial.println(host);
  if (!client.connect(host, httpsPort)) {
    Serial.println("connection failed");
    return;
  }

  if (client.verify(fingerprint, host)) {
    Serial.println("certificate matches");
  } else {
    Serial.println("certificate doesn't match");
  }

  String url = "/v2/pushes";
  Serial.print("requesting URL: "); Serial.println(url);

  client.print(String("POST ") + url + " HTTP/1.1\r\n" +
               "Host: " + host + "\r\n" +
               "User-Agent: ESP8266\r\n" +
               "Access-Token: " + accessToken + "\r\n" +
               "Content-length: 114\r\n"
               "Content-Type: application/json\r\n" +
               "Connection: close\r\n\r\n" +
               "{\"body\":\"Space Elevator, Mars Hyperloop, Space Model S (Model Space?)\",\"title\":\"Space Travel Ideas\",\"type\":\"note\"}"
              );


  Serial.println("request sent");
  while (client.connected()) {
    String line = client.readStringUntil('\n');
    if (line == "\r") {
      Serial.println("headers received");
      break;
    }
  }
  String line = client.readStringUntil('\n');
  //  String line = client.readString(); // this line is good for debugging error messages more then a single line
  if (line.startsWith("{\"active\":true")) {
    Serial.println("esp8266/Arduino CI successfull!");
  } else {
    Serial.println("esp8266/Arduino CI has failed");
  }
  Serial.println("reply was:");
  Serial.println("==========");
  Serial.println(line);
  Serial.println("==========");
  Serial.println("closing connection");
}

void loop() {
}
```

Hope this blogpost helped you save sometime. :)
