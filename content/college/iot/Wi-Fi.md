import the library to use it
```
#include <ESP8266WiFi.h>
```
Wifi ssid and password with whom the device will connect to
```
const char* ssid = "Pawan";
const char* password = "12345678";
```
Creates a WiFi server object, which listens for incoming connections on port 80 (the default port for HTTP):
```
WiFiServer server(80);
```
The setup() function is called once at the beginning of the program.
It initializes the serial communication, sets up the WiFi connection, and starts the server.

1. Initializes the serial communication at a baud rate of 9600:
```
void setup() {
 Serial.begin(9600);
```
2. Waits for 10 milliseconds to ensure the serial communication is stable:
```
 delay(10);
```
3. Sets the built-in LED pin as an output and turns it off
```
 pinMode(LED_BUILTIN, OUTPUT);
 digitalWrite(LED_BUILTIN, LOW);
```
4. Prints a message to the serial console indicating that the ESP8266 is trying to connect to the WiFi network:
```
 // Connect to WiFi network
 Serial.println();
 Serial.print("Connecting to ");
 Serial.println(ssid);
```
5. Starts the WiFi connection using the WiFi.begin() function, passing the SSID and password as arguments:
```

 WiFi.begin(ssid, password);
```
6. Waits for the WiFi connection to be established, printing dots to the serial console every 500 milliseconds:
```
 while (WiFi.status() != WL_CONNECTED) {
 delay(500);
 Serial.print(".");
 }
````
7. Prints a success message to the serial console when the WiFi connection is established:
````
 Serial.println("");
 Serial.println("WiFi connected");
````
8. Prints the IP address of the ESP8266 to the serial console:
````
 // Print the IP address
 Serial.println(WiFi.localIP());
````
9. Starts the WiFi server using the server.begin() function:
```
 // Start the server
 server.begin();
````
10 .Prints a success message to the serial console indicating that the server has started:
````
 Serial.println("Server started");
}
````
Loop Function

The loop() function is called repeatedly after the setup() function has completed. It handles incoming client requests and controls the LED accordingly.

1. hecks if there's a new client trying to connect to the server, If there's no client, the function returns immediately.
```
void loop() {
 WiFiClient client = server.available();
```
2. Waits for the client to send a request, printing a message to the serial console when a new client is detected:
```
 if (!client) {
 return;
 }

 Serial.println("new client");
```
3. Waits for the client to send a complete request, using the client.available() function to check if there's data available:
```
 while(!client.available()) {
 delay(1);
 }
```
4. Reads the first line of the request using the client.readStringUntil() function, which reads until it encounters a carriage return (\r):
```
 // Read the first line of the request
 String req = client.readStringUntil('\r');
```
5.This line prints the client's request to the serial monitor.
```
Serial.println(req);
```
6. clears the client's input buffer to prepare for the next request.
```
client.flush();
```
7. declare two variables: val to store the LED state, and m to store the response message.
```
 // Match the request
 int val;
 String m;
```
8. checks if the client's request contains the string "/LED/ON". If it does, it sets the LED to HIGH (turns it on) and sets the response message to "LED is ON".
```
 if (req.indexOf("/LED/ON") != -1){
 m = "LED is ON";
 digitalWrite(LED_BUILTIN, HIGH);
 }
```
9. checks if the client's request contains the string "/LED/OFF". If it does, it sets the LED to LOW (turns it off) and sets the response message to "LED is OFF".
```
 else if (req.indexOf("/LED/OFF") != -1){
 m = "LED is OFF";
 digitalWrite(LED_BUILTIN, LOW);
 }
```
10. If the client's request is invalid, this line prints an error message to the serial monitor and stops the client connection.
```
 else {
 Serial.println("invalid request");
 client.stop();
 return;
 }
 client.flush();
````
11.This line prepares the HTTP response. It sets the HTTP version, content type, and includes the response message (m) in the HTML body.
```

 // Prepare the response
 String s = "HTTP/1.1 200 OK\r\nContent-Type: text/html\r\n\r\n<!DOCTYPE HTML>\r\n<head><meta
http-equiv=\"Access-Control-Allow-Origin\" content=\"*\"></head>\n<html>\r\n" + m;
```
12. This line adds the closing HTML tag to the response.
```
s += "</html>\n";
```
13. This line sends the HTTP response to the client.
```
 // Send the response to the client
 client.print(s);
 delay(1);
```
14. This line prints a message to the serial monitor indicating that the client has disconnected.
```
 Serial.println("Client disconnected");
 // The client will actually be disconnected
 // when the function returns and 'client' object is destroyed
}
