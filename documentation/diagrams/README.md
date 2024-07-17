# GDTwins

## Documentation
TODO

## Table of contents
- [Context Diagram](#context-diagram)
- [Use-cases](#use-cases)
- [Activities](#activities)
- [Sequences](#sequences)
- [Interactions](#interactions)
- [Timing](#timing)
- [Components](#components)
- [Entities](#entities)
- [Classes](#classes)
- [States](#states)
- [Objects](#objects)
- [Packages](#packages)
- [Deployment](#deployment)
- [Kanban](#kanban)
- [Git Flow](#git-flow)
- [Wireframe](#wireframe)
- [Prototype](#prototype)

## Context-Diagram
TODO

![Context diagram for GDTwins.](./context.drawio.svg)

## Use-Cases
This section describes the main use-cases in our system.

![Use case diagram for GDTwins.](./usecase.drawio.svg)

There are three types of actors in human roles:
1. **Unregistred Modeller (A1)**: This actor expectation is to create a digital twin but has not yet registered on the GDTwins web application. For fullfilling his expectation he needs to register first.
2. **Registred Modeller (A2)**: This actor's expectation is to create a digital twin project with a digital map of the region, enhanced by digital objects, to gather feedback from citizens or inform them about future visions.
3. **Citizen (A3)**: This actor expectation to stay informed about new projects in the region, check them on the public website, and provide feedback on the types of objects to be used.

Use cases:
1. **Register using GDTwins creator (UC1)**: If a user wants to create a digital twin model, they must visit the UJEP web server with the GDTwins web app and register. Required information: email, password. After registration, the user can log in to the GDTwins web app, which is mandatory for all use cases involving the GDTwins web server.
2. **Create digital twin project (UC2)**: After logging in, the user can access the dashboard with all projects and create their first project. Later, they can check existing projects. A project serves as a placeholder for a digital twin map with objects and voting information from citizens.
3. **Create digital twin map (UC3)**: By creating a new empty project, the user can start building a digital twin. All digital twins are represented by a visual 3D map (digital twin map), which includes a base map and objects placed on it. This use case can only be performed after creating a project that will hold all the data and has a unique ID.
4. **Add base map (UC4)**: Through the GUI button and file explorer, the user can add a base map on which objects will be placed. Some base maps will be provided in the application for testing purposes.
5. **Add object to map (UC5)**: Through the GUI button and file explorer, the user can add a 3D object, which will be listed in the objects list and can be placed on the base map.
6. **Create object variants (UC6)**: 3D objects can be grouped together to create variants. One variant is the default, which is shown in the exported visualization of the digital twin map. Citizens can choose other variants from the group to display on the digital twin map instead of the default one.
7. **Specify feedback (UC7)**: The registered modeler can specify the type of feedback allowed for each 3D object and the base map itself (e.g., voting on a scale, free text answers, like/dislike). This is configured for each object.
8. **Publish digital twin project (UC8)**: This action stores the digital project in the database and exports an iframe code for the registered modeler to use on their website to load the digital twin map visualization. This functionality can only be accessed after some work on the project has been done (e.g., adding a base map with at least one object; feedback collection is optional).
9. **Check citizen feedback report (UC9)**: After publishing the digital twin project, the registered modeler can check the collected feedback on objects and the base map (representing the digital twin map as a whole). They can view statistics with simple visualizations and export them to a CSV file.
10. **Delete digital twin project (UC10)**: If the registered modeler no longer wishes to gather feedback or wants to close the digital twin map visualization to the public, they can delete the project. All files and feedback will be removed from the database.
11. **Include digital twin map to website (UC11)**: After obtaining the iframe code, the registered modeler can (possibly with the help of an IT specialist) access the code of the public website where they want to place the digital twin map and paste it into the appropriate place in the HTML code or web component. After pasting the iframe code, the website should be able to load the digital twin map from the GDTwins web server and render it for visiting citizens.
12. **View digital twin map (UC12)**: Citizens can load the website of the public server (e.g., a regional or municipal website) and view the interactive visualization of the digital twin map. They can rotate, zoom, and pan within the map.
13. **Provide opinion on objects by voting (UC13)**: When a citizen clicks on an object, they can choose variants of objects from the same group and provide feedback (the feedback scheme is defined by the registered modeler). They can also provide feedback on the digital twin map as a whole. Feedback is posted through a REST API to the GDTwins server, paired with digital twin projects by ID, and saved.

## Activities
TODO

## Sequences
TODO

## Interactions
TODO

## Timing
TODO

## Components
TODO

## Entities
TODO

## Classes
TODO

## States
TODO

## Objects
TODO

## Packages
TODO

## Deployment

This section describes the deployment strategy for our system.

![Deployment diagram for GDTwins.](./deployment.drawio.svg)

GDTwin web application will be hosted on UJEP server inside a virtual machine instance. Application will be divided to containerized microservices in Docker containers and running as a composed services via Docker Compose. 

List of containers:
1. Nginx: serves as reverse proxy for application, enhances security.
2. Django: hosts python webapp with all the logic. Hosts webgl build of unity engine application.
3. Postgres: servers Django container for storing data about digital twin maps and feedback to its objects.

Citizens can contact GDTwin app through https requests on port 80 on their public webservers. Upon opening specified webpage on public webserver (GET method in https request) the Webgl build is send from GDTwin web app to public webserver. Feedback interaction in deployed build on public webserver sends feedback data through REST API on GDTwin webapp where it will be stored in Postgres database. Database data are stored with virtual Docker volume that holds database data and configuration data.

![Profile diagram for IT operations for deployment diagram.](./profile-deployment.drawio.svg)

Deployment diagram will be used mainly by IT operations department of UJEP. Profile diagram for own stereotypes was created with attributes of custom made stereotypes. These attributes are key attributes that needs to be checked and optimized by IT operations department and developers.

## Kanban
TODO

## Git-Flow
TODO

## Wireframe

## Prototype
TODO