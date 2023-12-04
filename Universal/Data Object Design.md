# Data Object Classes

---

### User

#### Attributes

username: string

user_type: enum ("Customer", "Employee", "Manager", "Guest")

isActive: boolean

id:number

---

### Product

#### Attributes

display_name: string

stock: number

price_per_unit: number

product_type: enum ("IceCream", "Cone", "Topping")

id: number

---

### Drone

#### Attributes

display_name: string

id: number

is_active: boolean

drone_size: number

id: number

---

### Order

#### Attributes

cones: Array(FullCone)

total_price: number

employee_cut: number

profit: number

order_time: string

customer_id: number

id: number

---

### Full Cone

#### Attributes

products: Array(Product)
drone_id: number
