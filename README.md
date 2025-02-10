# Basic Postman Collection  

## Overview  
This repository contains a Postman collection that demonstrates a basic workflow for managing bookings using RESTful APIs. The workflow includes creating, retrieving, updating, and verifying booking records. Authentication is required for updates, which is handled using a token-based authentication mechanism.  

## API Workflow  

### 1. Create Booking (`POST /booking/`)  
Creates a new booking with user details, price, deposit status, dates, and additional needs.  

**Request URL:**  
```
https://restful-booker.herokuapp.com/booking/
```

**Request Headers:**  
- `Content-Type: application/json`  

**Request Body:**  
```json
{
  "firstname": "Mehedi",
  "lastname": "Hasan",
  "totalprice": 111,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2025-01-01",
    "checkout": "2025-02-01"
  },
  "additionalneeds": "Breakfast"
}
```

**Response Example:**  
```json
{
  "bookingid": 352,
  "booking": {
    "firstname": "Mehedi",
    "lastname": "Hasan",
    "totalprice": 111,
    "depositpaid": true,
    "bookingdates": {
      "checkin": "2025-01-01",
      "checkout": "2025-02-01"
    },
    "additionalneeds": "Breakfast"
  }
}
```

---

### 2. Get Booking (`GET /booking/{id}`)  
Fetches the details of an existing booking using its ID.  

**Request URL:**  
```
https://restful-booker.herokuapp.com/booking/352
```

**Response Example:**  
```json
{
  "firstname": "Mehedi",
  "lastname": "Hasan",
  "totalprice": 111,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2025-01-01",
    "checkout": "2025-02-01"
  },
  "additionalneeds": "Breakfast"
}
```

---

### 3. Create Authentication Token (`POST /auth`)  
Generates a token for authentication, which is required for updating a booking.  

**Request URL:**  
```
https://restful-booker.herokuapp.com/auth
```

**Request Headers:**  
- `Content-Type: application/json`  

**Request Body:**  
```json
{
  "username": "admin",
  "password": "password123"
}
```

**Response Example:**  
```json
{
  "token": "277db7451732ccd"
}
```

---

### 4. Update Booking (`PUT /booking/{id}`)  
Updates an existing booking using the authentication token.  

**Request URL:**  
```
https://restful-booker.herokuapp.com/booking/352
```

**Request Headers:**  
- `Content-Type: application/json`  
- `Cookie: token=277db7451732ccd`  

**Request Body:**  
```json
{
  "firstname": "Soumik",
  "lastname": "Hasan",
  "totalprice": 111,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2025-02-01",
    "checkout": "2025-04-01"
  },
  "additionalneeds": "Breakfast"
}
```

**Response Example:**  
```json
{
  "firstname": "Soumik",
  "lastname": "Hasan",
  "totalprice": 111,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2025-02-01",
    "checkout": "2025-04-01"
  },
  "additionalneeds": "Breakfast"
}
```

---

### 5. Check Update (`GET /booking/{id}`)  
Fetches the updated booking details to verify the changes.  

**Request URL:**  
```
https://restful-booker.herokuapp.com/booking/352
```

**Response Example:**  
```json
{
  "firstname": "Soumik",
  "lastname": "Hasan",
  "totalprice": 111,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2025-02-01",
    "checkout": "2025-04-01"
  },
  "additionalneeds": "Breakfast"
}
```

---

## Installation and Usage  

### Prerequisites  
- **Postman** installed  
- **Active Internet Connection** (APIs are hosted on `restful-booker.herokuapp.com`)  

### Steps to Run  
1. **Import the Collection**  
   - Open Postman  
   - Click **Import** and select the `Basic.postman_collection.json` file  

2. **Run API Requests in Sequence:**  
   - **Create Booking** (`POST /booking/`)  
   - **Get Booking** (`GET /booking/{id}`)  
   - **Create Token** (`POST /auth`)  
   - **Update Booking** (`PUT /booking/{id}`)  
   - **Check Update** (`GET /booking/{id}`)  

3. **Authentication for Updates:**  
   - Obtain a token from `POST /auth`  
   - Include the token in the request headers under `Cookie`  

---

## Notes  
- This project is a basic demonstration and should not be used in production without proper security considerations.  
- Ensure the booking ID used for updates exists.  
- The token is required for update operations and should be included in the `Cookie` header.  

---

## Author  
**Mehedi Hasan Soumik**  



