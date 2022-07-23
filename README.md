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
         
         
## - Establishing a web Server 


         #include <ESP8266WiFi.h>        // Include the Wi-Fi library
         #include <ESP8266WebServer.h>

         const char* ssid = "ABbkareno Wifi";
         const char* password = "12345678";  //Enter Password here
         ESP8266WebServer server(80);


        void setup()
            {
              Serial.begin(115200);         // Start the Serial communication to send messages to the computer
              WiFi.mode(WIFI_AP);

              WiFi.softAP(ssid, password);
  
              IPAddress myIP = WiFi.softAPIP();
              Serial.print("AP IP address: ");
               Serial.println(myIP);
 
             // Starting WEB-server 
              server.begin();
               Serial.println("HTTP server started"); 
           }

        void loop()
           {
           }
## - Establishing a web Server Create HTML 

              #include <SoftwareSerial.h>
              #include <ESP8266WiFi.h>       
              #include <ESP8266WebServer.h>
              
              //Server name and password
              const char* ssid = "ABbkareno Wifi";
               const char* password = "12345678";  //Enter Password here
              ESP8266WebServer server(80);

              String header;
              
               void setup() 
               {
                 Serial.begin(115200);  
                 
                   // Server Start code
                   WiFi.mode(WIFI_AP);
                   WiFi.softAP(ssid, password);
                    IPAddress myIP = WiFi.softAPIP();
                   Serial.print("AP IP address: ");
                    Serial.println(myIP);
                   // Starting WEB-server
                   server.begin();
                   Serial.println("HTTP server started");
                   
                   void loop() 
                   {
                   }
 
 
                   String SendHTML() {

                   String value = server.arg("value"); //this lets you access a query param (http://x.x.x.x/action1?value=1)
                     int number = value.toInt(); 
                     String s = " <!DOCTYPE html> <html>";
                     s += "<head><meta name='viewport' content='width=device-width, initial-scale=1'> <title>GPS DATA</title> <style>";
                     s += "<style>html, body { font-family: Helvetica; display: block; margin: 0px auto; text-align: center;}";
                     s += ".button { background-color: #209e48; border: none; color: white; padding: 12px 24px;";
                     s += "text-decoration: none; font-size: 20px; margin: 2px; cursor: pointer;}";
                     s += ".button2 {background-color: #c20a0a;}";
                     s += ".textbox {width: 80px; border: 1px solid #333; padding: 16px 20px 0px 24px; background-image: linear-gradient(180deg, #fff, #ddd 40%, #ccc);}";
                     s += ".mytext {font-size: 16px; font-weight:bold; font-family:Arial ; text-align: justify;}";
                      s += "#container {width: 100%; height: 50px; margin-left: 5px; margin-top: 20px; padding: 10px; display: -webkit-flex; -webkit-justify-content: center; display: flex; justify-content: center;} ";

                     s += "a:link {background-color: YELLOW;text-decoration: none;}";
                     s += "table, th, td </style> </head> <body> <h1  style=";
                     s += "font-size:300%;";
                     s += " ALIGN=CENTER> GPS DATA</h1>";
                     s += "<p ALIGN=CENTER style=""font-size:150%;""";
                      s += "> <b>Location Details</b></p> <table ALIGN=CENTER style=";
                     s += "width:50%";
                      s += "> <tr> <th>Latitude</th>";
                      s += "<td ALIGN=CENTER >";

                      s += "</td> </tr> <tr> <th>Longitude</th> <td ALIGN=CENTER >";

                      s += "</td> </tr> <tr>  <th>Date</th> <td ALIGN=CENTER >";
 
                       s += "</td></tr> <tr> <th>Time</th> <td ALIGN=CENTER >";
 
                       s += "</td>  </tr> </table> ";
 

                       s += "</body> </html>";
                        return s;
                         }
