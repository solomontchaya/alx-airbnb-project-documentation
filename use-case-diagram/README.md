# 1. Design the Use Case Diagram of the Features and Functionalities

## 📌 Objective
The purpose of this task is to visualize how different actors interact with the Airbnb Clone backend system.  
The **use case diagram** provides a high-level view of the system's features, functionalities, and user interactions.

---

## 👥 Actors
- **Guest User**  
  Can browse properties, register, log in, and make bookings.  

- **Registered User (Host/Traveler)**  
  - **Traveler**: Can search properties, make bookings, and process payments.  
  - **Host**: Can list, update, and manage properties.  

- **Admin**  
  Manages users, properties, bookings, and payments across the platform.  

- **Payment Gateway**  
  External service that handles secure payment transactions.

---

## 🎯 Key Use Cases
The following use cases are captured in the diagram:

### 1. User Authentication
- Register a new account  
- Log in / Log out  
- Manage profile  

### 2. Property Management
- Host lists a property  
- Update or remove a property  
- View property details  

### 3. Booking Management
- Search for available properties  
- Book a property  
- Cancel a booking  
- View booking history  

### 4. Payments
- Traveler makes a payment  
- Payment Gateway processes payment  
- Admin verifies and tracks payments  

### 5. Admin Operations
- Manage users (activate, deactivate, suspend)  
- Manage property listings  
- Monitor bookings and transactions  

---

## 🔗 Relationships
- **Guest Users** can only register and browse listings.  
- **Registered Users** can act as Hosts or Travelers depending on their role.  
- **Hosts** interact with property management features.  
- **Guests** interact with booking and payment features.  
- **Admins** have oversight of all system operations.  
- **Payment Gateway** is an external actor that processes financial transactions.  

---

