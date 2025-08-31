# Backend Feature Requirement Specifications

## 📌 Objective
Document the **technical and functional requirements** for key backend features of the Airbnb Clone.  
This includes **API endpoints**, **input/output specifications**, **validation rules**, and **performance criteria**.

---

## 1. User Authentication

### Description
Handles user registration, login, password management, and role-based access control.

### API Endpoints
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth/register` | POST | Register a new user (Guest or Host) |
| `/api/auth/login` | POST | Login and receive JWT |
| `/api/auth/logout` | POST | Logout user (invalidate token) |
| `/api/auth/password-reset` | POST | Request password reset |
| `/api/auth/password-update` | POST | Update password using reset token |

### Input / Output Specifications
**Register**
```json
{
  "input": {
    "name": "John Doe",
    "email": "john@example.com",
    "password": "securePass123",
    "role": "guest"
  },
  "output": {
    "message": "Registration successful",
    "user_id": 123,
    "verification_sent": true
  }
}
```
**Login**
```json
{
  "input": {
    "email": "john@example.com",
    "password": "securePass123"
  },
  "output": {
    "token": "JWT_TOKEN_HERE",
    "expires_in": 3600,
    "user": {
      "id": 123,
      "name": "John Doe",
      "role": "guest"
    }
  }
}
```
Validation Rules
Email must be valid and unique.

Password: minimum 8 characters, must include letters and numbers.

Role must be either guest or host.

Performance Criteria
Registration and login responses within 500ms.

JWT token expiration configurable (default 1 hour).

Support at least 1000 concurrent logins.

## 2. Property Management
Description
Allows hosts to create, update, delete, and manage property listings.

API Endpoints
Endpoint	Method	Description
/api/properties	POST	Create new property listing
/api/properties/{id}	PUT	Update property details
/api/properties/{id}	DELETE	Delete property
/api/properties	GET	List/search properties
/api/properties/{id}	GET	Get property details

Input / Output Specifications
Create Property
```json
{
  "input": {
    "title": "Cozy Apartment",
    "description": "2 bedroom apartment downtown",
    "location": "Lilongwe, Malawi",
    "price": 50.00,
    "amenities": ["WiFi", "Pool"],
    "availability": ["2025-09-01", "2025-09-30"]
  },
  "output": {
    "message": "Property created successfully",
    "property_id": 456
  }
}
```
Validation Rules
Price must be positive decimal.

Title and description required, min 5 characters.

Availability dates must be valid and in the future.

Amenities must be from allowed list.

Performance Criteria
Search queries return within 1 second for up to 10,000 properties.

Support 500 concurrent property creation requests.

3. Booking System
Description
Manages creation, cancellation, and tracking of bookings between guests and hosts.

API Endpoints
Endpoint	Method	Description
/api/bookings	POST	Create a new booking
/api/bookings/{id}	GET	Retrieve booking details
/api/bookings/{id}/cancel	POST	Cancel a booking
/api/bookings/user/{user_id}	GET	List bookings for a user

Input / Output Specifications
Create Booking
```json
{
  "input": {
    "property_id": 456,
    "guest_id": 123,
    "start_date": "2025-09-10",
    "end_date": "2025-09-15",
    "guests_count": 2
  },
  "output": {
    "message": "Booking confirmed",
    "booking_id": 789,
    "status": "confirmed"
  }
}
```
Validation Rules
Dates must be valid and not overlap existing bookings.

Guests count must not exceed property capacity.

Guest must be a registered user.

Performance Criteria
Booking creation must complete within 500ms.

System supports 1000 concurrent bookings without data conflicts.

**Notes**
All APIs must use HTTPS.

JWT token required for authenticated endpoints.

All responses follow a standard JSON structure with message, data, and status fields.
