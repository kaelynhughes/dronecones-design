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
Reponse fail: {error: string} 400

# Customer Menu

### Question: If Ice Cream, Toppings, and Cones all have similar attributes, should they share a
### type?

api.GET("getAllIceCream")
Request params: { }
Response success: {Array<IceCream>: [ {name: Chocolate, stock: 12, ppu: 0.45, img: choc.png, idx: 1} ]}
Reponse fail: {error: string} 400

api.GET("getAllToppings")
Request params: { }
Response success: {Array<Topping>: [ {name: Oreos, stock: 20, ppu: 0.10, img: oreo.png, idx: 1} ]}
Reponse fail: {error: string} 400

api.GET("getAllCones")
Request params: { }
Response success: {Array<Cone>: [ {name: Waffle, stock: 3, ppu: 0.40, img: waffle.png, idx: 1} ]}
Reponse fail: {error: string} 400

### Note: We could add request for just one type of ice cream based on name, but that seems unnecessary currently.

# Cart

### Cart may utilized previous api calls from the menu, but I think cones currently in the cart
### should be saved in local memory, not db storage.  Up for debate though.

# Checkout / Confirmation

api.POST("orderConfirmed")
Request params: {order: { username: string, cones: Array<IceCreamCone>, drones: Array<Drone>, cost: number, timestamp: Date } }
Response success: {"Order saved"} 201
Reponse fail: {error: string} 400

### Note: this would be called after the order is confirmed.

# View Information: Employee

api.GET("getAllDrones")
Request params: { }
Response success: {Array<Drone>: [ {name: Drone2, size: number?, id: 10394825, isActive: true } ]}
Reponse fail: {error: string} 400

### Note: This should only retrieve drones that match the currently logged in user.  That may warrant
### sending the username, but I believe could be done better with a saved user session in the server.

api.GET("getEmployeeEarnings")
Request params: { }
Response success: {earnings: number}
Reponse fail: {error: string} 400

### See previous note, this would need the employee's username to find orders performed by drones they
### own, and then calculate their earnings on the server maybe?  Or their cut could be saved in their
### database? This might be tricky, worth discussing.

# Register Drone

api.POST("registerDrone")
Request params: {drone: Drone}
Response success: {"Drone registered successfully."} 201
Reponse fail: {error: string} 400

# Manage Drones

api.DELETE("deleteDrone")
Request params: {droneID: number}
Response success: {"Drone deleted successfully."} 200
Reponse fail: {error: string} 400

api.PUT("updateDrone")
Request params: {drone: Drone}
Response success: {"Drone updated successfully."} 200
Reponse fail: {error: string} 400

### Note: updateDrone can be used to activate and deactivate a drone, but also change other traits
### if we so desire.

# View Information: Manager

api.GET("getOrders")
Request params: {orderCount: number} ### Note: this is to limit amount of orders, in case we've got a ton in the db.  Might not be necessary though.
Response success: {order: Array<Order>}
Reponse fail: {error: string} 400

api.GET("getAccounting")
Request params: {date: Date?} ### Note: should we choose how much calculate expense and income from a given date?
Response success: {PLACEHOLDER TEXT} This one is weird.  Do we do all the calculations in the server, or what? Seems complicated.
Reponse fail: {error: string} 400

# Inventory Management

api.PUT("updateIceCream")
Request params: {iceCreamIdx: number}
Response success: {"Succesfully updated Ice Cream."}
Reponse fail: {error: string} 400

api.PUT("updateCone")
Request params: {coneIdx: number}
Response success: {"Succesfully updated Cone."}
Reponse fail: {error: string} 400

api.PUT("updateTopping")
Request params: {toppingIdx: number}
Response success: {"Succesfully updated Topping."}
Reponse fail: {error: string} 400

api.POST("addIceCream")
Request params: {iceCream: IceCream}
Response success: {"Succesfully added new Ice Cream."}
Reponse fail: {error: string} 400

api.POST("addCone")
Request params: {cone: Cone}
Response success: {"Succesfully added new Cone."}
Reponse fail: {error: string} 400

api.POST("addTopping")
Request params: {topping: Topping}
Response success: {"Succesfully added new Topping."}
Reponse fail: {error: string} 400

# Note: These might be redundant, but separating all 3 types seems like a good idea to me.
# Up for debate.

# Account Management

### Note: to get the list of recent users, I think that api.getOrders could be utilized.
### That said, if we color names based on user activity status, maybe a separate call should be used,
### because user activity status probably wouldn't make much sense to include in an order.
### Maybe a joint api call that gets user activity and combines it with the order data?

api.PUT("updateUser")
Request params: {username: string, isActive: boolean}
Response success: {"User updated successfully"}
Reponse fail: {error: string} 400







