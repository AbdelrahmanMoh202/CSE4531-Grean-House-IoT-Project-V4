# CSE4531-Grean-House-IoT-Project-V4
Green House IoT Project
1.	Project Overview 
Environmental Monitoring:
•	Monitor temperature and humidity using the DHT11 sensor.
•	Monitor ambient light intensity using an LDR sensor.
Device Automation:
•	Control a fan based on temperature levels.
•	Control a humidity regulator based on humidity levels.
•	Control a lighting system based on ambient light levels.
IoT Integration:
•	Send real-time environmental data (temperature, humidity, and light intensity) to the GSM module for remote monitoring and analysis.
•	Using the provided library on SIM900D to perform mobile communication.
Simulate the Design:
•	Implement and verify the functionality in the Proteus simulation environment.

2.	Code explaining:
Initialization

•	DHT11 Setup: Initializes the temperature and humidity sensor using the DHT.h library.

•	LDR Setup: Reads ambient light levels from the LDR connected to analog pin A0.

•	GSM module Setup: Establishes mobile communication with the SIM900D module and connects to the Mobile number specified.

Device Control
•	Fan: Activates when the temperature exceeds 30°C.

•	Humidity Regulator: Activates when humidity falls below 60%.

•	Lighting System: Activates when the ambient light intensity (LDR reading) is below 19.1.

Data Logging

•	Sends temperature, humidity, and light intensity data to the GSM module using a mobile sim card request.

External Libraries:
DHT.h:
•	Functions for reading temperature and humidity.
•	Simplifies interfacing with the DHT11 sensor.
GSM:
•	Handles GSM communication, including sending Message publishing requests to the mobile number SIM card.

3. Output:
1.	Proteus Simulation:
•	The fan, humidity regulator, and lighting system respond appropriately to changes in sensor data.
•	The virtual terminal displays GSM responses from Mobile phone.
2.	IoT Platform:
•	Sensor data is successfully logged to the mobile platform and can be read remotely.
Results:
1.	Automation: The devices respond dynamically based on environmental conditions.
2.	IoT Connectivity: Data is reliably transmitted to GSM, enabling mobile monitoring.
3.	Validation: Proteus simulation confirms that the system behaves as expected.
