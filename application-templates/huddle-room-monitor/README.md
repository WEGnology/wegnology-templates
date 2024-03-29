# Huddle Room Monitoring Template
This template reduces wasted time searching for huddle rooms by providing a real-time space availability and utilization application. Employees can log in and see a floor plan containing live huddle room availability. Managers can log in to see both live and historical utilization data.

## Key Components
* Sample huddle rooms with occupancy monitoring.
* Aggregated occupancy data by floor and building.
* Access control through user roles.

## Setup
Enable the [Simulate Rooms](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationHuddleRoomMonitor~/workflows/~exportplaceholderid-flow-simulateRooms~/develop) workflow.

## Room Simulation
When the [Simulate Rooms](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationHuddleRoomMonitor~/workflows/~exportplaceholderid-flow-simulateRooms~/develop) workflow is enabled, occupancy data will be simulated for each huddle room every two minutes.

On each iteration, there's a small chance a room will become occupied. Rooms will only become occupied during business hours (8:00a - 5:00p EST). Once occupied, the room will remain occupied for a random amount of time between 15 and 90 minutes.

To change the working hours or the time zone, edit the [Time Range Node](https://docs.app.wnology.io/workflows/logic/time-range/) that can be found in the [Simulate Rooms](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationHuddleRoomMonitor~/workflows/~exportplaceholderid-flow-simulateRooms~/develop) workflow.

## Dashboards
This template includes two dashboards: one for employees and one for facilities managers.

### Available Rooms Dashboard
The [Available Rooms](https://console.app.wnology.io/dashboards/~exportplaceholderid-dashboard-availableRooms~) dashboard provides live availability for each of this template's three huddle rooms.

### Occupancy History Dashboard
The [Occupancy History](https://console.app.wnology.io/dashboards/~exportplaceholderid-dashboard-occupancyHistory~) dashboard provides historical usage data for this template's three huddle rooms.

## Experience
This template's [Experience](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationHuddleRoomMonitor~/experience/versions/develop) provides an authenticated portal where employees and managers can view this application's dashboards. To distinguish between an employee and a manager, each user has a `role` tag that is set to either `employee` or `manager`.

### Users
This experience has two example users:
* `employee@example.com`: Represents an employee.
* `manager@example.com`: Represents a manager.

The password for both users is `qwerty123`. Users can be modified, added, or removed by navigating to the experience's [Users & Groups](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationHuddleRoomMonitor~/experience/users) page.

## Resources
* [Image Overlay Block](https://docs.app.wnology.io/devices/overview/)
* [System Devices](https://docs.app.wnology.io/devices/systems/)

---

This template was created by WEGnology. For license details, or to submit feature requests or bugs, visit the [GitHub repository](https://github.com/WEGnology/wegnology-templates). If you have general questions or comments, let us know on the [WEGnology Forums](https://forums.app.wnology.io).

Copyright (c) 2023 WEGnology.