I created an ERD that models the relationships between different entities in the shoe
store.
# Nike Store ERD

```mermaid
erDiagram
    PRODUCT {
        string product_id PK "Unique identifier for each product"
        string model_name "Model name of the Nike shoe"
        string size "Size of the shoe"
        decimal price "Price of the shoe"
        int stock_quantity "Available stock quantity"
    }
    
    CUSTOMER {
        string customer_id PK "Unique identifier for each customer"
        string first_name "First name of the customer"
        string last_name "Last name of the customer"
        string email "Email address of the customer"
        string phone "Contact number of the customer"
    }
    
    SALE {
        string sale_id PK "Unique identifier for each sale"
        string product_id FK "Identifier for the sold product"
        string customer_id FK "Identifier for the customer"
        date sale_date "Date of the transaction"
        decimal sale_amount "Total amount of the sale"
    }

    INVENTORY {
        string inventory_id PK "Unique identifier for inventory record"
        string product_id FK "Identifier for the product"
        int quantity "Quantity available in inventory"
        date last_updated "Date when inventory was last updated"
    }

    PRODUCT ||--o{ SALE : "sold in"
    CUSTOMER ||--o{ SALE : "makes"
    PRODUCT ||--o{ INVENTORY : "tracked in"
