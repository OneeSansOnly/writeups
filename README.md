# Overpass Writeup
*Difficulty - Easy*

*Room - Overpass*

*Created by: NinjaJc01*

## The inital scan shows TCP ports 22 and 80 open. We’ll start enumerating the webpage.

![nmap](images/nmap.PNG)

## Enumerating the webpage

### I used wfuzz to do basic fuzzing and within seconds we got the admin login . Let’s check out /admin first. 

![wfuzz](images/wfuzz.PNG)

## Checking Source Code

### As this room contains OWASP top 10 we should read the source code to hind any hints

![source](images/source.PNG)

### We can we have login.js file which checks for login info

![source2](images/source2.PNG)

#### Looking at the function login there’s a simple if else statement. Basically, it’s checking if the response is equal to “Incorrect Crentials”. If true, it will display a message saying “Incorrect Credentials”. Otherwise, it will set the cookie named “SessionToken” to the returned statusOrCookie and redirect the user to /admin. Since this is only checking for a cookie named SessionToken let’s just create a cookie and give it a bogus value.
#### So what we can do is make fake cookie named SessionToken and give it a false value and try to reload the page then 
![source2](images/webpage.PNG)

### You can make the fake cookie with Firefox or whatever browser using through the Cookie Editor. Onnce 
