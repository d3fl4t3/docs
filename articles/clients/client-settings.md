---
description: Describes the differences between the Auth0 Client types and what they mean when it comes to settings
---

# Client Settings

When creating an Auth0 Client, you'll be asked to indicate the *type* of Client you want to create. 

![Window for selecting client type](/media/articles/clients/create-clients.png)

You can choose from one of four options:

* **Native**: used for desktop or mobile apps that run natively on the the device
* **Single Page Web Applications**: apps with a JavaScript front-end utilizing an API
* **Regular Web Applications**: traditional web apps with refresh behavior
* **Non Interactive Clients**: CLIs, daemons, or services running on the back-end

## Settings

By default, the [settings](${manage_url}/#/clients/${account.clientId}/settings) include the following:


- **Name**: The name of your client. This information is editable and you will see in the portal, emails, logs, and so on.

- **Domain**: Your Auth0 account name. Note that the domain name is chosen when you create a new Auth0 account and cannot be changed. If you need a different one you have to register for a new account by selecting *New Account* at the top right menu.

- **Client ID**: The unique identifier for your client. This is the ID you will use with when configuring authentication with Auth0. It is generated by the system when you create a new client and it cannot be modified.

- **Client Secret**: A string used to sign and validate `id_tokens` for authentication flows and to gain access to select Auth0 API endpoints. By default, the value is hidden, so check the **Reveal Client Secret** box to see this value.

  ::: warning
  While the Client ID is considered public information, the Client Secret **must be kept confidential**. If anyone can access your Client Secret they can issue  tokens and access resources they shouldn't.
  :::

- **Description**: A free-text description of the Client's purpose with a maximum of 140 characters.

- **Client Type**: The type of client you are implementing. Depending on which you choose, the available settings differ to show you only the settings applicable to your Client Type. You can change this value at any time by selecting one of the following: Native, Non Interactive Client, Regular Web Application, or Single Page Application.

- **Token Endpoint Authentication Method**: Defines the requested authentication method for the token endpoint. Possible values are `None` (public client without a client secret), `Post` (client uses HTTP POST parameters) or `Basic` (client uses HTTP Basic). This setting is only available for clients of type **Non Interactive Clients** or **Regular Web Page Applications**

- **Allowed Callback URLs**: Set of URLs to which Auth0 is allowed to redirect the users after they authenticate. You can specify multiple valid URLs by comma-separating them (typically to handle different environments like QA or testing). You can use the star symbol as a wildcard for subdomains (`*.google.com`). Make sure to specify the protocol, `http://` or `https://`, otherwise the callback may fail in some cases.

- **Allowed Logout URLs**: After a user logs out from Auth0 you can redirect them with the `returnTo` query parameter. The URL that you use in `returnTo` must be listed here. You can specify multiple valid URLs by comma-separating them. You can use the star symbol as a wildcard for subdomains (`*.google.com`). Notice that querystrings and hash information are not taking into account when validating these URLs. Read more about this at: [Logout](/logout).

- **Allowed Origins (CORS)**: Set of URLs that will be allowed to make requests from JavaScript to Auth0 API (typically used with CORS). This prevents same-origin policy errors when using Auth0 from within a web browser. By default, all your callback URLs will be allowed. This field allows you to enter other origins if you need to. You can specify multiple valid URLs by comma-separating them. You can use the star symbol as a wildcard for subdomains (`*.google.com`). Notice that querystrings and hash information are not taking into account when validating these URLs.

- **JWT Expiration (seconds)**: The amount of time (in seconds) before the Auth0 id_token expires. The default value is `36000`, which maps to 10 hours.

- **Use Auth0 instead of the IdP to do Single Sign On**: If enabled, this setting prevents Auth0 from redirecting authenticated users with valid sessions to the identity provider (such as Facebook, ADFS, and so on).

![Client Settings Page](/media/articles/clients/settings.png)

### Advanced Settings

The **Advanced Settings** section allows you to:

* Manage or add Client Metadata, Mobile, OAuth, and WS-Federation settings 
* Obtain certificates and token endpoint information
* Set the grant type(s) for the Client

![Advanced Client Settings Page](/media/articles/clients/advanced-settings.png)

Regardless of which Client Type you choose, this area is the same. The exception is for Clients of type **Non Interactive Clients** or **Regular Web Page Applications**; both, under the OAuth tab, show a **Trust Token Endpoint IP Header** setting. By enabling this setting, the `auth0-forwarded-for` is set as trusted and used as a source of end user IP information for protection against brute-force attacks on the token endpoint.
