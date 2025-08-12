
# 🌐 RESTful-Booker API Testing with Postman & Newman
## 📖 Overview
This project demonstrates automated API testing for the [RESTful-Booker API](https://restful-booker.herokuapp.com/) using **[Postman](https://www.postman.com/)** and **[Newman](https://www.npmjs.com/package/newman)**.It includes a complete test collection covering CRUD operations with dynamic data handling, environment variables, pre-request scripts, and detailed HTML reports.

## ✨ Key Features
- ✅ Full CRUD Coverage: GET, POST, PUT, PATCH, DELETE
- 🔄 Dynamic Data Generation using Postman variables and scripts
- 🌍 Environment Management for switching between different setups
- 📝 Pre-request Scripts for data preparation
- 🔍 Assertions & Validations with JavaScript test scripts
- 📊 Detailed HTML Reports with Newman HTML Extra Reporter

## 📄 API Documentation
- Official RESTful-Booker API Docs → **[RESTful-Booker API Reference](https://restful-booker.herokuapp.com/apidoc/index.html#api-Booking)**
  
## 🛠 Technologies Used
| Tool / Tech                    | Purpose                                             |
| ------------------------------ | --------------------------------------------------- |
| **Postman**                    | API request creation, scripting, and test execution |
| **Newman**                     | Command-line test runner for Postman collections    |
| **Newman HTML Extra Reporter** | Enhanced HTML reporting                             |
| **Node.js**                    | Runtime environment for Newman                      |

## 📌 Prerequisites
Before running the tests, ensure you have:
- Node.js installed → **[Download Here](https://nodejs.org/en/download)** 
- Postman installed → **[Download Here](https://www.postman.com/downloads/)**

## Install Newman globally ##
```bash
npm install -g newman
```
**Install Newman HTML Extra Reporter globally**
```bash
npm install -g newman-reporter-htmlextra
```
  
**1.📥 Installation**
Clone this repository
```
- git clone https://github.com/your-username/restful-booker-api-testing.git
- cd restful-booker-api-testing
```
  
## Import the Postman Collection & Environment ##
- Open Postman
- Click Import
- Select the collection **.postman_collection.json and
  environment **.postman_environment.json files from the repository
