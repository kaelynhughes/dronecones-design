# Inventory View

## View/Feature description

Manager's must have an intuitive page to update their stock. The intention is to physically take stock of items on paper to have available, as to update stock recorded in DroneCones all at once. Stock will not be tracked by individual units, but by package (I.E. tubs of icecream, boxes of toppings). Only the manager will have permission to update this inventory.

## View

Single page displaying table of all items available for purchase, and a blank input spot to insert count of available stock.

Below, a button labelled 'Update' that will submit changes and redirect user to inventory page.

## Functions needed

### Update Form

Action: [???]
    method: post

    label (Repeated for each inventory item)
        for: [item]
        "[item]"
    input (Repeated for each inventory item)
        type: number
        id: [item]
        name: [item]
    input
        type: submit
        value: Update

## Interactions

When submitted, form will be sent to be saved to the database. If failed, will redirect back to update page to allow user to try again. Upon success, database will update the database with the provided counts and redirect user back to Inventory page.