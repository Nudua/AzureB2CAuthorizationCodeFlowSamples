# Securing an ASP.NET 6 Web App with Azure AD B2C using Authorization Code Flow with PKCE
Sample code for the blog post [Securing an ASP.NET 6 Web App with Azure AD B2C using Authorization Code Flow with PKCE](https://www.ramstad.io/2022/03/08/Securing-an-ASP-NET-6-Web-App-with-Azure-AD-B2C-using-Authorization-Code-Flow-with-PKCE/) and includes examples for Razor Pages, MVC, and Web Api applications.

## Prerequisites
To run these samples you must have setup an Azure AD B2C tenant and created an application that is configured to use the Authorization Code Flow with a user flow that allows a user to sign in. Which we go through in the post above.

You can find the *tenant domain name* on the overview of the B2C tenant. *ClientID* (Application ID) and *TenantId* (Directory ID) can be found under the overview of the application that you've registered.

## Razor Pages or MVC appsettings.json
Update the *appsettings.json* file and fill in the required details.

```javascript
"AzureAdB2C": {
    "Instance": "https://{tenant_domain_name}.b2clogin.com",
    "Domain": "{tenant_domain_name}.onmicrosoft.com",
    "TenantId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    "ClientId": "{client_id}",
    "SignUpSignInPolicyId": "B2C_1_signup_signin",
    "CallbackPath": "/signin-oidc",
    "ResponseType": "code",
    "UsePkce": true,
    "Scope": [ "openid", "{client_id}" ]
  },
```

Example configuration:
```javascript
"AzureAdB2C": {
    "Instance": "https://contoso.b2clogin.com",
    "Domain": "contoso.onmicrosoft.com",
    "TenantId": "f9be029f-b4c4-4b49-adf8-63717b57676c",
    "ClientId": "cd14e98c-72c3-40ce-99e1-28f4ed4cc26e",
    "SignUpSignInPolicyId": "B2C_1_signup_signin",
    "CallbackPath": "/signin-oidc",
    "ResponseType": "code",
    "UsePkce": true,
    "Scope": [ "openid", "cd14e98c-72c3-40ce-99e1-28f4ed4cc26e" ]
  },
```

## Web Api appsettings.json
```javascript
"AzureAdB2C": {
    "Instance": "https://{tenant_domain_name}.b2clogin.com",
    "Domain": "{tenant_domain_name}.onmicrosoft.com",
    "TenantId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    "ClientId": "{client_id}",
    "SignUpSignInPolicyId": "B2C_1_signup_signin",
    "Scope": [ "openid", "{client_id}" ],
    "AllowWebApiToBeAuthorizedByACL": true
},
```

Enjoy!