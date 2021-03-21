# BigCommerce Auth0 OpenID Connect (OIDC) Customer Login Middleware

This is a simple Express example (ie, not production-ready) of how Auth0 OIDC can be used to create and authenticate users into a Stencil BigCommerce Storefront using the Customer Login API that accepts a JWT.

This example uses only Google login and creates the user in BigCommerce if they do not already exist. Further work required to add additional.

Uses [Auth0's Open ID Connect](https://github.com/auth0/express-openid-connect)

## Setup 

Copy .env.template to .env ander complete details:

    ISSUER_BASE_URL= {the base domain from Auth0}
    CLIENT_ID= {the client ID from the app created in Auth0}
    BASE_URL= {URL of the middleware}
    SECRET= {min 32 char secret}

    TARGET_DOMAIN= {base URL of BC store (no trailing slash)}
    LOGOUT_TARGET_URL= {logout URL in BC store eg, TARGET_DOMAIN/login.php?action=logout}

    PORT=4000 

    # BigCommerce API credentials
    BC_STORE_ID=
    BC_ACCESS_TOKEN=
    BC_CLIENT_ID=
    BC_CLIENT_SECRET=

### Auth0 Setup

Create a new account and application. Configure Applicaiton URIs:

#### Allowed Callback URLs : 

    eg http://localhost:4000/callback

#### Allowed Logout URLs : 

    eg {TARGET_DOMAIN}/login.php?action=logout

### Stencil Setup

- Configure Login links to point to {BASE_URL} above. This will login/register the user, login via JWT
- Configure Logout links to point to {BASE_URL}/logout, it will redirect back to {LOGOUT_TARGET_URL}. This will logout the user from Auth0 then redirect to the logout page in Stencil to logout there also
- Further work required to control register/login/logout flow

