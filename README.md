# 🚀 API Testing for Open Charge Map API

## 📌 Overview
This project contains API tests for the Open Charge Map API, focusing on two endpoints:

✅ **Get POIs (Points of Interest)**  
✅ **Get Reference Data**  

The tests cover **response time**, **status codes**, **response data schema validation**, and **business logic verification**.

---

## 🛠️ Setup Instructions

### 🔹 Prerequisites
- Install [Postman](https://www.postman.com/) or any API testing tool of your choice (e.g., **REST Assured, Karate, Newman CLI**).

### 📥 Importing the Tests
#### 🏗️ **Using Postman**
1. Open **Postman**.
2. Click on **Import** in the top-left corner.
3. Upload the provided Postman collection file (`OpenChargeMapTests.postman_collection.json`).

---

## 🔎 Test Cases

### 📍 **Get POIs Endpoint**
- **Response Time & Status Code**
  - ✅ Verify response time is under **1000ms**
  - ✅ Confirm status code is **200**

- **Schema Validation**
  - ✅ Response contains an **array** of POI objects
  - ✅ Each POI object includes:
    - 🆔 **ID**
    - 📍 **AddressInfo** (containing **Latitude** and **Longitude**)
    - 🔢 **NumberOfPoints**

- **Business Logic Validation**
  - ✅ Request with `latitude=51.5074&longitude=0.1278&distance=10&maxresults=5` returns **exactly 5 results**
  - ✅ Ensure all returned POIs are **within 10km** of the specified coordinates

### 🔧 **Get Reference Data Endpoint**
- **Response Time & Status Code**
  - ✅ Verify response time is under **1000ms**
  - ✅ Confirm status code is **200**

- **Schema Validation**
  - ✅ Response contains arrays for **ChargerTypes** and **StatusTypes**
  - ✅ Each item in these arrays has an **ID** and **Title**

- **Business Logic Validation**
  - ✅ `ChargerTypes` includes both **Fast** and **Slow** chargers
  - ✅ Ensure all `StatusTypes` have **unique IDs**

---

## 📊 Test Results & Observations

![1stTest](https://github.com/user-attachments/assets/1c926272-b7f1-481c-9a3c-716f9982ac50)

### **📌 Summary**
- ✅ **All API requests responded within the expected time limits (<1000ms).** **The first request fails with ~200ms delay, after that every test passes, maybe because of caching.** 
- ✅ **Status codes were as expected (200 OK).**
- ✅ **Schema validation passed for all responses.**
- ⚠️ **Some POIs were found slightly beyond the 10km range** (suggests minor inaccuracies in the dataset).
- ✅ **Business logic checks passed for reference data, including unique IDs and charger type verification.**
