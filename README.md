# 7n8n-api-weather-pipeline

# 🌤️ Project 08: Automated API Data Pipeline (GET to POST)

![n8n](https://img.shields.io/badge/n8n-FF6D5W?style=for-the-badge&logo=n8n&logoColor=white)
![API Integration](https://img.shields.io/badge/API_Integration-005571?style=for-the-badge&logo=api&logoColor=white)

## 📖 Overview
This project is an end-to-end API integration built in **n8n**. It demonstrates the ability to extract data from a third-party public API using an HTTP GET request, isolate specific data points, strictly format the JSON payload, and push it to an external server/dashboard using an HTTP POST request.

*Note: This is a personal case study simulating a real-world logistics operational requirement.*

---

## 🏢 Business Problem
A logistics company relies on real-time weather data (temperature) in Jakarta to manage fleet operations. 
- **The Bottleneck:** Admins have to manually check weather websites every hour and type the current temperature into the company's operational dashboard. 
- **The Risk:** This manual process is time-consuming, prone to human error (typos), and impossible to maintain 24/7 without delays.

## 💡 Proposed Solution
An automated pipeline that runs on a schedule, fetches the exact current temperature via a reliable API, formats the data into a machine-readable JSON structure, and pushes it directly to the company's webhook.

### ⚙️ Workflow Architecture
1. **Schedule Trigger:** Initiates the workflow (simulated for hourly execution).
2. **HTTP Request (GET):** Connects to the Open-Meteo API to pull current weather data for Jakarta (Lat: -6.2088, Lon: 106.8456).
3. **Data Extraction & Formatting:** Extracts the `temperature` variable and formats it strictly as a `Number` data type (not a string) so the receiving dashboard can plot charts.
4. **HTTP Request (POST):** Pushes the clean JSON payload to the client's webhook server.

<img width="676" height="305" alt="image" src="https://github.com/user-attachments/assets/73c59714-57b5-4a67-bf60-587c357b6970" />


---

## 🛠️ Technical Specs & Data Structure

**Outgoing Payload (POST to Client Dashboard):**
```json
{
  "kota": "Jakarta",
  "suhu_saat_ini": 33.7
}

<img width="719" height="755" alt="image" src="https://github.com/user-attachments/assets/b118c384-45f4-49f1-b457-95a51dc37c0c" />


(Notice: The temperature is passed as a Float/Number to comply with charting system requirements, avoiding string concatenation errors).

📈 Business Value
Zero Manual Data Entry: Saves admins ~14 hours of repetitive tasks per week.

100% Real-Time Accuracy: Data is pulled and pushed machine-to-machine, eliminating human typos.

System Compatibility: The correctly formatted JSON ensures the client's dashboard can immediately read and visualize the data without breaking.

Note : incollaboration with gemini Pro 
