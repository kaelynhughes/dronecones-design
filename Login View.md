# Login View

## View/Feature description

Login page is a simple view. It is necessary to allow user's the opportunity to create and access an account, which allows them certain functionalities based on whether they are a customer, a drony, or a manager. It is also important to allow guest accounts for user's who wish to use the website services without being forced to have an account. With that being said, this view will focus on the accepting login information for each type of user, creating a temporary account that is limited to being a customer, and the ability for new users to create a new account.

## View

Login page will default to a simple form with two inputs. "Username" and "Password" (Further details will be provided [below]). Inputs must be labelled clearly, allowing user to know for certain which empty field corresponds to which label.

Underneath those two inputs is a link labelled 'Forgot Password?' that will redirect the user to a password reset form.

The form will have a button labelled 'Login' that will attempt to log the user in. Should it fail, there needs to be a noticable message displayed to the user, alerting them to the failure. Upon success, there should be a message displayed, or at minimum some indication that there has been no issue.

There must also be a link labelled 'Continue as Guest' that will create a temporary account that the user may use to have customer access to the website.

Finally, there must be a link labelled 'Need an account?' that will direct the user to a new form that will allow them to create an account to use to access the website.

## Functions needed

### Login Form

Action: [???]
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
    input
        type: submit
        value: Log In

### Error Handling

Wrong login info
    Trigger: Submitted inputs does not match database entries
    Actions:
        Message ("Incorrect Username or Password.")
        Redirect (Login page)

Too many Attemps:
    Trigger: Failure to login after [???] attempts
    Actions:
        Message ("Too many failed attempts. Please try again [???].")
        Account Lockout (Temporary, time based)

## Interactions

When submitted, form will be sent to verify is inputs matched database of user accounts. If failed, will redirect back to login page to allow user to try again. Upon success, database will verify type of account and redirect user to appropriate page I.E. Manager, Employee, Customer.

If link 'Forgot Password' is selected, user will be redirected to reset password page to allow a change of password.

If link 'Continue as Guest' is selected, user will be redirected to home page with access to temporary account that will allow them to make use of customer privileges.

If link 'Need and Acount?' is selected, user will be redirected to sign up page to allow user to create either a customer account or an employee account.