## Introduction

There’s no existing system to monitor the patients while they are taken to the hospital by emergency vehicles in Sri Lanka. In some scenarios, due to the lack of facilities and resources, patients are transferred from one hospital to another hospital. This can be inconvenient for both parties; the patient and the hospital. It might be a risk to the patient’s life as well. Even after admitting to the hospital, it may take some time to arrange things for the patient and check the status of the patient. Other than the test results, the Status and the condition of the patient are normally conveyed by a guardian of the patient and there can be reliability issues in such information. 

These problems can be addressed separately by a real-time monitoring device for checking the status of the patient and a location tracking system for the ambulance which is connected to a cloud such that hospitals can get information and take decisions. As an example, they can monitor the real-time status of the patient (pulse rate, heart rate etc.) together with a summary report of the patient, and can get the predictions at which time a particular ambulance reaches their hospital. So that hospital staff will get enough time to do the necessary arrangements for that patient and allocate their staff appropriately. Not only that, when considering the emergency vehicle service side(ambulance) they can track the nearest available hospitals for this particular patient after submitting his/her pre-conditions. So, they can directly take patients to the appropriate hospitals without wasting the time. 


## Solution Architecture
![new solution arc](https://user-images.githubusercontent.com/73444543/208265720-25ee0ba3-8126-4050-be56-db9e08c26552.png)

## Hardware and Software Designs
### Hardware Components
**NodeMCU ESP8266**\
![nodemcu](https://user-images.githubusercontent.com/73444543/208266752-962d3ed1-1adb-4f89-8e55-7af7f72bf5d0.jpg)

Microcontroller is like brain of the system because it communicates with inputs and outputs and controls the entire operation of the system. Here we are using NodeMCU ESP8266 as the Microcontroller.It consists of inbuilt WIFI module. Reading longitude and latitude from GPS modem, reading health parameters of the patient from the sensors, desplaying them on a user interfaces and send these data to the cloud are the various functions of the Microcontroller.</p>
</kbd>
**GPS Modem (NEO6MV2)**\
 ![gps](https://user-images.githubusercontent.com/73444543/199442004-74162ede-0182-4212-aa7d-c7a19581b212.jpg)

Main function of GPS modem is provide longitude and latitude of the ambulance to the Microcontroller. It receives data from satellite and transfer them into Microcontroller through serial communication. As ambulance moves along the way from patient’s home to hospital, the co- ordinates of ambulance location will change and these variations are given to Microcontroller.

**GSM Module - SIM800L**\
![GSM](https://user-images.githubusercontent.com/73444543/208266015-cd79e4e7-68e1-4424-9f42-155554595a0f.jpg)

The SIM800L GSM/GPRS module is a miniature GSM modem can be used for normal cell phones to send SMS messages, make phone calls, connect to the Internet via GPRS etc.

**Heart Rate Oxygen Pulse Sensor Module - MAX30100**\
![bpm](https://user-images.githubusercontent.com/73444543/204417296-e6cda821-8f3d-4506-a4fd-d3d5342bab45.jpg)

MAX30100 is a multipurpose sensor used for multiple applications. It is a heart rate monitoring sensor along with a pulse oximeter. The sensor comprises two Light Emitting Diodes, a photodetector, and a series of low noise signal processing devices to detect heart rate and to perform pulse oximetry.

**Temperature Sensor Module - DS18B20**\
![temp](https://user-images.githubusercontent.com/73444543/199442056-3605ccba-edb2-4250-b456-cc2aacf86f1b.jpg)

DS18B20 digital temperature sensor works on a single bus and it has 64-bit ROM to store the serial number of component. It can get quite a few DS18B20 sensors connected to a single bus in parallel. With a microcontroller, you can control so many DS18B20 sensors that are distributed around a wide range.

## Circuit Diagram
![cicuit diagram](https://user-images.githubusercontent.com/73444543/204421503-0e8982d4-ff6d-4d79-807e-af54e95d36df.png)

## UI Design 
### Mobile Application
![1](https://user-images.githubusercontent.com/73444543/204421741-097ead06-a8a0-42b7-9909-e57f2a42749c.jpeg) ![2](https://user-images.githubusercontent.com/73444543/204421756-5044ca8f-5539-4fd2-b548-d2fb9653f210.jpeg) ![3](https://user-images.githubusercontent.com/73444543/204421865-6246a490-6792-408c-a3ea-ab60dfa75b5d.jpeg) ![4](https://user-images.githubusercontent.com/73444543/204421896-f72edcda-189b-4d0e-97a7-b8929cb37fd3.jpeg) ![5](https://user-images.githubusercontent.com/73444543/204421907-ea42e1c7-7321-4937-9499-7467ccd4c7ee.jpeg) ![6](https://user-images.githubusercontent.com/73444543/204422174-d54a3402-d738-479d-ab6f-304f281294c5.jpeg)

### Web Site
![11](https://user-images.githubusercontent.com/73444543/204422296-5a30311c-bf57-4a55-996f-d5d61a02d51a.jpeg)
 ![12](https://user-images.githubusercontent.com/73444543/204422309-84cb99e1-f864-49a1-9c4f-e5c02b12adcd.jpeg) \
![13](https://user-images.githubusercontent.com/73444543/204422321-a20edf16-2f6c-4c07-8dac-eb6b77541fa5.jpeg)
 ![14](https://user-images.githubusercontent.com/73444543/204422332-05087242-e46a-4c22-b2f7-2df2d15c888b.jpeg)
 
## DataBase
Stored Information 
- User Credential details
- Hospital Information

Useful AWS Services 

**AWS Lambda**\
![lambda](https://user-images.githubusercontent.com/73444543/208267083-d9dab665-57b0-40a7-b8e2-d419366a0e64.png)

**Amazon DynamoDB**\
![dynamodb](https://user-images.githubusercontent.com/73444543/208267120-5a4ede32-1d2f-44ba-90c1-380c6b18b202.png)

**Amazon API GAteway**\
![gateway](https://user-images.githubusercontent.com/73444543/208267122-5f6769af-9dc9-43fc-bdc1-9fc36c321e1a.png)

## Testing

Software Testing - Web application
|**Testing Type** | **Functionlities to be checked** | **Software used** |
|-------------|------------------------------|--------------|
|Hardware Testing| Input data from sensors | Platform.io ![platformio](https://user-images.githubusercontent.com/73444543/208268165-b5c0ded8-0424-4fca-b804-30b91765a0a7.png)|
|Web-Application Testing|Login validation | Selenium ![selenium](https://user-images.githubusercontent.com/73444543/208268252-3481923c-5e93-462f-8007-66c98a183359.png) |
|Mobile Application Testing | Login validation | Appium ![appium](https://user-images.githubusercontent.com/73444543/208268362-b6bc9f2e-da5e-4784-b59e-ba37290f0b22.png) |
| API Testing | GET ,DELETE ,PUT requests about users and hospitals| Postman ![postman](https://user-images.githubusercontent.com/73444543/208268493-e550219f-5ca8-47c0-a08b-8120ec53b8fa.png) |

## Security Aspects

- User credentials for both the end users (hospitals, medical officers)
- Connection to the app is authorized by the device
- MQTT - Authentication - AWS certificates
- MQTT - Authorization - AWS Policies
- HTTP - Authentication - AWS certificates
- HTTP - Authorization - AWS Roles
- Both are end-to-end encrypted

## Detailed Budget
|**Item** | **Quantity** | **Price (LKR)** |
|-----|----------|------|
|NodeMCU ESP8266 CP2102 | 1 |From Department|
|Temperature Sensor DS18B20 | 1 | 480 |
|Heart rate & Oxygen sat. level sensor MAX30100 | 1 | 900 |
|GPS Modem NEO6MV2| 1 | 1700 |
|GSM sensor SIM800L | 1 | 2250 |
|128*64 Oled mini display 0.96 inch | 1 | 870 |
|Female to female jumper wires(40pcs) | 1 | 220 |
|Push button, Switch | 1 | 80 |
|Copper board (5cm*7cm) | 1 | 250 |
|4.7k Ohm resistor, LED strips | 2 | 250 |
|Outer cover & Other | - | 3000 |



Considering one device :

Data inputs : 

       pulse rate , heart rate , oxygen saturation - from a real person   
       GPS cordinates :  executing  a given script of GPS cordinates
       
Checking them via Web interface 



## Conclusion

Currently, there’s no system for real-time patient monitoring and updating the hospital from the ambulance exists. Normally medical officers/nurses in there will contact hospitals via mobile calls in critical situations which are not that reliable. And there’s no location tracking or time prediction system for ambulances that exists. Also, in case of finding a suitable hospital, ambulances prefer the nearest hospital or general hospital without considering the conditions or facilities available at the moment which will be caused previously mentioned issues. Considering the current situation regarding this matter, this project will be able to highly contribute to rebuilding this system.
