# Drone Cones API

# Home Page

No API needed, company info and button links can be hard coded.

# Login Customer/Employee/Manager

api.POST("loginUser")

Request params: {username: string, password: encrypted string}

Response success: {userType: string?(employee, customer, manager)} 202

Response fail: Unauthorized user 401

# Sign Up

api.POST("registerUser")

Request params: {newUser: User}

Response success: {"User registered successfully"} 201

Response fail: {error: string} 400

# Customer Menu

api.GET("getAllProducts")

Request params: { }

Response success: {products: Array<Product>}

Response fail: {error: string} 400

# Cart

### Cart may utilize previous api calls from the menu if necessary, but cones in cart will be saved in local memory instead of database.

# Checkout / Confirmation

api.POST("orderConfirmed")

Request params: {order: { username: string, cones: Array<IceCreamCone>, drones: Array<Drone>, cost: number, timestamp: Date } }

Response success: {"Order saved"} 201

Response fail: {error: string} 400

### Note: this would be called after the order is confirmed.

# View Information: Employee

api.GET("getAllDrones")

Request params: { }

Response success: {Array<Drone>: [ {name: Drone2, size: number, id: 10394825, isActive: true } ]}

Response fail: {error: string} 400

### Note: This should only retrieve drones that match the currently logged in user.  That may warrant
### sending the username, but I believe could be done better with a saved user session in the server.

---

api.GET("getEmployeeEarnings")

Request params: { }

Response success: {earnings: number}

Response fail: {error: string} 400

### See previous note, this would use the employee's username to find orders performed by drones they
### own, and then calculate their earnings on the server.

# Register Drone

api.POST("registerDrone")

Request params: {drone: Drone}

Response success: {"Drone registered successfully."} 201

Response fail: {error: string} 400

# Manage Drones

api.DELETE("deleteDrone")

Request params: {droneID: number}

Response success: {"Drone deleted successfully."} 200

Response fail: {error: string} 400

---

api.PUT("updateDrone")

Request params: {drone: Drone}

Response success: {"Drone updated successfully."} 200

Response fail: {error: string} 400

# View Information: Manager

api.GET("getOrders")

Request params: {orderCount: number, filter?} # Note: this is to limit amount of orders, in case we've got a ton in the db.

#### Note: Optionally this may be filtered to show a specific user's order, etc.

Response success: {order: Array<Order>}

Response fail: {error: string} 400

---

api.GET("getAccounting")

Request params: {date: Date} # Note: This allows the user to choose choose to calculate expense and income from a given date.

Response success: {totalIncome: number, stockExpense: number, employeeExpense: number} 

Response fail: {error: string} 400

# Inventory Management

api.PUT("updateProducts")

Request params: {products: Array<Product>}

Response success: {"Succesfully updated Products."}

Response fail: {error: string} 400

---

api.PUT("updateProduct")

Request params: {product: Product}

Response success: {"Succesfully updated Ice Cream."}

Response fail: {error: string} 400

---

api.POST("addProduct")

Request params: {product: Product}

Response success: {"Succesfully added new Product."}

Response fail: {error: string} 400

# Account Management

api.GET("getRecentUsers")

Request params: {count: number}

Response success: {Array<{Order, User.isActive}>}

Response fail: {error: string} 400

---

api.PUT("updateUser")

Request params: {username: string, isActive: boolean}

Response success: {"User updated successfully"}

Response fail: {error: string} 400

