# WEGnology Connected Product Foundation

The [WEGnology Connected Product Foundation](https://~exportplaceholderid-docs-url~/cpf/overview/) (WCPF) is a prebuilt and production-ready template that significantly reduces the development time and complexity for your WEGnology applications. The WCPF provides a wide variety of out-of-the-box functionality required by most IoT products and services. This includes:

* Multitenancy
* User Management
* Device Management
* Data Visualization
* Event Management
* White Labeling

## Setup

This template creates a ready-to-use application with example devices, recipes, customers, sites, and users. This template also includes a data simulation workflow and a workflow that generates events based on the simulated data. To begin using the WCPF, the following setup steps are required:

1. Set a password for the WCPF's system admin. Navigate to **User and Groups** using the left navigation. Click the `system-admin@example.com` user from the list. Click the **Change Password?** checkbox and provide a secure password.
1. Enable the **Simulator** and **Check Thresholds** workflows. The simulation workflow replays device data from the `TurbineEngine.csv` file once a minute and records that data to the example Turbofan devices.
1. Set a secure value for the `cpf-jwt-password-reset-secret` [Application Global](https://~exportplaceholderid-docs-url~/applications/overview/#application-globals). This secret is used to sign tokens as part of the forgot password process.

The WCPF can now be accessed using your application’s default [Experience Slug](https://~exportplaceholderid-docs-url~/experiences/domains/#experience-slugs) (e.g. `<YOUR_APPLICATION_ID>.wnology.io`). Once you navigate to that URL with your browser, you’ll automatically be redirected to the WCPF’s log in page (/login) where you can login using your system admin's email and password.

For more details, please review the [WCPF User Guide](https://~exportplaceholderid-docs-url~/cpf/user-guide/).

## License

Copyright &copy; 2023 WEGnology. All rights reserved.