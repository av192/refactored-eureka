# refactored-eureka
Login Page using tkinter which has forgot password, create account, sign in buttons.

This will open a window which has two input fields - username and password.
The window has 3 buttons - sign in, create account and forgot password.

If the username and password matches, the user is taken to another window saying 'Login Success'.
If the username and password does not matche, a label will appear saying - 'Invalid Credentials'.

Choosing create account will create another window asking for e-mail id and password. A function checks if e-mail and password is valid using regex.
If both are valid, a label appears saying - 'Account created' and subsquently destroying the pop-up window.

Choosing forgot password will create another window asking for username registered. A function checks if username is registered or not.
If username is not registered, a label will appear saying - 'Username not registered'.
If username is registered, a new window will open up asking for otp_sent and new password.
