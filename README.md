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

# Create SNOW Credential Type

Select `Credential Types` from the menu
Click `Add`
Name the `Credential Type` ServiceNow
Input Configuration
```
fields:
  - id: username
    type: string
    label: Username
    help_text: Username used for authentication.
  - id: password
    type: string
    label: Password
    secret: true
    help_text: Password used for authentication.
  - id: client_id
    type: string
    label: Client ID
    help_text: ID of the client application used for OAuth authentication.
  - id: client_secret
    type: string
    label: Client Secret
    secret: true
    help_text: Secret associated with client_id. Used for OAuth authentication.
  - id: host
    type: string
    label: Host
    help_text: The ServiceNow host name including https://
  - id: refresh_token
    type: string
    label: Refresh Token
    help_text: Refresh token used for OAuth authentication.
  - id: timeout
    type: string
    label: Timeout
    help_text: Timeout in seconds for the connection with the ServiceNow instance.
  - id: grant_type
    type: string
    label: Grant Type
    help_text: Grant type used for OAuth authentication.
required:
  - host
```

Injector Configuration:
```
env:
  SN_HOST: '{{ host }}'
  SN_TIMEOUT: '{{ timeout }}'
  SN_PASSWORD: '{{ password }}'
  SN_USERNAME: '{{ username }}'
  SN_CLIENT_ID: '{{ client_id }}'
  SN_GRANT_TYPE: '{{ grant_type }}'
  SN_CLIENT_SECRET: '{{ client_secret }}'
  SN_REFRESH_TOKEN: '{{ refresh_token }}'
```


