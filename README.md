# NodeMCU-ESP8266 
## - Establishing a Wi-Fi connection

     #include <ESP8266WiFi.h>        // Include the Wi-Fi library

      const char* ssid     = "SSID";         // The SSID (name) of the Wi-Fi network you want to connect to
      const char* password = "PASSWORD";     // The password of the Wi-Fi network

      void setup()
       {
         Serial.begin(115200);         // Start the Serial communication to send messages to the computer
          delay(10);
          Serial.println('\n');
  
          WiFi.begin(ssid, password);             // Connect to the network
          Serial.print("Connecting to ");
          Serial.print(ssid); Serial.println(" ...");

          int i = 0;
           while (WiFi.status() != WL_CONNECTED)
           { // Wait for the Wi-Fi to connect
             delay(1000);
             Serial.print(++i); Serial.print(' ');
           }

        Serial.println('\n');
        Serial.println("Connection established!");  
        Serial.print("IP address:\t");
        Serial.println(WiFi.localIP());         // Send the IP address of the ESP8266 to the computer
       }

      void loop()  
      { }

## - Access Point mode


        #include <ESP8266WiFi.h>        // Include the Wi-Fi library

         const char *ssid = "ESP8266 Access Point"; // The name of the Wi-Fi network that will be created
         const char *password = "thereisnospoon";   // The password required to connect to it, leave blank for an open network

         void setup() 
         {
              Serial.begin(115200);
              delay(10);
              Serial.println('\n');

               WiFi.softAP(ssid, password);             // Start the access point
              Serial.print("Access Point \"");
              Serial.print(ssid);
              Serial.println("\" started");

              Serial.print("IP address:\t");
              Serial.println(WiFi.softAPIP());         // Send the IP address of the ESP8266 to the computer
         }

         void loop()
         { 
         }
