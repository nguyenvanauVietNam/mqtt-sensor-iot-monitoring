# mqtt-sensor-iot-monitoring
SmartSensorHub: A multi-platform IoT project that simulates sensor data (C++ on Linux), processes and stores data on a Python-based server (Windows 10), and visualizes sensor readings with real-time charts in a C# WPF application (Windows 11).


# IoT Monitoring System

---

## Overview
This project focuses on creating a multi-platform IoT system for simulating, storing, and visualizing sensor data. It involves three main components:

1. **C++ on Linux**: Simulate sensor data and send it to a central MQTT broker.
2. **Python on Windows 10**: Act as the server to receive, process, and store sensor data in a MySQL database.
3. **C# WPF on Windows 11**: Visualize the real-time data using charts and implement AI for image analysis.

---

## Step 1: Setting up MQTT Broker

1. **Install Eclipse Mosquitto** (on Linux):
   ```bash
   sudo apt update
   sudo apt install mosquitto mosquitto-clients
   ```
2. Start the broker:
   ```bash
   sudo systemctl start mosquitto
   ```
3. Test the broker:
   ```bash
   mosquitto_sub -h localhost -t test/topic
   mosquitto_pub -h localhost -t test/topic -m "Hello MQTT"
   ```

---

## Step 2: C++ MQTT Application

1. **Install Dependencies**:
   - Install Paho MQTT C++ library from [Eclipse Paho](https://github.com/eclipse/paho.mqtt.cpp).

2. **Write the Simulation Code**:
   - Simulate the following sensors:
     - Soil Temperature and Moisture
     - Light Intensity
     - Air Humidity and Temperature
     - CO2 and O2 Concentration
     - Water Flow
   - Structure the data in JSON format, e.g.:
     ```json
     {
         "sensor_type": "temperature",
         "value": 25.3,
         "timestamp": "2024-12-22T12:00:00Z"
     }
     ```

3. **Send Data via MQTT**:
   - Publish data to the MQTT broker.

4. **Compile and Run**:
   - Use `g++` to compile and run the program.

---

## Step 3: Python Server

1. **Install Required Libraries**:
   ```bash
   pip install paho-mqtt mysql-connector-python
   ```

2. **Create a MySQL Database**:
   - Set up a database and table:
     ```sql
     CREATE DATABASE sensor_data;
     USE sensor_data;
     CREATE TABLE sensor_readings (
         id INT AUTO_INCREMENT PRIMARY KEY,
         sensor_type VARCHAR(50),
         value FLOAT,
         timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
     );
     ```

3. **Write the MQTT Listener**:
   - Subscribe to sensor topics and save incoming data to MySQL.

4. **Test the Server**:
   - Run the Python script and verify that data is stored in the database.

---

## Step 4: C# WPF Application

1. **Set Up the Project**:
   - Create a new WPF project in Visual Studio.

2. **Install MQTT Library**:
   - Use [MQTTnet](https://github.com/dotnet/MQTTnet) for MQTT communication.

3. **Build the Interface**:
   - Design a dashboard to:
     - Display sensor data in real-time.
     - Plot charts using LiveCharts or OxyPlot.

4. **Integrate AI for Image Processing**:
   - Use ML.NET or OpenCV for basic image analysis.

---

## Step 5: Testing and Deployment

1. **Testing**:
   - Verify communication between all components.
   - Ensure real-time updates on the dashboard.

2. **Deployment**:
   - Package each component separately.
   - Document how to set up the system.

---

## Future Improvements

- Add support for more sensors.
- Implement cloud storage for data.
- Enhance AI capabilities for better image processing.

---

## References

- [Paho MQTT Documentation](https://www.eclipse.org/paho/)
- [LiveCharts for WPF](https://lvcharts.com/)
- [MySQL Python Connector](https://dev.mysql.com/doc/connector-python/en/)
- [MQTTnet for C#](https://github.com/dotnet/MQTTnet)
- [OpenCV for C#](https://github.com/shimat/opencvsharp)

