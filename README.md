

# **GPS Data Logger - TinyGPS++** 🌍📡  

This project uses the **TinyGPS++** library to interface with a GPS module and logs location, speed, altitude, and other GPS-related information. The data is printed on the Serial Monitor, with the option to extend this project for data logging or further processing.  

---

## **✨ Features**  

- **GPS Location**: Logs latitude and longitude with high precision.  
- **Speed**: Displays the speed in kilometers per hour (km/h).  
- **Altitude**: Outputs altitude in meters.  
- **HDOP**: Horizontal Dilution of Precision (HDOP) for location accuracy.  
- **Satellites**: Displays the number of satellites used for position fix.  
- **Time**: Shows the UTC time and date for synchronization.  

---

## **📂 Folder Structure**  

- `GPS_Data_Logger.ino`  
  - Main Arduino sketch file that interfaces with the GPS module and displays data.  
- `README.md`  
  - Documentation for the project.  
- `LICENSE`  
  - Open-source license details (if applicable).  

---

## **🔧 Hardware Components**  

- **GPS Module** (e.g., NEO-6M or similar)  
  - For receiving GPS signals and providing location data.  
- **Microcontroller**  
  - Compatible with Arduino or ESP32/ESP8266 boards.  
- Jumper wires  
- Breadboard (optional)  
- Power supply for your microcontroller (e.g., USB cable)  

---

## **🔌 Circuit Connections**  

| Component        | Pin Assignment  |  
|------------------|-----------------|  
| **GPS RX**       | GPIO 16 (RXD2)  |  
| **GPS TX**       | GPIO 17 (TXD2)  |  
| **Microcontroller** | Any compatible Arduino/ESP32 board |

---

## **⚙️ Software Requirements**  

- Arduino IDE (version 1.8.10 or later)  
- TinyGPS++ library:  
  ```bash
  Install from Arduino Library Manager
  ```  

---

## **🚀 How to Use**  

1. **Setup**  
   - Connect the GPS module to your microcontroller's RX and TX pins.  
   - Ensure your GPS module is properly powered (e.g., via 5V or 3.3V depending on your module).  

2. **Upload Code**  
   - Open the `GPS_Data_Logger.ino` file in Arduino IDE.  
   - Ensure the correct board and port are selected under **Tools**.  
   - Upload the code to your microcontroller.  

3. **Monitor the Output**  
   - Open the Serial Monitor (set baud rate to 115200).  
   - Watch as the location, speed, altitude, HDOP, satellites, and UTC time are displayed.  

4. **Extend the Project**  
   - This project can be extended to log data to an SD card, display information on an LCD, or even send the data to a cloud service for further analysis.  

---

## **💡 Code Overview**  

- **Serial Communication**  
  - Uses `HardwareSerial` to communicate with the GPS module via Serial 2 (pins RXD2 and TXD2).  
  - The GPS module transmits data, which is then decoded and displayed.  

```cpp
// GPS Encoding and Data Display
while (gpsSerial.available() > 0) {
  gps.encode(gpsSerial.read());
}
if (gps.location.isUpdated()) {
  Serial.print("LAT: ");
  Serial.println(gps.location.lat(), 6);
  Serial.print("LONG: ");
  Serial.println(gps.location.lng(), 6);
  Serial.print("SPEED (km/h): ");
  Serial.println(gps.speed.kmph());
  // Additional GPS data...
}
```

- **Data Logging**  
  - For every GPS update, latitude, longitude, speed, altitude, and time are printed on the Serial Monitor.  

---

## **📜 License**  

This project is licensed under the **MIT License**. See the `LICENSE` file for details.  

---

## **🤝 Contributing**  

Contributions are welcome! You can:  
- Submit a pull request with new features or bug fixes.  
- Open an issue to report bugs or suggest improvements.  

---

## **💬 Feedback**  

For questions, suggestions, or feedback, feel free to open an issue or contact me directly.  

--- 

Happy Coding! 🎉  

