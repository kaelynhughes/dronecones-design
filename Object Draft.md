# Data Object Classes Draft

---

### User

#### Attributes

username: String

userType: Enum ("Customer", "Employee", "Manager")

isActive: Boolean

id: Integer

---

### Product

#### Attributes

name: String

stock: Integer

ppu: Float

img: Image

type: Enum ("IceCream", "Cone", "Topping")

id: Integer

---

### Drone

#### Attributes

name: String

id: Number

isActive: Boolean

size: Enum ("Small", "Medium", "Large")

id: Integer

---

### Order

#### Attributes

cones: Array(FullCone)

totalPrice: Float

employeeCut: Float

remainder: Float

timestamp: Date

droneId: Integer

userId: Integer

id: Integer

---

### Full Cone

#### Attributes

components: Array(Product) (We can parse the number of scoops and toppings from their count in this array)
