Title: Tic-Tac-Toe Writeup
Author: Sean Kung
Date: 2020-06-11
Category: posts
Tags: python
Slug: password-checker-wripteup


The code sample is found [here](https://github.com/seakun/Python-Projects/blob/master/checkpassword.py).


Modules used: requests, hashlib, and sys.


We use this program to check if the given password was cracked.
To do that we use the command line and type in the program name with as many passwords as we want to check:

    :::python3
    python3 checkpassword.py password123 abc123 test123

In the main method, it iterates through the arguments. In this case, checkpassword will loop through "password123", "abc123", and "test123".

The method calls pwned_api_check(password) to:
⋅⋅* Hash the password using hashlib.
⋅⋅* Split the hashed password into the first 5 and last 5 characters.


We split the hashed password because it would be insecure to send the entire password over the internet anyway.


The database we're querying is on haveibeenpwned.com. We'll send a request and we'll get the list of all hashes that have that first 5 characters hashed.


It's in the get_password_leaks_count() method where we match the hashes and count the number of times that hash has shown up. 


The program prints out if the password is found and how many times it showed up. Otherwise, it states the password wasn't found.
