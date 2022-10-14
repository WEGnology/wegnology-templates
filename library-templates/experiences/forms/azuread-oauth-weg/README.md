# Oauth 2.0 (Microsoft)

This template demonstrates an example of how to include Google's social authentication method inside of an application. It includes:

- Endpoints
  - Home
  - Oauth Callback
  - User Summary
- Worflows
  - Oauth Callback
  - Oauth Sign in
- Pages
  - Login
  - User Summary
- Layout
  - Example Layout

## Dependencies

This component requires the use of [Twitter Bootstrap v4](https://getbootstrap.com/) as a CSS and JS framework.

## Getting Started

Before start using this template, keep in mind that some actions must be taken beforehand:

- Create credentials for your application at [Azure Active Directory](https://portal.azure.com) and setup the desired scopes and permissions that your app will need.
- Register the correct **Redirect URI** for your application being able to receive the user's information.
- Update the *Application Globals* with the **Client ID**, **Client Secret** generated from your credentials creation and the **hostname** of the application.

The main purpose of each one of the workflows contained in this template are briefly stated below:

- GET /oauth/signin: This workflow is only responsible to build the oauth authentication URL with proper params configuration and redirect the user to it when called.
- GET /oauth/callback/azuread: Callback workflow that will receive the user-related information from the identity provider. In this workflow you can develop business logic to decide to log the user in or create a new user if does not exists, for example.

### Setting Global Configuration

It’s best practice to use application globals to store application-wide configuration that may be used across multiple workflows, like phone numbers or API keys.
Application globals are a set of key/value pairs that are accessible inside of a workflow.

In this case, you can use them to store the **Client ID**, **Client Secret** and the application **hostname**. 

- Setup the **oauth** variable that will hold the credentials information as a JSON object:
```
{
    "microsoft": {
        "clientId": "<your-client-id>",
        "clientSecret": "<your-client-secret>"
    }
}
```
- Setup the **hostname** variable that will hold the host information of your application address as a string object (e.g: "my-application.staging.wnology.io"):
```
<application-hostname>
```
