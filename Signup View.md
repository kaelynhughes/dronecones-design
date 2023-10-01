# Signup View

## View/Feature description

Signup page is a simple view. It is necessary to allow users the opportunity to create an account. The average user will create a customer account, which allows them to create an order, and access their order history. Users will have the chance to register for an employee account. This account has access to a personal inventory of drones that the user submits to make deliveries on behalf of DroneCones. This page allows employees to view and edit their submitted drones for delivery, view an order history that their drones have delivered, and view how much income each of their drones is accumulating.

## View

Sign up page will be a simple form with three inputs. "Username", "Password", and "Confirm Password" (Further details will be provided [below]) Inputs must be labelled clearly, allowing user to know for certain which empty field corresponds to which label.

Underneath those two inputs is text saying 'Already a member?' followed by a link labelled 'Log In' that will redirect the user to the log in page.

The form will have a button labelled 'Sign up' that will attempt to create an account for the user. Should it fail, there needs to be a noticable message displayed to the user, alerting them to the failure. Upon success, there should be a message displayed, or at minimum some indication that there has been no issue.

## Functions needed

### Signup Form

Action: [???]
    method: post

    label
        for: username
        "Username"
    input
        type: text
        id: username
        name: username
    label
        for: password
        "Password"
    input
        type: text
        id: password
        name: password
    label
        for: confirm
        "Confirm Password"
    input
        type: text
        id: confirm
        name: confirm
    input
        type: checkbox
        id: employee
        name: employee
    label
        for: employee
        "Click here to register as a Droner"
    input
        type: submit
        value: Sign Up

### Error Handling

Blank inputs:
    Trigger: Submitted inputs are blank
    Actions:
        Message ("[label] can not be blank.")
        Redirect (Sign up page)

Username taken:
    Trigger: Database already contains given username
    Actions:
        Message ("This username has already been taken")
        Redirect (Sign up page)

Password misinput:
    Trigger: Confirm does not match Password
    Actions:
        Message: ("Passwords do not match.")
        Redirect (Sign up page)

## Interactions

When submitted, form will be sent to be saved to the database. If failed, will redirect back to sign up page to allow user to try again. Upon success, database will verify type of account and redirect user to appropriate page I.E. Employee, Customer.

If link 'Log In' is selected, user will be redirected to Login page.