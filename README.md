## Entity-Relationship Diagram (ERD)
# User
# Attributes:
- UserID (PK)
- Username
- Password
- Email
# TwoFactorAuthentication
# Relationships:
- Addresses (One-to-Many)
- ShoppingCart (One-to-One)
- Orders (One-to-Many)
- ProductReviews (One-to-Many)
- LoyaltyProgram (One-to-One)
# Address
# Attributes:
- AddressID (PK)
- Street
- City
- State
- ZipCode
# Relationships:
- Users (Many-to-One)
# Product
# Attributes:
- ProductID (PK)
- Name
- Description
- Price
- StockQuantity
# Relationships:
- ShoppingCartItems (One-to-Many)
- OrderItems (One-to-Many)
- ProductReviews (One-to-Many)
# ShoppingCart
# Attributes:
- CartID (PK)
- Status
# Relationships:
- User (One-to-One)
- CartItems (One-to-Many)
- CartItem
# Attributes:
- CartItemID (PK)
- Quantity
# Relationships:
- ShoppingCart (Many-to-One)
- Product (Many-to-One)
# Order
# Attributes:
- OrderID (PK)
- OrderDate
# Status
# Relationships:
- User (Many-to-One)
- Address (Many-to-One)
- OrderItems (One-to-Many)
# OrderItem
# Attributes:
- OrderItemID (PK)
- Quantity
- UnitPrice
# Relationships:
- Order (Many-to-One)
- Product (Many-to-One)
# ProductReview
# Attributes:
- ReviewID (PK)
- Rating
- Comment
- ReviewDate
# Relationships:
- User (Many-to-One)
- Product (Many-to-One)
# Admin
# Attributes:
- AdminID (PK)
- Username
- Password
# LoyaltyProgram
# Attributes:
- LoyaltyProgramID (PK)
- Points
# Relationships:
- User (One-to-One)
# AnalyticsData
# Attributes:
- AnalyticsID (PK)
- DataType
- DataValue
-Timestamp
# Relationships:
- Admin (Many-to-One)
  
| **User**           | **Address**        | **Product**         |
|---------------------|--------------------|---------------------|
| UserID (PK)         | AddressID (PK)     | ProductID (PK)     |
| Username            | UserID (FK) -----> | Name                |
| Password            | Street             | Description         |
| Email               | City               | Price               |
| TwoFactorAuth...    | State              | StockQuantity       |

| **ShoppingCart**    | **CartItem**       | **Order**           |
|---------------------|--------------------|---------------------|
| CartID (PK)         | CartItemID (PK)    | OrderID (PK)        |
| UserID (FK) ----->  | CartID (FK) -----> | UserID (FK)         |
| Status              | ProductID (FK)     | AddressID (FK)      |
|                     | Quantity           | OrderDate           |
|                     |                    | Status              |

| **OrderItem**       | **ProductReview**  | **Admin**           |
|---------------------|--------------------|---------------------|
| OrderItemID (PK)    | ReviewID (PK)      | AdminID (PK)        |
| OrderID (FK) -----> | ProductID (FK)     | Username            |
| ProductID (FK)      | UserID (FK) -----> | Password            |
| Quantity            | Rating             |                     |
| UnitPrice           | Comment            |                     |
|                     | ReviewDate         |                     |

| **LoyaltyProgram**  | **AnalyticsData**  |
|---------------------|---------------------|
| LoyaltyProgramID    | AnalyticsID (PK)   |
| UserID (FK) ----->  | AdminID (FK)       |
| Points              | DataType            |
|                     | DataValue           |
|                     | Timestamp           |
