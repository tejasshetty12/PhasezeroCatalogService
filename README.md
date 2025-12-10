 PhaseZero – Product Catalog Service

A simple backend microservice built using Java 17 and Spring Boot to manage product catalogue data using REST APIs.

---

 1. How to Run the Application

 Requirements
- Java 17
- Maven
- STS / IntelliJ / Eclipse

  Steps
1. Clone or download this project.
2. Open the project in your IDE.
3. Run the main class:
4. Application will start at: http://localhost:8080

2. Project Structure (3 Layers)
src/main/java
└── com.org.phasezero_catalog_service
├── Controller → Handles REST APIs
├── Service → Business logic
├── Repository → In-memory storage (HashMap)
├── model → Product model
├── exception → Error handling


 3. Data Model

| Field       | Type    | Description |
|-------------|---------|-------------|
| partNumber  | String  | Unique identifier (business key) |
| partName    | String  | Product name (stored in lowercase) |
| category    | String  | Product category |
| price       | double  | Must be non-negative |
| stock       | int     | Must be non-negative |



4. Endpoints (REST APIs)

   1️ Add New Product
    Request Body:
    json
{
  "partNumber": "P001",
  "partName": "Air Filter",
  "category": "Engine",
  "price": 500,
  "stock": 5
}

  2️ List All Products
     GET /products
     
  3️ Search Products by Name
    GET /products/search?name=filter
    
  4️ Filter by Category
    GET /products/filter?category=Engine
    
  5️ Sort Products by Price (Ascending)
    GET /products/sort/price
    
  6️ Total Inventory Value
    GET /products/inventory/value
    
    
5. Validations (Mandatory)

❌ Duplicate partNumber → returns error
❌ price or stock negative → returns error
❌ Missing fields → returns error

Error response example:
{
  "message": "price cannot be negative",
  "code": 400
}

6. Example Responses
Successful Add
{"message": "Product added successfully"}

Error Example
{"message": "partNumber already exists"}


    
    
    
    
   
    




