
## 🌐 RESTful-Booker API Testing with Postman & Newman 
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

 Install Newman globally
```bash
npm install -g newman
```

Install Newman HTML Extra Reporter globally
```bash
npm install -g newman-reporter-htmlextra
```
  
📥 Installation**
Clone this repository
```
git clone https://github.com/your-username/restful-booker-api-testing.git
cd restful-booker-api-testing
```
  
Import the Postman Collection & Environment 
- Open Postman
- Click Import
- Select the collection (*.postman_collection.json) and
  environment (*.postman_environment.json) files from the repository

## 🚀 Running the Tests
Run in Command Prompt (CMD)
```
newman run restful-booker.postman_collection.json \
  -e restful-booker.postman_environment.json
```

## Run with HTML Report
```
newman run restful-booker.postman_collection.json \
  -e restful-booker.postman_environment.json \
  -r cli,htmlextra
```

## 🧪 Test Scenarios
**_1️⃣ Create a New Booking_**
- Method: POST
- Request URL : **[https://restful-booker.herokuapp.com/booking/](https://restful-booker.herokuapp.com/booking/)**
- Pre-request Script: Generates random booking details :
  ```
  
          // Set First Name in the Environment
          let firstName = pm.variables.replaceIn("{{$randomFirstName}}");
          console.log(firstName);
          pm.environment.set("firstname",firstName);

          // Set Last Name in the Environment 
          let lastName = pm.variables.replaceIn("{{$randomLastName}}");
          console.log(lastName);
          pm.environment.set("lastname",lastName);

          // Set Total Price in the Environment
          let totalPrice = pm.variables.replaceIn("{{$randomInt}}");
          console.log(totalPrice);
          pm.environment.set("totalprice",totalPrice);

          // Set Deposit Paid in the Environment
          let depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
          pm.environment.set("depositpaid",depositpaid)

          // Set Booking Dates in the Environment
          const moment = require('moment');
          const today = moment();
          // Checkin
          let checkin = today.subtract(3,'Y').format("YYYY-DD-MM");
          pm.environment.set("checkin",checkin);
          // Checkout
          let checkout = today.add(1,'M').format("YYYY-DD-MM");
          pm.environment.set("checkout",checkout);

          // Set Additional Needs in the Environment
          let additionalneeds = pm.variables.replaceIn("{{$randomCompanyName}}");
          pm.environment.set("additionalneeds",additionalneeds)
          console.log(additionalneeds);
  ```
- Request Body:
  ```
         {
            "firstname" : "{{firstname}}",
            "lastname" : "{{lastname}}",
            "totalprice" : {{totalprice}},
            "depositpaid" : {{depositpaid}},
            "bookingdates" : {
            "checkin" : "{{checkin}}",
            "checkout" : "{{checkout}}"
              },
           "additionalneeds" : "{{additionalneeds}}"
               }
- Response Body :
  ```
              {
            "bookingid": 2749,
            "booking": {
            "firstname": "Evangeline",
            "lastname": "Effertz",
            "totalprice": 96,
            "depositpaid": true,
            "bookingdates": {
            "checkin": "2025-05-14",
            "checkout": "2025-05-16"
             },
           "additionalneeds": "Schiller and Sons"
             }
 
  ```
  
**_2️⃣ Get Booking Details by ID_**

- Method: GET
- Requst URL : **[https://restful-booker.herokuapp.com/booking/:bookingid](https://restful-booker.herokuapp.com/booking/:bookingid)**
- Request Body : None
- Response Body :
  ```
          {
             "firstname": "Alene",
             "lastname": "Reynolds",
             "totalprice": 745,
             "depositpaid": true,
             "bookingdates": {
             "checkin": "2025-05-14",
             "checkout": "2025-05-16"
                    },
            "additionalneeds": "Toy Inc"
     }
  ```

**_3️⃣ Create Token for Authentication_**
- Method: POST
- URL: **[https://restful-booker.herokuapp.com/booking/auth](https://restful-booker.herokuapp.com/auth)**
- Request Body:
```
           {
          "username" : "admin",
          "password" : "password123"
           }
```
Response Body :
```
          {
         "token": "dad87424e777fef"
          }
```
**_4️⃣ Update Booking Details_**
- Method: POST
- Request URL : **[https://restful-booker.herokuapp.com/booking/:bookingid](https://restful-booker.herokuapp.com/booking/:bookingid)**
- Pre-request Script: Generates updated details: 
  ```
  
          // Set First Name in the Environment
          let firstName = pm.variables.replaceIn("{{$randomFirstName}}");
          console.log(firstName);
          pm.environment.set("firstname",firstName);

          // Set Last Name in the Environment 
          let lastName = pm.variables.replaceIn("{{$randomLastName}}");
          console.log(lastName);
          pm.environment.set("lastname",lastName);

          // Set Total Price in the Environment
          let totalPrice = pm.variables.replaceIn("{{$randomInt}}");
          console.log(totalPrice);
          pm.environment.set("totalprice",totalPrice);

          // Set Deposit Paid in the Environment
          let depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
          pm.environment.set("depositpaid",depositpaid)

          // Set Booking Dates in the Environment
          const moment = require('moment');
          const today = moment();
          // Checkin
          let checkin = today.subtract(3,'Y').format("YYYY-DD-MM");
          pm.environment.set("checkin",checkin);
          // Checkout
          let checkout = today.add(1,'M').format("YYYY-DD-MM");
          pm.environment.set("checkout",checkout);

          // Set Additional Needs in the Environment
          let additionalneeds = pm.variables.replaceIn("{{$randomCompanyName}}");
          pm.environment.set("additionalneeds",additionalneeds)
          console.log(additionalneeds);
  ```
- Request Body:
  ```
         {
            "firstname" : "{{firstname}}",
            "lastname" : "{{lastname}}",
            "totalprice" : {{totalprice}},
            "depositpaid" : {{depositpaid}},
            "bookingdates" : {
            "checkin" : "{{checkin}}",
            "checkout" : "{{checkout}}"
              },
           "additionalneeds" : "{{additionalneeds}}"
        }
- Response Body :
  ```
      {
          "firstname": "Jed",
          "lastname": "O'Hara",
          "totalprice": 571,
          "depositpaid": true,
          "bookingdates": {
         "checkin": "2025-08-18",
         "checkout": "2025-08-28"
            },
         "additionalneeds": "241-666-8263"
     }
  ```
**_4️⃣ Delete Booking Report_**
- Method: DELETE
- Request URL : **[https://restful-booker.herokuapp.com/booking/:bookingid](https://restful-booker.herokuapp.com/booking/:bookingid)**
- Response Body : None
