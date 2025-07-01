# Use Case Diagram: Airbnb Clone Backend

This diagram outlines the interactions between various user roles and the system's core functionalities. The goal is to visualize who (actors) can perform what (use cases) in the system.

## Actors
- **Guest**
- **Host**
- **Admin**
- **Payment Gateway (External System)**

## Use Cases

### For Guest:
- Register an account
- Login
- View properties
- Search/filter properties
- Book property
- Cancel booking
- Make payment
- View booking history
- Leave review
- Send/receive messages
- Receive notifications

### For Host:
- Register an account
- Login
- Create property listing
- Edit/delete listing
- View booking requests
- Accept/reject booking
- Receive payments
- Respond to reviews
- Send/receive messages
- Receive notifications

### For Admin:
- Login
- Manage users (ban, verify)
- Manage listings
- Manage bookings
- Manage reviews
- View reports/metrics

### For Payment Gateway:
- Process guest payments
- Trigger host payouts