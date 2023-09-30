# Drone Cone API Draft

# Home Page

No API needed, company info and button links can be hard coded.

# Login Customer/Employee/Manager

api.POST("loginUser")

Request params: {username: string, password: encrypted string}

Response success: {userType: string?(employee, customer, manager)} 202

Response fail: Unauthorized user 401

# Sign Up

api.POST("registerUser")

Request params: {username: string, password: encrypted string}

Response success: {"User registered successfully"} 201

Response fail: {error: string} 400

# Customer Menu

### Question: If Ice Cream, Toppings, and Cones all have similar attributes, should they share a type?

api.GET("getAllIceCream")

Request params: { }

Response success: {Array<IceCream>: [ {name: Chocolate, stock: 12, ppu: 0.45, img: choc.png, idx: 1} ]}

Response fail: {error: string} 400

---

api.GET("getAllToppings")

Request params: { }

Response success: {Array<Topping>: [ {name: Oreos, stock: 20, ppu: 0.10, img: oreo.png, idx: 1} ]}

Response fail: {error: string} 400

---

api.GET("getAllCones")

Request params: { }

Response success: {Array<Cone>: [ {name: Waffle, stock: 3, ppu: 0.40, img: waffle.png, idx: 1} ]}

Response fail: {error: string} 400

---

api.GET("getAllProducts")

Request params: { }

Response success: {Array<IceCream, Cone, Topping>}

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

Response success: {Array<Drone>: [ {name: Drone2, size: number?, id: 10394825, isActive: true } ]}

Response fail: {error: string} 400

### Note: This should only retrieve drones that match the currently logged in user.  That may warrant
### sending the username, but I believe could be done better with a saved user session in the server.

---

api.GET("getEmployeeEarnings")

Request params: { }

Response success: {earnings: number}

Response fail: {error: string} 400

### See previous note, this would need the employee's username to find orders performed by drones they
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

### Note: updateDrone can be used to activate and deactivate a drone, but also change other traits if we so desire.

# View Information: Manager

api.GET("getOrders")

Request params: {orderCount: number} ### Note: this is to limit amount of orders, in case we've got a ton in the db.  Might not be necessary though.

Response success: {order: Array<Order>}

Response fail: {error: string} 400

---

api.GET("getAccounting")

Request params: {date: Date?} ### Note: should we choose how much calculate expense and income from a given date?

Response success: {PLACEHOLDER TEXT} This one is weird.  Do we do all the calculations in the server, or what? Seems complicated.

Response fail: {error: string} 400

# Inventory Management

api.PUT("updateIceCream")

Request params: {iceCream: IceCream}

Response success: {"Succesfully updated Ice Cream."}

Response fail: {error: string} 400

---

api.PUT("updateCone")

Request params: {cone: Cone}

Response success: {"Succesfully updated Cone."}

Response fail: {error: string} 400

---

api.PUT("updateTopping")

Request params: {topping: Topping}

Response success: {"Succesfully updated Topping."}

Response fail: {error: string} 400

---

api.POST("addIceCream")

Request params: {iceCream: IceCream}

Response success: {"Succesfully added new Ice Cream."}

Response fail: {error: string} 400

---

api.POST("addCone")

Request params: {cone: Cone}

Response success: {"Succesfully added new Cone."}

Response fail: {error: string} 400

---

api.POST("addTopping")

Request params: {topping: Topping}

Response success: {"Succesfully added new Topping."}

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







◊
