Task 3
*************************************************************************
👓 Exercise 1: Client‑Centric Data Model

From the perspective of a client interacting with the system, the database must store:

Suppliers

supplier_id

name

address

street

number

floor

door

city

postal_code

country

phone

fax

tax_id (NIF)

Business rule:A glasses brand is supplied by one single supplier, but a supplier may provide multiple brands.

Glasses

glasses_id

brand

left_lens_graduation

right_lens_graduation

frame_type (floating, plastic, metallic)

frame_color

left_lens_color

right_lens_color

price

supplier_id (reference → Supplier)

Clients

client_id

name

address

phone

email

registration_date

recommended_by (self‑reference, optional)

Employees

employee_id

name

surname

phone

role

Sales

Each sale links a client, an employee, and a pair of glasses.

sale_id

sale_datetime

client_id (reference → Client)

employee_id (reference → Employee)

glasses_id (reference → Glasses)

👉 With this design, the system can answer:

Which employee sold glasses to a specific client

Which supplier provides the glasses purchased

Who referred the client to the store

🕶️ Exercise 2: Product‑Centric Data Model

From the perspective of the glasses (product‑centric view), the system must represent:

Glasses (central entity)

glasses_id

brand

graduation_left

graduation_right

frame_type

frame_color

lens_color_left

lens_color_right

price

supplier_id (reference → Supplier)

Supplier

Provides the glasses brand

One supplier can provide multiple brands

Each brand belongs to a single supplier

Sale

Connects glasses to the client who bought them

Identifies the employee who handled the sale

Stores the sale date/time

Client

Linked to glasses through sales

May include referral relationships

Employee

Linked to glasses through sales

Identifies who sold each product

👉 With this design, the system can answer:

Which supplier provides a specific pair of glasses

Which client purchased them

Which employee sold them

When the sale occurred

🛠 Technologies Used

MongoDB (document‑oriented modeling)

MongoDB Compass / mongosh

JSON‑based schema design

Conceptual diagrams for justification

Git & GitHub for version control

Markdown documentation

📋 Requirements

MongoDB installed

MongoDB Compass or terminal client

Git installed

Basic understanding of NoSQL modeling principles

🚀 Installation and Execution

Create the database in MongoDB

Define the collections:

clients

suppliers

glasses

employees

sales

Insert sample documents

Run validation queries

Use Compass to visualize embedded structures and references

🧩 Diagrams and Technical Justification

The conceptual diagrams illustrate:

Entities and their attributes

1:N and N:M relationships

When embedding is preferred (e.g., purchase history inside a client document)

When referencing is required (e.g., supplier → glasses)

How the model avoids redundancy while keeping queries efficient

Justification includes:

Why certain collections exist

Why some relationships are embedded and others referenced

How the model supports both client‑centric and product‑centric queries

How document structure improves read performance for common operations
