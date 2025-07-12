
# 🌡️ Temperature-Control-Library

A complete **PLC automation library** featuring modular and reusable components for **temperature control** and **liquid level management**. This project is ideal for automation students, engineers, and PLC programmers looking to simulate or build a real-time industrial process control system.

The project is developed using **Siemens TIA Portal** with structured PLC logic and a user-friendly **HMI interface using faceplates**. The faceplates make it easy to reuse control blocks across multiple devices or zones.

---

## 📋 Introduction

Industrial process control often involves managing variables like **temperature** and **liquid levels** in tanks. This repository provides two core simulation models for controlling:

1. A **heater system**, where you can observe how temperature reacts when a heater is turned ON or OFF.
2. A **tank system**, where you can observe fluid levels change based on fill and drain valve positions.

Each control system includes simulation logic in a PLC programming language (Structured Text), an HMI layout for user interaction, and a sample video tutorial to help you visualize the process.

---

## 📂 Contents

- ✅ Task 1: Temperature Control Logic
- ✅ Task 2: Liquid Level Control Logic
- 🖥️ HMI Screens with Faceplates
- 🎥 Demonstration Video
- 📌 License and Contributors

---

## 🔧 Task 1: Temperature Control

### 🎯 Objective:
Simulate a simple thermal control system where a heater affects the temperature over time.

### 🧩 System Components:

- 🔘 Heater (BOOL) — Turns the heater ON or OFF.
- 🌡️ Temperature Sensor (REAL/FLOAT) — Simulated temperature value.

### ⚙️ Logic Description:

- When the heater is ON (`Heater = TRUE`), temperature increases at **0.5 °C per second**.
- When the heater is OFF (`Heater = FALSE`), temperature decreases at **0.25 °C per second**.
- The temperature value is constrained between **0°C and 100°C** to simulate realistic limits.

### 💻 Example Code (Structured Text):

```pascal
IF Heater THEN
    Temperature := Temperature + 0.5 * CycleTime; // Increase temp
ELSE
    Temperature := Temperature - 0.25 * CycleTime; // Decrease temp
END_IF;

// Clamp between 0 and 100
IF Temperature > 100 THEN
    Temperature := 100;
ELSIF Temperature < 0 THEN
    Temperature := 0;
END_IF;
```

### 🧠 Notes:

- `CycleTime` is the PLC scan cycle time (in seconds). You can replace this with a constant like `0.1` for 100 ms scan time.
- This logic is ideal for simulation or educational use.

---

## 🌊 Task 2: Liquid Level Control

### 🎯 Objective:
Control and simulate the level of fluid in a tank based on how much a fill and drain valve is opened.

### 🧩 System Components:

- 🚰 Fill Valve (REAL, 0–10V = 0–100%) — Controls fluid inflow.
- 🕳️ Drain Valve (REAL, 0–10V = 0–100%) — Controls fluid outflow.
- 📈 Liquid Level (REAL) — Percentage level in tank (0–100%).
- 🔴 High Level Alarm (BOOL) — Activated if level > 80%.
- 🟡 Low Level Alarm (BOOL) — Activated if level < 20%.

### ⚙️ Logic Description:

```pascal
FillRate := FillValve * 0.1; // 10V = 10%/s
DrainRate := DrainValve * 0.1;

Level := Level + (FillRate - DrainRate) * CycleTime;

// Clamp Level
IF Level > 100 THEN
    Level := 100;
ELSIF Level < 0 THEN
    Level := 0;
END_IF;

// Alarms
HighLevelAlarm := Level > 80;
LowLevelAlarm := Level < 20;
```

### 📊 Simulation Scenarios:

| Fill Valve | Drain Valve | Net Change  | Effect                  |
|------------|-------------|-------------|--------------------------|
| 100%       | 0%          | +10%/s      | Fast filling             |
| 0%         | 100%        | -10%/s      | Fast draining            |
| 50%        | 50%         | 0%/s        | No change                |
| 25%        | 50%         | -2.5%/s     | Slow draining            |
| 50%        | 25%         | +2.5%/s     | Slow filling             |

### 🧠 Notes:

- This logic can be easily extended to add PID control, emergency shutoffs, or graphical trend monitoring.

---

## 🖥️ HMI Design (Faceplates)

The HMI interface was built using **Siemens WinCC** in TIA Portal. To make the system modular, we used **faceplates**, which are like visual function blocks — easily copy-pasteable.

### 🧾 Faceplate Features:

- ▶️ Start / ⏹️ Stop buttons for manual control.
- 🔄 Reset to initialize values.
- 🔘 Heater ON/OFF status.
- 🌡️ Real-time value display.

📸 Sample HMI Screenshot:

![HMI Screenshot](68f2f0f7-b1e5-42f0-a43b-3e5c14311bcd.png)

---

## 🎥 Demo Video

Watch a detailed tutorial and live demonstration of the project:

📺 [Watch the video on YouTube](https://www.youtube.com/watch?v=Oln25NhrU5M)

---

