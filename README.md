# Project 8 - Pentesting Live Targets

Time spent: **16** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each color is vulnerable to only 2 of the 6 possible exploits. First discover which color has the specific vulnerability, then write a short description of how to exploit it, and finally demonstrate it using screenshots compiled into a GIF.

## Blue

Vulnerability #1: Session Hijacking/Fixation

Description:
-The hicjacking is performed on two browsers; one is logged in as administrator, other as a regular
-Using "public/hacktools/change_session_id.php", we can acquire the session ID
-This enables us to modify the session ID to the one obtained from victim

GIF: 
<img src="Blue-SessionHijack.gif">

Vulnerability #2: SQL Injection (SQLi)
Description:
-This injection is done by changing id to " OR SLEEP(5)=0-- " at the end of the URL
-Result is a pause for 5 seconds, then displaying the information

GIF:
<img src="Blue-SQLi.gif">

## Green

Vulnerability #1: Cross-Site Scripting (XSS)
Description:
-First we go and fill out feedout form "Contact Us" with XSS
-Upon administrator clicking "View Feedback" displays attack success

GIF:
<img src="Green-XSS.gif">

Vulnerability #2: Username Enumeration
Description:
- Simply utilizing the explicit criteria for existing and non-existing users
- In particular, entering credentials for existing users message is bold while entering credentials for non-existent users message is not bold

GIF:
<img src="Green-UserEmur.gif">

## Red

Vulnerability #1:Insecure Direct Object Reference (IDOR)

Description:
- This is done by changing the value of "id" in the URL to modify the GET request
- Due to missing code in Red we can access id=10 (shouldn't be public as it contains sensitive data)
- Additionally we're able to extract information from id=11, viewing info on fired employees

GIF:
<img src="RED-IDOR.gif">

Vulnerability #2: Cross-Site Request Forgery (CSRF)

Description:
-This will modify the information in the database
-First we send  the link to administrator through "feedback"
-The script will run upon opening the feedback page; the script will essentially change the information of the employee

GIF:
<img src="Red-CSRF.gif">
