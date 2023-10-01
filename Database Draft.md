# Database Design

Database will be creating using SQLite. Primary Keys will be denoted by names beginning with 'pk',
 and Foreign Keys will begin with 'fk', followed by column they reference, and a descriptive name if
necessary.

---

### Customer Table

#### Columns

pkUserId: Integer

username: Text

password: Text (salted and hashed)

userType: Text (Enum constraint to "Customer", "Employee", and "Manager")

isActive: Integer (0 or 1, SQLite doesn't support Boolean type)

---

### Products Table

#### Columns

pkProductId: Integer

name: Text

stock: Integer

ppu: Real (SQLite's floating point type)

img: Blob (Large Binary Object, stores data like images)

productType: Text (Enum constraint to "IceCream", "Cone", and "Topping")

---

### Drones Table

#### Columns

pkDroneId: Integer

name: Text

id: Integer

isActive: Integer (0, 1)

size: Integer (Constained to 1, 2, 3)

fkUserId: Integer

---

### Orders Table

#### Columns

pkOrderId: Integer

totalPrice: Real

employeeCut: Real

remainder: Real

timestamp: Text (SQLite supports ISO8601 timestamps, but this could also be an Integer field of milliseconds in epoch time)

fkDroneId: Integer (We could potentially use a JSON object to store multiple drone id's as well, if
necessary)

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

pkRestockId: Integer

timestamp: Text

expense: Real

