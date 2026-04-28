# Smart Helmet with Pollution Reduction System, Accident Detection and Alerting System

> **IEEE Conference Publication | CMR Institute of Technology, Bengaluru | 2023**

> Department of Mechanical Engineering & Electronics and Communication Engineering

> **Authors:** Janardhan B V, Naveen Kumar G N, Bhavana Lakshman H, Meenakshi R Patil, **Nikhil Vinayagamurthy**, Tejas B N, Adithya M G

---

## Project Overview

A smart helmet integrating two independently functional embedded systems to address two critical problems faced by motorcycle riders in urban India: **chronic exposure to particulate air pollution** and **delayed emergency response in accidents**.

The **Pollution Reduction System (PRS)** uses a three-layer filter stack driven by an Arduino-controlled DC fan to continuously supply purified air to the rider. The **Accident Detection and Alerting System (ADAS)** monitors vibration and acceleration in real time, and automatically dispatches an SMS with a GPS map link to emergency contacts when a true accident is detected — without any rider action required.

Validated on road in a polluted urban environment, the system demonstrated measurable reduction of particulate matter inside the helmet compared to ambient air levels across a 10-minute continuous test.

---

## Research Problem

> *How can a wearable system autonomously reduce a motorcycle rider's inhalation of PM1.0–PM10 particulates and simultaneously ensure sub-2-minute emergency notification with GPS precision in the event of an accident — without requiring any manual intervention from the rider?*

---

## System Architecture

```
Helmet ON → Module self-check → PRS + ADAS both activate simultaneously
     │
     ├── PRS: Inlet valve → 12V DC fan → 3-layer filter stack → clean air to rider
     │         (Arduino Uno + L298 motor driver controls airflow volume)
     │
     └── ADAS: Accelerometer + Vibration sensor → threshold check
                    │
                    ├── Below threshold → continue monitoring
                    └── Above threshold → 2-min buzzer timer
                              │
                              ├── Reset pressed → false accident → restart
                              └── Not reset → TRUE ACCIDENT
                                        → GPS coordinates collected
                                        → GSM sends SMS + Google Maps link
                                        → Emergency contacts notified
```

---

## Two-System Design

### System 1 — Pollution Reduction System (PRS)

The PRS draws external air through a three-stage filter stack, removing particulates across a full size range before the air reaches the rider.

| Filter Layer | Material | Pore Size | Removes |
|---|---|---|---|
| Layer 1 | Polypropylene | ~10 µm | Dust, sand particles |
| Layer 2 | Silicon Carbide | ~2.5 µm | Fine particulates (PM2.5) |
| Layer 3 | Activated Carbon | Sub-micron | Bacteria, fungi, viruses |

- Airflow controlled by **Arduino Uno + L298 motor driver** driving a **12V DC fan**
- Inlet and outlet valves regulate internal pressure for rider breathing comfort
- Fan speed adjustable to vary clean air volume

### System 2 — Accident Detection and Alerting System (ADAS)

| Component | Role |
|---|---|
| Vibration sensor | Detects physical impact on helmet |
| Accelerometer | Measures deceleration magnitude |
| Arduino Uno | Threshold comparison, timer logic, GSM trigger |
| GPS module | Captures real-time coordinates at accident moment |
| GSM module | Sends SMS + initiates call to emergency contacts |
| Buzzer | 2-minute alert window for false-accident cancellation |
| Reset button | Pressed within 2 min → classified as false accident |

**False accident logic:** A 2-minute countdown distinguishes accidental drops or minor impacts from true accidents. If the rider does not press reset within 2 minutes, the system treats the event as a true accident and triggers the alert sequence automatically.

---

## Alert Output

When a true accident is detected, emergency contacts receive:

1. An **SMS** stating `EMERGENCY` with a clickable **Google Maps link** to the exact accident coordinates
2. A **follow-up GPS coordinate update** if the emergency service replies with `RING`
3. The location is viewable directly in Google Maps or any browser via the coordinates

---

## Results

### Pollution Reduction System Efficiency

PM2.5 levels measured simultaneously inside and outside the helmet using two **GP2Y1010AU0F Dust Smoke Particle Sensors** while riding in a polluted urban environment over 10 minutes (data logged every 2 seconds).

| Measurement Point | PM level (µg/m³) |
|---|---|
| Outside helmet (ambient) | Peak: ~650 µg/m³, avg significantly elevated |
| Inside helmet (filtered) | Consistently and substantially lower throughout test |

The inside-helmet readings remained well below ambient levels across the full 10-minute test, confirming effective particulate filtration during real road conditions.

### Accident Detection System

| Scenario | Outcome |
|---|---|
| Helmet dropped (false accident) | Buzzer triggered; reset pressed within 2 min → no SMS sent |
| Simulated true accident (no reset) | GPS collected; SMS + Google Maps link sent to emergency contact within 2-minute window |
| System startup | Welcome SMS sent to synced contacts confirming all modules operational |

---

## Hardware Stack

| Component | Specification |
|---|---|
| Microcontroller | Arduino Uno |
| Fan | 12V DC fan |
| Motor driver | L298 / LM298 |
| Air quality sensor | PM2.5 GP2Y1010AU0F |
| Impact detection | Vibration sensor + Accelerometer |
| Location | GPS module |
| Communication | GSM module |
| Power | Rechargeable battery + charging module |
| User interface | Reset button, ON/OFF button, power indicator LEDs |

---

## System Flow

**Startup → Module Check → PRS + ADAS Active → Continuous Monitoring → Accident Logic → Emergency Alert**

See `Smart_Helmet_IEEE_Paper.pdf` for full flow chart, circuit diagrams, hardware photographs, and sensor placement details.

---

## Publication

**Title:** Smart Helmet With Pollution Reduction System, Accident Detection And Alerting System

**Published in:** IEEE Conference Proceedings

**IEEE Xplore DOI:** *(https://ieeexplore.ieee.org/document/10593979)*

**Authors:** Janardhan B V · Naveen Kumar G N · Bhavana Lakshman H · Meenakshi R Patil · **Nikhil Vinayagamurthy** · Tejas B N · Adithya M G

---

## Tools & Skills

- Embedded C / Arduino IDE
- Arduino Uno, GSM, GPS, accelerometer, vibration sensor integration
- Motor driver control (L298) for DC fan speed regulation
- PM2.5 optical dust sensor calibration and data logging
- IoT system design - multi-module integration and self-check logic
- Real-time SMS alerting via GSM with GPS coordinate payload

---

## Affiliation

**CMR Institute of Technology, Bengaluru, Karnataka, India**
Department of Mechanical Engineering & Department of Electronics and Communication Engineering

---

