# Ban Form View

## View/Feature description


The band form isa page that allows managers to ban employees and customers accounts alike using a simple form. It should be linked to from the page displaying each transaction. It should have some input allowing for the ban of users, but also a list of banned users, and the ability to unban them.

## View

There should be a grid of all banned users and their info as well as a simple red “unban” button. The ban button is hosted on the page where all transactions, but there also should be an input box that allows people to be banned if their email and role is specified too.

## Functions needed

###Unban Function###
	* method: POST
	* inputs: userID
	* outputs: changes ban boolean in the data tables
###Ban Function###
	* method: POST
	* inputs: userID, Role
	* outputs: changes ban boolean in the data tables

## Interactions

When an unban request is submitted, a request to change the banned boolean will be made to our database. If failed, an alert will be sounded, and the user will remain on the grid. If it is successful, react should remove that list element from the grid. When a ban request is submitted, a request to set the ban boolean to true will be sent to the database. If failed, an alert will sound and nothing will change. If it succeeds, the user will be added to the grid of banned users, and it will briefly highlight, then it will be uniform with the rest of the grid, and the user will have been banned.
