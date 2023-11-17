# Low Level Design Audit

### Document Inconsistencies

## Universal

---

#### Home View

No Home Page documents were made.

---

#### Login View

Image is ambiguous (why make 3 login pages if they'll all look the same?)

Guest account option should be exclusive to user login.

---

#### Signup View

No image.

---

#### Account Info View

No text description.

See Design Concerns section.

---

## Customer

---

#### Menu View

No add to cart buttons in image.

API request to submit the order probably doesn't need to happen until the order
is confirmed from the cart.

We decided not to include a cart table in the database.

---

#### Cart View

No delete button in image.

No modify button in image.

No back button is needed, menu is available in side bar.

API request for price is unnecessary, price is provided when products are all
retrieved from the database.  We could potentially include one for flow-breaking
use cases and performance though.

API post request for the final order should be sent after the checkout button
is pressed (probably).

---

#### Confirmation View

No description of order in image.

---

#### Order History View

No descriptive design document.

API call for orders with filters need refinement.

---

## Employee 

---

#### Drone Info View

Manage and Register buttons are on sidenav, not bottom.

Recent data for each drone not shown as described in text.

---

#### Manage Drones / Drone Edit / Other Drone Views

Inconsistent names and page numbers.

API/Object data for drone earnings has yet to be written.

General ideas about the detailed Drone views seems conflicting.
  We should definitely re-evaluate our goals for these views as a group.

---

## Manager

---

#### Manager Info View

No documents were made.  Perhaps this view is unnecessary?

---

#### Manager Inventory / Update View

Document titles for Inventory View and Update View are both Inventory View.

No button in image to add new stock items.

See Design Concerns section.

---

#### Banned Users View

No major conflicts.

---

#### Manager History View

No text documentation.

---

## Backend/Data

---

#### Data Objects

User may need extra attributes, see Profile View.

All floats should be changed to int for monetary transaction calculation.

On the Order object, drone Id's should be an array.

---

#### API

Need more filtered requests for drone order history and drone earnings.

Should request to update a group of item automatically return the updated items? 
This would benefit the view with live updates after success.

Will probably need to change based on final database decisions.

---

### Database

Discussion needed on how much user info to store.

Products table and other should change REAL type to INTEGER for monetary 
transactions.

Products table should include separate fields for Cost to purchase and Sell price.

See Drones section in Design Concerns, but should the Drones Table include its own
 income column?

Tracking multiple drones on one order currently requires foreign key concatenation 
(not great).

Order table price tracking may need to change.

Ordered Cones table includes a lot of fields that may be repetitive.

---

# Design Concerns

## Universal

---

#### Misc.

We should convert money calculation across the app into Int instead of Float.  
Mostly applies to database.

---

#### Login View

I think there should be bold text descriptions of which login you're on, 
to avoid confusion for users that may have 1 account and not another, or
manage a customer and employee account.

The design doc ideas are all good, but some seem a little out of scope.  
In specific, resetting a password is a great feature, but would typically involve 
working with email, and alternatives may be just as tough. Counting login attempts
probably wouldn't be hard, but I'm slightly worried about complications with that.

I think there should be links to the other login pages, at least between the customer 
and employee pages, if a user is lost.  Maybe not though, idk.

---

#### Account Info View

We should discuss whether we will collect and save user's legal names on signup,
 and if we are keeping usernames and emails separate.  I was under the impression 
we wanted to just use emails AS usernames, but I may be remembering incorrectly.

---

## Customer

---

#### Menu View

Adding each scoop, topping, and cone to the cart separately seems unintuitive.
Maybe we should design one cone at a time, and have one add to cart button?

We should specify how multiple cones order flow works, and how user can add more
than one scoop to a cone.

Should we display a price for the cone on the menu page?

---

#### Cart View

Displaying full custom images of each cone may be difficult, but might work 
based on some other teams wireframe prototypes.

---

#### Confirmation View

No huge concerns, we just need to decide if an order description should be shown 
along with the timer.

The page should only need the timestamp of when the order was submitted, if that.
  That said, passing the order would be trivial.

---

#### Order History View

We should specify all the info we'd like to display to a customer for each past 
order.

---

## Employee

---

#### Drone Info View

Should we display deactivated drones as well, just grayed out maybe?

Displaying tons of detail for each drone on this page seems unnecessary, given 
that the manage drones page does the same.

#### Drone Edit / History / Manage / Register Views

We should only display certain order details for each drone.  Omit usernames and cone
details maybe?  Not sure.

Mostly as a note to self, but drone earnings can be pulled from database by 
searching the orders table for orders involving this drone.

In regard to that last note, we may need to rework database to store drone earnings 
differently.  How would earnings be split between multi-drone orders easily otherwise?

This needs some serious discussion in general.  Personally, I think I favor the
 images, and adding an extra view for drone history.  That said, 
we should vote or something after discussion, and choose specifics.

---

## Manager

---

#### Inventory View / Update View

These seem a bit redundant.  Perhaps the base page could handle restocking, and 
a button could open a dialog to add new products?

We should add the ability to change an items price.  

If we do want to add stock in units that do not match the units they are sold in (which I don't, for the record),
we'll need unit conversion logic.  For example, if you restock ice cream in gallons, we 
need a set amount of scoops in each gallon.  This doesn't really match the real world, 
~~Which is why tracking the entire stock programatically doesn't make sense to me at all~~
, but it's good enough.

---

## Backend/Data

---

#### Data Objects

Orders may need some work in the database and as a frontend object.

Specifically, we should discuss how money on an order is stored, especially when 
employee payment may be split between multiple drones.  Should drone earnings be 
stored on each drone?  Both?

---

### Potential Extra Features

Add cone directly from history to cart.

