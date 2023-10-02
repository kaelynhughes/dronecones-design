# Inventory View

## View/Feature description

Manager's must have an intuitive view of their current stock. The view involves a table of what products are currently available. Stock will not be tracked by individual units, but by package. (I.E. tubs of icecream, boxes of toppings) It is important that physical inventory is tracked daily and reported. Only the manager will have access to this inventory, and so it is necessary to allow them permission to alter the table. Whether to note when stock is going down, or to update when stock has been replenished.

## View

Single page displaying table of all items available for purchase, and the number of units that were available as of the previous update.

Below, a button labelled 'Update' that will take the user to a page that will allow them to insert manually new counts of the inventory and submits those counts all at once.

## Functions needed

### Update Button

Action: Redirect
    method: [???]

    type: button
    id: update
    "Update"

## Interactions

When the button is clicked, it will redirect the user to Update View.