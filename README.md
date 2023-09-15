# snow_inventory

## Create a RO token in git

Go to:
https://github.com/settings/tokens

Under `Personal access tokens` create a `Fine-grained tokens` with read-only permissions to the `Contents` of the required repositories.

## Add SCM Credential to AWX

Select `Credentails` from the menu
Click `Add`
Name the credential
Choose `Source Control`
The username can be anything, and the token will be the password

## Add this project

Select `Projects` from the menu
Click `Add`
Name the project
Source Control Type `Git`
Source Control URL `https://github.com/bradynathan/snow_inventory.git`
Selec the source control credential from previous step

#Create SNOW Credential Type
