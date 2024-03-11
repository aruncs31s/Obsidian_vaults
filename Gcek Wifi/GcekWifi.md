---
id: GcekWifi
aliases: []
tags: []
---
# Gcek Wifi
- [ ] [Connect to wifi using Curl](#connect%20to%20wifi%20using%20curl)
- [ ] [Connect to wifi using esp32](#2)

---
#### Connect to wifi using Curl

###### Skeleton


```bash
curl -d "username=your_username&password=your_password" -X POST http://wifi_login_page_url

```
source : chatgpt
- -d : specifies post data 



- after modifing
```bash
curl -d "usrname=abc&newpasswd=def&terms=on&page_sid=internal&org_url=http%3A%2F%2F172.16.0.2%3A2280%2F&update_btn=Login"
```

##### post request

#gcekWifipost

```rust
POST /submit/user_login.php HTTP/1.1
Host: 172.16.0.2:2280
Content-Length: 111
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://172.16.0.2:2280
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.216 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://172.16.0.2:2280/cportal/login.html?h=9ff35957&url=http://172.16.0.2:2280/
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Connection: close

usrname=abc&newpasswd=def&terms=on&page_sid=internal&org_url=http%3A%2F%2F172.16.0.2%3A2280%2F&update_btn=Login
```
- usrname: The username
- newpasswd: The password
- terms: Checkbox for terms acceptance
- page_sid: Some sort of session identifier
- org_url: Original URL
- update_btn: Button indicating login action

##### Esp32 code

#esp32ByChatGpt 

```cpp
#include <WiFi.h>
#include <HTTPClient.h>

const char* ssid = "YourWiFiSSID";
const char* password = "YourWiFiPassword";

void setup() {
  Serial.begin(115200);
  
  // Connect to Wi-Fi
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("Connecting to WiFi...");
  }
  Serial.println("Connected to WiFi");

  // Send HTTP POST request to login page
  HTTPClient http;
  http.begin("http://172.16.0.2:2280/submit/user_login.php");
  http.addHeader("Content-Type", "application/x-www-form-urlencoded");
  String postData = "usrname=your_username&newpasswd=your_password&terms=on&page_sid=internal&org_url=http%3A%2F%2F172.16.0.2%3A2280%2F&update_btn=Login";
  int httpResponseCode = http.POST(postData);
  if (httpResponseCode > 0) {
    Serial.print("HTTP response code: ");
    Serial.println(httpResponseCode);
    // Check if login was successful
    if (httpResponseCode == 200) {
      Serial.println("Login successful");
      // You're now connected to the internet
    } else {
      Serial.println("Login failed");
    }
  } else {
    Serial.print("Error in HTTP POST request: ");
    Serial.println(http.errorToString(httpResponseCode).c_str());
  }
  http.end();
}

void loop() {
  // Your main code goes here
}

```
#esp32code
```cpp
#include <WiFi.h>
#include <HTTPClient.h>

const char* ssid = "YourWiFiSSID";
const char* password = "YourWiFiPassword";

void setup() {
  Serial.begin(115200);
  
  // Connect to Wi-Fi
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("Connecting to WiFi...");
  }
  Serial.println("Connected to WiFi");

  // Send HTTP POST request to login page
  HTTPClient http;
  http.begin("http://wifi_login_page_url");
  http.addHeader("Content-Type", "application/x-www-form-urlencoded");
  String postData = "username=your_username&password=your_password";
  int httpResponseCode = http.POST(postData);
  if (httpResponseCode > 0) {
    Serial.print("HTTP response code: ");
    Serial.println(httpResponseCode);
    // Check if login was successful
    if (httpResponseCode == 200) {
      Serial.println("Login successful");
      // You're now connected to the internet
    } else {
      Serial.println("Login failed");
    }
  } else {
    Serial.print("Error in HTTP POST request: ");
    Serial.println(http.errorToString(httpResponseCode).c_str());
  }
  http.end();
}

void loop() {
  // Your main code goes here
}

```
