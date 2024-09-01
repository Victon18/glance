1.Include necessary libraries:
These libraries provide the necessary functions to connect to WiFi, send and receive HTTP requests, and read data from the DHT11 sensor.
```
#include <ESP8266WiFi.h>
#include <ESP8266HTTPClient.h>
#include <DHT.h>
#include <WiFiClient.h>
```
2. Define constants and variables:
These constants and variables define the WiFi credentials,
ThingWorx server address and port, app key, DHT11 sensor pin and type, and the names of the things and properties used in the ThingWorx server.
```
#define ACCEPT_TYPE "text/csv"
WiFiClient client;

#define DHT_PIN 5
#define DHT_TYPE DHT11



DHT DHT11_INTERFACE(DHT_PIN, DHT_TYPE);
float temp  = 0;
float hum = 0 ;



const char* ssid = "Pawan";
const char* password = "12345678";



const char* host = "192.168.4.246";
const int Port = 7081;
const char appKey[]= "e682ae39-4d76-473b-b012-57f5c90e53ed";



const char Thing[] = "D_Pro_Things";
const char Property1[] = "Humidity";
const char Property2[] = "temp";
const char Property3[] = "Switch";
```
3. Set up the ESP8266 board:
```
void setup()
{
```
4. Initializes the DHT11 sensor by calling the begin() function of the DHT object.
```
DHT11_INTERFACE.begin();
```

5. Sets the LED pin as an output pin using the pinMode() function.
```
  pinMode(LED_BUILTIN,OUTPUT);
```
6. Starts the serial communication with the computer by calling the begin() function of the Serial object.
```
  Serial.begin(115200);
```
7.Prints the IP address of the ESP8266 board using the localIP() function of the WiFi object.
```
  Serial.println();
  Serial.print("connecting to ");
  Serial.println(ssid);
```
8. Connects to the WiFi network by calling the begin() function of the WiFi object with the ssid and password parameters.
````
WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED)
{
    delay(500);
    Serial.print(".");
}
````
9. Prints the IP address of the ESP8266 board using the localIP() function of the WiFi object.
```
  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());



}
```
10. Reads the temperature and humidity data from the DHT11 sensor using the readTemperature() and readHumidity() functions of the DHT object.
````
void loop()
{
  temp = DHT11_INTERFACE.readTemperature();
  hum = DHT11_INTERFACE.readHumidity();
````
11. Prints the temperature and humidity data to the serial monitor using the print() and println() functions of the Serial object.
12. Sends the temperature and humidity data to the ThingWorx server using the Put() function.
13. Receives the switch state data from the ThingWorx server using the Get() function.
14. Controls the LED based on the switch state data received from the ThingWorx server.
15. aits for 5 seconds before starting the next iteration using the delay() function.
````

  Serial.print("Temp: ");
  Serial.print(temp);
  Serial.print("\t");
  Serial.print("Hum: ");
  Serial.println(hum);



  if(temp != NULL && hum != NULL)
  {
    Put(Thing,Property1,hum);
    Put(Thing,Property2,temp);
  }



  String res = Get(Thing,Property3);
  Serial.print(res); //fan_control,0
  Serial.println(res[11]);



  if (res[11] == 't')
  {
    digitalWrite(LED_BUILTIN,LOW);
  }
  else if (res[11] == 'f')
  {
    digitalWrite(LED_BUILTIN,HIGH);
  }
  delay(5000);
}



void Put(String ThingName, String ThingProperty, float Value)
  {



    Serial.println(host);
  if (!client.connect(host, Port))
{
    Serial.println("connection failed");
    return;
  } else



{
    Serial.println("Connected to ThingWorx.");
  }
  String url = "/Thingworx/Things/" + ThingName + "/Properties/" + ThingProperty;
  Serial.print("requesting URL: ");
  Serial.println(url);



  String strPUTReqVal = "{\"" + ThingProperty + "\":\"" + Value + "\"}";
  Serial.print("PUT Value: ");
  Serial.println(strPUTReqVal);



  client.print(String("PUT ") + url + " HTTP/1.1\r\n" +
               "Host: " + host + "\r\n" +
               "appKey:"+ appKey + "\r\n" +
               "x-thingworx-session: false" + "\r\n" +
               "Accept: application/json" + "\r\n" +
               "Connection: close" + "\r\n" +
               "Content-Type: application/json" + "\r\n" +
               "Content-Length: " + String(strPUTReqVal.length()) + "\r\n\r\n" +
               strPUTReqVal + "\r\n\r\n");



  while (client.connected())
{
    String line = client.readStringUntil('\r');
    Serial.print(line);
  }
  client.stop();
}



String Get(String get_Thing, String get_Property)
{
        HTTPClient http;
        int httpCode = -1;
        String fullRequestURL = "http://" + String(host) +":"+ String(Port)+ "/Thingworx/Things/"
                                + get_Thing + "/Properties/" + get_Property + "?appKey=" + appKey;

        Serial.println(fullRequestURL);
        http.begin(client, fullRequestURL);
        http.addHeader("Accept",ACCEPT_TYPE,false,false);
        httpCode = http.GET();
        Serial.println(httpCode);

        String responses;
        if(httpCode > 0)
        {
           responses= http.getString();
             //Serial.println(responses);
             //Serial.print(responses[9]);
        }
        else
        {
            Serial.printf("[httpGetPropertry] failed, error: %s\n\n", http.errorToString(httpCode).c_str());
        }
        http.end();
        return responses;
}
```
