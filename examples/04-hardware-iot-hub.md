<!-- DO NOT COPY VERBATIM - REFERENCE FOR DIVERSE MENTAL MODELS ONLY -->
# Reference Example 4: Greenhouse IoT Controller ("FloraLink")

> **Domain**: Embedded Systems / IoT Hardware (ESP32 + FreeRTOS + MQTT)  
> **Persona Level**: Mid (Embedded engineer, strong C/C++ background, pragmatic about wireless constraints)  
> **Notice**: Demonstrates how interview focuses on power budgeting, sensor drift, intermittent Wi-Fi connectivity, and fail-safe physical actuators (solenoid valves).

---

## 1. Vision & Core Problem
- **1-Sentence Definition**: An off-grid, solar-assisted IoT controller box that regulates water pumping, nutrient dosing, and ventilation for automated hydroponic greenhouses while logging telemetry to local SD storage during cellular outages.
- **The Core Problem**: Standard consumer smart-plug controllers rely on 24/7 cloud internet. When farm connectivity drops during summer storms, pumps freeze in the "open" or "closed" state, killing \$15,000 worth of crops in 6 hours.
- **Distinguishing Facets**:
  1. *Fail-Safe Closed Valve Relays*: Solenoids are spring-loaded normally closed (NC); loss of power halts water flow immediately.
  2. *Offline Local Rule Engine*: Water schedules run on the ESP32 RTC (Real-Time Clock) without needing cloud NTP.
  3. *Flash Flash Wear-Leveling*: Telemetry written to SD card using circular buffer to prevent SD flash degradation.

---

## 2. In-Scope vs. Non-Goals
- **In-Scope (MVP)**:
  - ESP32-S3 microcontroller reading 4 analog soil sensors, pH probe, EC probe, and ambient temp/humidity.
  - Driving 4 12V relays for irrigation solenoids and exhaust fans based on local threshold rules.
  - BLE provisioning interface for initial mobile Wi-Fi / MQTT broker pairing.
- **Explicit Non-Goals**:
  - ❌ No machine learning computer vision yield prediction models on the microchip.
  - ❌ No live HD video streaming from the greenhouse canopy.
  - ❌ No custom injection-molded enclosure design (using standard IP67 off-the-shelf junction box).

---

## 3. Blast Radius & Worst-Case Failure
- **Worst-Case**: Relay jams in the "ON" position, flooding the nursery floor and burning out pump motors.
- **Mitigation Architecture**: Hardware watchdog timer + maximum continuous run limit (firmware cuts relay after 90 seconds regardless of software state).

---

## 4. Definition of Done
1. Controller operates continuously on test bench for 72 hours without memory leaks or watchdog resets.
2. Relays actuate within 500ms of simulated soil moisture drop below 20%.
3. System survives Wi-Fi router disconnect for 24 hours and successfully transmits backlogged MQTT events upon reconnect.
