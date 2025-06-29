# Airbnb Clone: Backend Features and Functionalities

This document outlines the main backend features and functionalities required for the Airbnb Clone project. These have been grouped into core modules for clarity.

## 1. User Management

**Key Functionalities:**
- User Registration (Guests and Hosts)
- Secure Authentication using JWT
- OAuth Support (Google, Facebook)
- Role-Based Access Control (guest, host, admin)
- User Profile Management (edit profile, upload photo)

## 2. Property Management

**Key Functionalities:**
- Hosts can create, update, and delete property listings
- Properties contain attributes like name, description, location, price, amenities, availability
- Upload and manage property images

## 3. Search and Filtering

**Key Functionalities:**
- Search properties by:
  - Location
  - Price range
  - Number of guests
  - Amenities
- Pagination and sorting support

## 4. Booking System

**Key Functionalities:**
- Guests can book a property for a specified date range
- Validate dates to avoid double bookings
- Track booking statuses: `pending`, `confirmed`, `cancelled`, `completed`
- Allow booking cancellations under policy rules

## 5. Payment Processing

**Key Functionalities:**
- Integration with Stripe, PayPal
- Guests pay upfront
- Payouts triggered to hosts after completed bookings
- Handle multiple currencies

## 6. Reviews and Ratings

**Key Functionalities:**
- Guests leave reviews and rate properties (1–5 stars)
- Hosts may respond to reviews
- Prevent review spamming (1 review per completed booking)

## 7. Messaging System

**Key Functionalities:**
- Direct messaging between hosts and guests
- Store conversation history
- Notifications on new messages

## 8. Notifications System

**Key Functionalities:**
- In-app and email notifications for:
  - Booking status updates
  - Payment confirmations
  - New messages
- Use services like SendGrid or Mailgun

## 9. Admin Dashboard

**Key Functionalities:**
- Admins can manage:
  - Users
  - Listings
  - Bookings
  - Payments
  - System reports
- View platform metrics and user activity

## 10. Technical Features

- RESTful API Design
- Optional GraphQL support for flexible data fetching
- PostgreSQL as primary database
- File storage for media (images)
- Global error handling
- JWT + Role-based authentication
