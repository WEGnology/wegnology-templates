# Module (Users and Groups)

The **Module (Users and Groups)** is the means by which a web interface can be built for users to interact with what has been developed on the platform. This module provides some tools that were used in this model to deliver a user control application with a login system, account registration, and deletion, permissions based on user groups, navigation between pages, and much more.

## Description

This model is a complete user control application. The components *page*, *component*, *layout*, *endpoint*, and *experience workflows* were used to control user actions in the application, restricting access for common users to the home page and allowing actions such as user registration and deletion only for users with administrator permissions, i.e., those belonging to the "adm" group.

## Key Components

- **LAYOUT** *layout-base*:
  A *layout* provides components that need to be present on different pages, saving the effort of rewriting code;
- **PAGE** *Login*:
  This is the initial page of the application, where the user enters their credentials to be authenticated by the WORKFLOW *Endpoint/login*;
- **PAGE** *Home*:
  This page only contains the DASHBOARD *Dashboard* and can be accessed by any authenticated user;
- **PAGE** *Create Account*:
  This page contains a user registration form. When the "confirm registration" button is clicked, the WORKFLOW *POST api/v2/user* validates the entered data before sending a configuration email. Only users in the "adm" group can access this page;
- **PAGE** *Delete Account*:
  This page displays a list of all application users. You can delete any user who is not in the "adm" group by clicking the "trash can." Once this action is performed, the user's information in the selected row is sent to the WORKFLOW *DELETE api/v1/user* to be removed from the application. Only users in the "adm" group can access this page;
- **COMPONENT** *js-imports*:
  A component that imports JS files necessary for some functionalities. It is important that all imports are saved in the application (in *Files*) and that this component is imported on all pages before the "script" tag;
- **COMPONENT** *js-notify*:
  A component that displays a custom notification with parameters defined by the user. It should be instantiated after the "js-import" component and only on pages where it is necessary to show a notification;
- **ENDPOINT** *GET/*:
  This address redirects the user to the *login* page when not authenticated. Otherwise, it redirects them to the home page;
- **ENDPOINT** *POST/login*:
  The path for sending credentials for authentication. This endpoint is invoked by the *login* screen to send the entered credentials to the WORKFLOW *Endpoint/login* for authentication;
- **ENDPOINT** *DELETE/delete-account*:
  This address sends the data of the user from the selected row on the *Delete Account* PAGE to the WORKFLOW *DELETE/api/v1/user*, which then removes the user from the application;
- **WORKFLOW** *Endpoint/login*:
  Triggered when the user accesses the "/" endpoint and when credentials are sent from the *login* screen. It evaluates the access mode, checks if the provided credentials are valid, and redirects the user to the home screen if authenticated;
- **WORKFLOW** *POST/api/v2/user*:
  The first step in user registration. Triggered when sending registration data from the *Create Account* page, it validates if the user does not already exist and sends a confirmation email;
- **WORKFLOW** *GET/validate-email*:
  The second step in user registration. Triggered from the confirmation email, if the token is not expired, a new user is registered and can log in to the application;
- **WORKFLOW** *DELETE/api/v1/user*:
  Triggered when the user clicks the trash can. It evaluates the data of the user in the selected row and removes them from the application;
- **GROUP** *normal*:
  Users belonging to this group can only access the application's home page;
- **GROUP** *adm*:
  Users belonging to this group have access to all pages and can register and delete other users in the application;
- **DASHBOARD** *Dashboard*:
  Displayed on the *Home* PAGE, it contains charts with data from the *random-device* DEVICE that provides simulated values only to populate this dashboard;

## Configuration

1. Set a new password for the "admin" user:
   - Navigate to Experience *Users & Groups*;
   - Select the user "user@adm.com";
   - Select the "Change Password?" check-box;
   - Add a password and save the change.
2. To display values on the dashboard, it is necessary to force a value on the "random-device" device:
   - Navigate to *Devices*;
   - Select the "random-device" device;
   - Click "Device Actions" in the upper right corner;
   - Choose "Force State";
   - Select the "attribute" attribute, enter an integer value, and click "Force Report State."
3. Set the *slug* of your application to access it through your browser:
   - Navigate to *Experience Domains & Slugs*;
   - Click the green button with the text "Add";
   - Save the change by clicking "Create Slug";
   - Obtain the application link by clicking on the action button of your *slug* or go to *Experience Edit* and copy the link in the upper right corner.

After completing these configurations, you can access the application through your browser, and other users can be added from the registration screen. When sending the data of a new user, a confirmation email is sent to the provided address, and the registration is only confirmed when the user completes the confirmation.

## Auxiliary Documentation

- For more information about the *EXPERIENCE* module, refer to the platform documentation.

## About

This model is in version 1.0.0.

For any questions, we recommend using the [forum](https://forums.app.wnology.io/).

Copyright © 2023 WEG SA. All rights reserved.

Licensed under the MIT license.

[https://www.weg.net](https://www.weg.net)