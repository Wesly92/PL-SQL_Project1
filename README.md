# Hotel Management System Database

## Overview
This project represents the database schema for a comprehensive **Hotel Management System**. It is designed to manage customer bookings, reservations, room assignments, payments, services, and customer satisfaction data. The system uses **SQL** to create tables and establish relationships between key entities like **customers, bookings, reservations, invoices, rooms**, and **services**. Below is a detailed explanation of each table, its structure, and how it fits into the overall system.

## Database Schema

### 1. Customer
The `Customer` table stores information about the guests who book hotel services. It holds personal information like the first and last name, gender, and phone number.
- **Columns**: `customer_id` (Primary Key), `first_name`, `last_name`, `Gender`, `phone_number`
- **Primary Key**: `customer_id`

### 2. Booking
The `Booking` table records the booking details for customers. Each booking is linked to a customer, establishing a relationship between the two tables.
- **Columns**: `Booking_id` (Primary Key), `Book_type`, `Book_date`, `Customer_id` (Foreign Key)
- **Primary Key**: `Booking_id`
- **Foreign Key**: `Customer_id` references `Customer(customer_id)`

### 3. Reservation
The `Reservation` table records the details of a customer's stay at the hotel, including the check-in and check-out dates, the number of days, and links to both the customer and their booking.
- **Columns**: `Res_id` (Primary Key), `check_in_date`, `check_out_date`, `No_of_days`, `Customer_id` (Foreign Key), `Booking_id` (Foreign Key)
- **Primary Key**: `Res_id`
- **Foreign Keys**: 
  - `Customer_id` references `Customer(customer_id)`
  - `Booking_id` references `Booking(Booking_id)`

### 4. Room
The `Room` table records information about the rooms assigned to guests during their stay, including the room type, bed type, price, and links to reservations and customers.
- **Columns**: `Room_no` (Primary Key), `Room_type`, `Bed_type`, `No_of_occupants`, `Room_price`, `Customer_id` (Foreign Key), `res_id` (Foreign Key)
- **Primary Key**: `Room_no`
- **Foreign Keys**: 
  - `Customer_id` references `Customer(customer_id)`
  - `res_id` references `Reservation(Res_id)`

### 5. Address
The `Address` table stores the address details for customers, including street, city, state, country, and zip code. Each customer has a corresponding address.
- **Columns**: `Street`, `City`, `State`, `Country`, `Customer_id` (Foreign Key), `Zip_code`
- **Foreign Key**: `Customer_id` references `Customer(customer_id)`

### 6. Invoice
The `Invoice` table records the invoices generated for customer reservations. Each invoice is linked to a reservation and a customer.
- **Columns**: `Invoice_No` (Primary Key), `Res_id` (Foreign Key), `customer_id` (Foreign Key)
- **Primary Key**: `Invoice_No`
- **Foreign Keys**:
  - `Res_id` references `Reservation(Res_id)`
  - `customer_id` references `Customer(customer_id)`

### 7. Line
The `Line` table links services to an invoice. It records the quantity of services availed during a reservation.
- **Columns**: `Invoice_No` (Foreign Key), `Service_id` (Foreign Key), `Service_quantity`, `res_id` (Foreign Key)
- **Foreign Keys**: 
  - `Service_id` references `Services(Service_id)`
  - `Invoice_No` references `Invoice(Invoice_No)`
  - `res_id` references `Reservation(Res_id)`

### 8. Services
The `Services` table defines the different services available at the hotel, such as spa, laundry, and meals.
- **Columns**: `Service_id` (Primary Key), `Service_type`, `Service_cost`
- **Primary Key**: `Service_id`

### 9. Transactions
The `Transactions` table tracks customer payments. It stores details about the payment method, payment date, and links to the invoice and customer.
- **Columns**: `Trans_No` (Primary Key), `Payment_Method`, `Payment_Date`, `Invoice_no` (Foreign Key), `Customer_id` (Foreign Key)
- **Primary Key**: `Trans_No`
- **Foreign Keys**: 
  - `Invoice_no` references `Invoice(Invoice_No)`
  - `Customer_id` references `Customer(customer_id)`

### 10. Satisfaction
The `Satisfaction` table stores customer satisfaction ratings for their stay, linked to a specific transaction.
- **Columns**: `Satisfaction_ID` (Primary Key), `Satisfaction_level`, `Trans_no` (Foreign Key)
- **Primary Key**: `Satisfaction_ID`
- **Foreign Key**: `Trans_no` references `Transactions(Trans_No)`

## Features
- **Complete Customer Lifecycle**: Tracks customer information from booking to reservation, room allocation, invoicing, and transaction.
- **Service Management**: Allows the hotel to assign services to customers and record them in the invoice.
- **Satisfaction Tracking**: Captures customer feedback through a satisfaction level rating system linked to their transactions.
- **Room and Reservation Linkage**: Rooms are tied to specific reservations and customers, facilitating easy tracking of room occupancy and billing.

## Installation
1. Clone the repository.
2. Execute the provided SQL scripts to set up the database structure.
3. Populate the tables with the provided INSERT statements.
4. Use SQL queries to interact with the data, such as retrieving customer details, booking information, reservation history, and more.

## Usage
This schema is designed to serve as the backbone of a fully functional hotel management system. You can extend it with additional features such as:
- **Customer Loyalty Programs**
- **Dynamic Pricing Models**
- **Enhanced Reporting and Analytics**

The system is built to be flexible and adaptable to different hotel sizes and operational models.

## Contact
If you have any questions or need further information, feel free to contact the project maintainers.
