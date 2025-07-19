# Airbnb Clone Backend — Requirements Specifications

🎯 **Objective**

This document specifies the technical and functional requirements for three key backend features of the Airbnb Clone system:  
- User Authentication  
- Property Management  
- Booking System

It defines API endpoints, input/output formats, validation rules, and performance criteria to guide implementation and testing.

---

## 🔐 1️⃣ User Authentication

### Overview
Handles user registration, login, authentication, and profile management securely.

### API Endpoints

| Method | Endpoint               | Description                     |
|-------:|------------------------|---------------------------------|
| POST   | `/api/v1/auth/register` | Register a new user account.   |
| POST   | `/api/v1/auth/login`    | Authenticate user credentials. |
| GET    | `/api/v1/users/me`      | Retrieve current user profile. |
| PUT    | `/api/v1/users/me`      | Update current user profile.   |

### Input/Output

#### POST `/api/v1/auth/register`
**Input (JSON):**
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john.doe@example.com",
  "password": "securePassword123",
  "role": "guest"
}

## 🏠 2️⃣ Property Management

### Overview
Allows hosts to create, update, delete, and view property listings.

### API Endpoints

| Method | Endpoint                     | Description                      |
|--------|------------------------------|----------------------------------|
| POST   | `/api/v1/properties`        | Create a new property listing.  |
| GET    | `/api/v1/properties/{id}`   | Get details of a property.      |
| PUT    | `/api/v1/properties/{id}`   | Update property details.        |
| DELETE | `/api/v1/properties/{id}`   | Delete a property.              |
| GET    | `/api/v1/properties`        | List/search properties.         |

---

### Input/Output

#### POST `/api/v1/properties`

**Input (JSON):**
```json
{
  "name": "Cozy Apartment",
  "description": "A cozy 2-bedroom apartment near the beach.",
  "location": "Cape Town, South Africa",
  "price_per_night": 150.00,
  "amenities": ["Wi-Fi", "Kitchen", "Parking"],
  "availability": true
}

{
  "message": "Property created successfully",
  "property_id": "uuid"
}


Validation Rules
Name, description, and location cannot be empty.

Price must be a positive decimal number.

Only authenticated host users may create, update, or delete properties.

Performance Criteria
Property search queries must return results in under 1 second with pagination.

The system must efficiently support at least 10,000 concurrent listings.