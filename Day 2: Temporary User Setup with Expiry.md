Task:
As part of the temporary assignment to the Nautilus project, a developer named ammar requires access for a limited duration. To ensure smooth access management, a temporary user account with an expiry date is needed. Here's what you need to do:

Create a user named ammar on App Server 1 in Stratos Datacenter. Set the expiry date to 2027-03-28, ensuring the user is created in lowercase as per standard protocol.

Solution: Login to stapp01 server

`useradd ammar -e 2027-03-28`
