# 7n8n-api-weather-pipeline

# 🌤️ Project 08: Automated API Data Pipeline (GET to POST)

![n8n](https://img.shields.io/badge/n8n-FF6D5W?style=for-the-badge&logo=n8n&logoColor=white)
![API Integration](https://img.shields.io/badge/API_Integration-005571?style=for-the-badge&logo=api&logoColor=white)

## 📖 Overview

This project is an end-to-end API integration built in n8n. It demonstrates how to fetch real-time data from a third-party public API using an HTTP GET request, extract the required values, and send the cleaned result to a client system through an HTTP POST request.

The workflow simulates a real operational need in the logistics industry, where temperature data in Jakarta must be delivered automatically to a dashboard without manual input.

> Note: This is a personal case study simulating a real-world logistics operational requirement.

---

## 🏢 Business Problem

A logistics company relies on real-time weather information, especially the temperature in Jakarta, to support its daily fleet operations.

- The bottleneck: Admin staff manually check weather websites every hour and type the current temperature into the company dashboard.
- The risk: This process is time-consuming, prone to human error, and not scalable for 24/7 operations.
- The impact: Delays in temperature updates can affect operational planning and decision-making.

---

## 💡 Proposed Solution

An automated pipeline runs on a schedule, fetches the latest temperature from a reliable public API, transforms the data into a structured JSON payload, and sends it directly to the company's receiving endpoint.

This approach eliminates repetitive manual work, reduces human error, and ensures the operational dashboard always has near real-time data.

---

## ⚙️ Workflow Architecture

1. Schedule Trigger
   - Starts the workflow on a recurring interval (simulated hourly execution).

2. HTTP Request (GET)
   - Connects to the Open-Meteo API to retrieve current weather data for Jakarta.
   - Coordinates: Latitude -6.2088, Longitude 106.8456

3. Data Extraction & Formatting
   - Extracts the `temperature` value.
   - Formats it as a Number instead of a string so the receiving dashboard can process it correctly for chart plotting.

4. HTTP Request (POST)
   - Sends the final JSON payload to the client webhook server.

<img width="676" height="305" alt="Workflow architecture diagram" src="https://github.com/user-attachments/assets/73c59714-57b5-4a67-bf60-587c357b6970" />

---

## 🛠️ Technical Specs & Data Structure

### Outgoing Payload (POST to Client Dashboard)

```json
{
  "kota": "Jakarta",
  "suhu_saat_ini": 33.7
}
```

This payload is simple, machine-readable, and suitable for direct use in a dashboard or operational system.

The value `suhu_saat_ini` is sent as a float/number instead of a string to avoid parsing and charting issues.

<img width="719" height="755" alt="API and payload configuration screenshot" src="https://github.com/user-attachments/assets/b118c384-45f4-49f1-b457-95a51dc37c0c" />

---

## 📈 Business Value

- Zero Manual Data Entry
  - Saves admins approximately 14 hours of repetitive work per week.

- 100% Real-Time Accuracy
  - Data is pulled and pushed automatically, reducing human error and delays.

- System Compatibility
  - The correctly formatted JSON allows the dashboard to read and visualize data immediately without breaking.

- Operational Efficiency
  - Helps the company make faster and more reliable decisions based on current conditions.

---

## ✅ Outcome

This project demonstrates a practical n8n workflow for integrating external APIs into business operations and automating data delivery between systems without human intervention.

It reflects a realistic automation use case where data integration improves reliability, speed, and operational efficiency.

---

Note: In collaboration with Gemini Pro.
