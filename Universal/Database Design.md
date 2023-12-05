# Database Design

Database will be creating using SQLite. Primary Keys will be denoted by names beginning with 'pk',
 and Foreign Keys will begin with 'fk', followed by column they reference, and a descriptive name if
necessary.

---

### User Table

#### Columns

pkId: Integer

username: Text

password: Text (salted and hashed)

user_type: Text (Enum constraint to "Guest", "Customer", "Employee", and "Manager")

is_active: Integer (0 or 1, SQLite doesn't support Boolean type)

---

### Products Table

#### Columns

pkId: Integer

display_name: Text

stock: Integer

price_per_unit: Integer

productType: Text (Enum constraint to "IceCream", "Cone", and "Topping")

---

### Drones Table

#### Columns

pkId: Integer

display_name: Text

serial_number: Text

is_active: Integer (0, 1)

size: Integer (Constained to 1, 2, 3)

fkowner_id: Integer

---

### Orders Table

#### Columns

pkId: Integer

total_price: Real

employee_cut: Real

profit: Real

order_time: Text

fkUserId: Integer

---

### Ordered Cones Table

#### Columns

pkOrderedConeId: Integer

fkProductIdCone: Integer 

fkProductIdScoop1: Integer

fkProductIdScoop2: Integer / NULL (SQLite allows null foreign key values, but maybe we should use json instead of potentially empty fields?)

fkProductIdScoop3: Integer / NULL

fkProductIdTopping1: Integer / NULL

fkProductIdTopping2: Integer / NULL

fkProductIdTopping3: Integer / NULL

fkOrderId: Integer

---

### Restock Table

#### Columns

pkId: Integer

restock_time: Text

cost: Real

