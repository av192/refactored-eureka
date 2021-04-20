from tkinter import *
import re
from time import sleep
from random import randint

# Create the main window and give its dimensions and title
root = Tk()
root.title('Sign in to Tkinter')
root.geometry('400x300')
root.configure(bg='gray87')

# Make a dictionary with keys as username and values as passwords
username_dictionary = {'25': '69'}      # This contains all the passwords and usernames

# Input Fields for main window
email = Entry(root, width=30, borderwidth=2)
password = Entry(root, width=20, borderwidth=2, show='*')

# Place the input fields in the main window
email.place(relx=0.18, rely=0.27)
password.place(relx=0.18, rely=0.47)


# Make the login successful window
def login_success():
    root_success = Tk()
    root_success.title('Login Successful')
    root_success.geometry('300x200')

    login_success_label = Label(root_success, text='Login Success', bg='ghost white', fg='gray2',
                                font='Helvetica 18 bold')
    login_success_label.place(relx=0.5, rely=0.05, anchor='center')

    # By clicking, it closes the login success window
    back_button = Button(root_success, text='Back', command=lambda: root_success.destroy())
    back_button.place(relx=0.45, rely=0.8)

    welcome_label = Label(root_success, text='Welcome to Tkinter', bg='ghost white', fg='gray2',
                          font='Helvetica 18 bold')
    welcome_label.place(relx=0.15, rely=0.45)

    root_success.mainloop()


# Make the registration window
def register_window():
    root_register = Tk()
    root_register.title('Join Tkinter')
    root_register.geometry('300x200')

    create_account_label = Label(root_register, text='Create Your Account', bg='ghost white', fg='gray2',
                                 font='Helvetica 18 bold')
    create_account_label.place(relx=0.5, rely=0.05, anchor='center')

    # Now make the username and password fields for registration window
    register_username = Entry(root_register, width=30, borderwidth=2)
    register_password = Entry(root_register, width=20, borderwidth=2)
    register_password_confirm = Entry(root_register, width=20, borderwidth=2)

    # Place the input fields in the registration window
    register_username.place(relx=0.18, rely=0.3)
    register_password.place(relx=0.18, rely=0.5)
    register_password_confirm.place(relx=0.18, rely=0.7)

    # Make username, password labels for the registration window
    register_username_label = Label(root_register, text='Email address:')
    register_password_label = Label(root_register, text='Password:')
    register_password_confirm_label = Label(root_register, text='Confirm Password:')

    # Place the labels in the registration window
    register_username_label.place(relx=0, rely=0.2)
    register_password_label.place(relx=0, rely=0.4)
    register_password_confirm_label.place(relx=0, rely=0.6)

    # When submit button is pressed in the registration window
    def submit_button_register_func(email_verify, password_verify, confirm_password):
        if email_verify in username_dictionary.keys():
            # First a label saying account created
            account_already_registered_label = Label(root_register, text='Account already Registered')
            account_already_registered_label.place(relx=0.4, rely=0.59)
            register_username.delete(0, END)
            register_password.delete(0, END)
            register_password_confirm.delete(0, END)
            sleep(1)
            account_already_registered_label.after(2000, account_already_registered_label.destroy)
            return

        # This checks whether the given username and password is valid or not (for registration window)
        def regex_func(email_verify_1, password_verify_1, confirm_password_1):

            regex_for_email = r'^[a-z0-9]+[\._]?[a-z0-9]+[@]\w+[.]\w{2,3}$'  # Used in registration window

            # Password is alpha numeric and email is valid
            boolean_of_password_validation = password_verify_1.isalnum()  # will be used in submit_button_register_func
            boolean_of_email_validation = re.search(regex_for_email, email_verify_1)

            # If all conditions are met
            if boolean_of_email_validation and boolean_of_password_validation and confirm_password_1 == password_verify_1:
                return 'True'
            elif not boolean_of_email_validation:
                return 'Email invalid'
            elif not boolean_of_password_validation:
                return 'Password Invalid'
            else:  # Happen only when confirmed password != password
                return 'Password not confirmed'

        regex_func_output = regex_func(email_verify, password_verify, confirm_password)

        # This takes the input if password is valid and adds to the dictionary of usernames
        if regex_func_output == 'True':
            # If regex_func is true, all inputs are verified. So create the account.
            # First a label saying account created
            account_created_label = Label(root_register, text='Account Registered')
            account_created_label.place(relx=0.6, rely=0.7)

            # Add the pass and username to dictionary
            username_dictionary[email_verify] = password_verify

            # Destroy the registration window
            root_register.after(3000, root_register.destroy)
            return

        else:
            register_error_label = Label(root_register, text=regex_func_output)
            register_error_label.place(relx=0.4, rely=0.59)
            register_username.delete(0, END)
            register_password.delete(0, END)
            register_password_confirm.delete(0, END)
            sleep(1)
            register_error_label.after(2000, register_error_label.destroy)
            return

    # proper function for submit_button
    proper_func = lambda: submit_button_register_func(register_username.get(), register_password.get(),
                                                      register_password_confirm.get())
    # This function uses the given values of username and password

    # Submit Button in registration window
    submit_button_register = Button(root_register, text='Create Account', command=proper_func)
    submit_button_register.place(relx=0.4, rely=0.8)

    root_register.mainloop()


# This function checks OTP, validating password, validating confirmed password
def update_func1(real_otp, input_otp, password_given, confirm_pass):
    password_valid = password_given.isalnum()
    if real_otp == input_otp and password_valid and password_given == confirm_pass:
        return 'True'
    elif not real_otp == input_otp:
        return 'OTP Invalid'
    elif not password_valid:
        return 'Password should be alphanumeric'
    elif not password_given == confirm_pass:
        return 'Password not confirmed'


# When forgot password is pressed, a window will open up asking for e-mail id registered.
def forgot_pass_window():
    # Make a window and give its dimensions and title
    forgot_pass_root = Tk()
    forgot_pass_root.title('Forgot Password')
    forgot_pass_root.geometry('300x200')

    # Give a label asking for username registered
    forgot_username_label = Label(forgot_pass_root, text='Email address registered:')
    forgot_username_label.place(relx=0, rely=0.25)

    # An input field asking for username registered
    forgot_username_entry = Entry(forgot_pass_root, width=30, borderwidth=2)
    forgot_username_entry.place(relx=0.18, rely=0.4)

    # If username is registered in forgot pass window, a new window appears asking for new password.
    # This func will open a new window, send OTP, verify it, make new pass and close the window.
    def username_verified_forgot(window_tk):
        forgot_pass_new_pass_root = Tk()  # New window will open asking to verify OTP and make new password.
        forgot_pass_new_pass_root.title('Make new password')
        forgot_pass_new_pass_root.geometry('300x200')

        # Make Labels for OTP and new Password
        otp_sent_pass = Label(forgot_pass_new_pass_root, text='OTP has been sent to your E-mail')
        otp_sent_pass.place(relx=0, rely=0.03)

        otp_forgot_pass = Label(forgot_pass_new_pass_root, text='OTP:')
        otp_forgot_pass.place(relx=0, rely=0.15)

        new_password_forgot = Label(forgot_pass_new_pass_root, text='New Password:')
        new_password_forgot.place(relx=0, rely=0.35)

        confirm_new_pass_forgot = Label(forgot_pass_new_pass_root, text='Confirm new password:')
        confirm_new_pass_forgot.place(relx=0, rely=0.55)

        # Make input fields
        otp_forgot_pass_input = Entry(forgot_pass_new_pass_root, width=30, borderwidth=2)
        otp_forgot_pass_input.place(relx=0.18, rely=0.25)

        new_password_forgot_input = Entry(forgot_pass_new_pass_root, width=30, borderwidth=2)
        new_password_forgot_input.place(relx=0.18, rely=0.45)

        confirm_new_pass_forgot_input = Entry(forgot_pass_new_pass_root, width=30, borderwidth=2)
        confirm_new_pass_forgot_input.place(relx=0.18, rely=0.65)

        # Generate OTP for validation
        otp_sent = randint(100000, 999999)
        print(otp_sent)

        # A function should come here which sends email of otp to the id entered so that otp can be verified.

        # command for update password button
        def update_func():
            func_value = update_func1(str(otp_sent), otp_forgot_pass_input.get(), new_password_forgot_input.get(),
                                      confirm_new_pass_forgot_input.get())

            if func_value == 'True':  # If all fields are correct
                password_updated_label = Label(forgot_pass_new_pass_root, text='Password updated')
                password_updated_label.place(relx=0.4, rely=0.88)
                username_dictionary[forgot_username_entry.get()] = new_password_forgot_input.get()
                forgot_pass_new_pass_root.after(2000, forgot_pass_new_pass_root.destroy)
                window_tk.after(2000, window_tk.destroy)  # Destroy the previous window
                return

            else:
                error_label_forgot = Label(forgot_pass_new_pass_root, text=func_value)
                error_label_forgot.place(relx=0.3, rely=0.88)
                error_label_forgot.after(2000, error_label_forgot.destroy)
                return

        # Now make a 'update password' button
        # Command of this button is checking for OTP, validating password, validating confirmed password
        update_password_button_forgot = Button(forgot_pass_new_pass_root, text='Update Password', command=update_func)
        update_password_button_forgot.place(relx=0.4, rely=0.77)

        # This code will come in the end.

    # After pressing Next in forgot password
    # This checks if username is registered or not
    def verify_username_forgot(forgot_username_entry_1):
        if forgot_username_entry_1 not in username_dictionary.keys():  # If username is not registered

            # A label will come up and will be destroyed after certain time
            email_not_registered_label = Label(forgot_pass_root, text='E-mail not registered')
            email_not_registered_label.place(relx=0.2, rely=0.65)
            email_not_registered_label.after(2000, email_not_registered_label.destroy)

        else:  # If username is registered
            username_verified_forgot(forgot_pass_root)

        return

    # A button with text='Next' and checks if username is registered or not.
    next_forgot_button = Button(forgot_pass_root, text='Next',
                                command=lambda: verify_username_forgot(forgot_username_entry.get()))
    next_forgot_button.place(relx=0.4, rely=0.55)


# defining functions
def forgot_pass_func():
    # When forgot password is pressed in the main window
    forgot_pass_window()
    return


def submit_func():
    # When submit is pressed in the main window
    try:
        if username_dictionary[email.get()] == password.get():  # If password matches
            # Open the login successful window
            login_success()

        else:
            error_label = Label(root, text='Incorrect credentials, try again ')  # Error label is formed
            error_label.place(relx=0.51, rely=0.48)  # Place the error label
            error_label.after(3000, error_label.destroy)  # Destroy the label after a certain time
            return False
    except KeyError:
        error_label = Label(root, text='Incorrect credentials, try again ')  # Error label is formed
        error_label.place(relx=0.51, rely=0.48)  # Place the error label
        error_label.after(3000, error_label.destroy)  # Destroy the label after a certain time
        return False


def register_func():
    # When create account is pressed
    register_window()
    return


# Create the label for main window
sign_in_label = Label(root, text='Sign in to Tkinter', bg='ghost white', fg='gray2', font='Helvetica 18 bold')
sign_in_label.place(relx=0.5, rely=0.05, anchor='center')

# Create labels for main window
username_label = Label(root, text='Email address registered:')
password_label = Label(root, text='Password:')
register_label = Label(root, text='New to Tkinter?')
contact_label = Label(root, text='©Tkinter corp           Contact: 999-999-999            Email: tkinter@corp.in ')

# Place the labels for main window
username_label.place(relx=0, rely=0.2)
password_label.place(relx=0, rely=0.4)
register_label.place(relx=0.1, rely=0.7)
contact_label.place(relx=0, rely=0.9)

# Make Forgot Password and Submit buttons for the main window
forgot_password = Button(root, text='Forgot password?', command=forgot_pass_func, width=13)
submit = Button(root, text='SUBMIT', command=submit_func)
register_button = Button(root, text='Create Account', command=register_func)

# Place the buttons in the main window
forgot_password.place(relx=0.6, rely=0.567)
submit.place(relx=0.243, rely=0.55)
register_button.place(relx=0.32, rely=0.69)

root.mainloop()
