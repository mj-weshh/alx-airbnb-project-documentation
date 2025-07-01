# Backend Feature Requirement Specifications

This document outlines the functional and technical specifications for core backend features in the ALX Airbnb Clone project. It includes detailed API endpoint definitions, input/output formats, validation rules, and performance expectations.

## 1. User Authentication

### Objective
Enable secure registration and login for users (guests, hosts, and admins).

### API Endpoints

#### POST `/api/v1/auth/register`
- **Input:**
  - `first_name` (string, required)
  - `last_name` (string, required)
  - `email` (string, required, valid email)
  - `password` (string, required, min. 8 characters)
  - `role` (enum: guest, host, admin)
- **Output:**
  - 201 Created with user data (excluding password)
  - JWT token for session management
- **Validation:**
  - Email must be unique
  - Password must be hashed before storage

#### POST `/api/v1/auth/login`
- **Input:**
  - `email` (string, required)
  - `password` (string, required)
- **Output:**
  - 200 OK with JWT token and user info
  - 401 Unauthorized for invalid credentials
- **Validation:**
  - Verify email exists and password matches hashed password

### Performance Criteria
- Response time: ≤ 300ms for authentication
- Secure token generation and storage using JWT

## 2. Property Management

### Objective
Allow hosts to create, update, and delete property listings.

### API Endpoints

#### POST `/api/v1/properties`
- **Input:**
  - `host_id` (UUID, required)
  - `name` (string, required)
  - `description` (text, required)
  - `location` (string, required)
  - `pricepernight` (decimal, required)
- **Output:**
  - 201 Created with property details
- **Validation:**
  - All fields required except for optional amenities
  - `host_id` must reference a valid user with role = 'host'

#### PUT `/api/v1/properties/:id`
- **Input:**
  - Any updatable field (e.g., name, description, price)
- **Output:**
  - 200 OK with updated property info
  - 404 Not Found if property doesn't exist
- **Validation:**
  - Only the host who owns the listing can update

#### DELETE `/api/v1/properties/:id`
- **Output:**
  - 204 No Content on successful deletion
  - 403 Forbidden if user is not the host

### Performance Criteria
- Database must be indexed by `location`, `host_id`
- Listing creation under 400ms

## 3. Booking System

### Objective
Allow guests to book properties and view/manage their bookings.

### API Endpoints

#### POST `/api/v1/bookings`
- **Input:**
  - `property_id` (UUID, required)
  - `user_id` (UUID, required)
  - `start_date` (date, required)
  - `end_date` (date, required)
- **Output:**
  - 201 Created with booking details
- **Validation:**
  - No overlapping bookings
  - Dates must be in the future and valid
  - `property_id` and `user_id` must exist

#### GET `/api/v1/bookings/user/:user_id`
- **Output:**
  - 200 OK with list of bookings for the user

#### DELETE `/api/v1/bookings/:id`
- **Output:**
  - 200 OK on successful cancellation
  - 403 if user is not the owner of the booking

### Performance Criteria
- Booking creation response time ≤ 400ms
- Caching enabled for frequent queries (e.g., property availability)

## Notes
- All endpoints will be secured using JWT-based authentication.
- Role-based access control (RBAC) is enforced on all endpoints.