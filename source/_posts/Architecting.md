---
title: Architecting
date: 2021-02-03 19:43:47
tags: [Javascript]
---
## Architecting an Express application in the MVC paradigm

Express doesn't enforce an opinion on how you should structure the Model, View, and Controller (MVC) modules of your application, or whether you should follow any kind of MVC paradigm at all.
The controller acceps inputs or requests from the user, converting that intocommands sent to the model.
The model contains data, logic, and rules which the application operatates.
The view is used to present the results to the user. 

As we learned in the previous chapter, the blank application created by the Express generator provides two aspects of the MVC model:

- The views directory contains template files, controlling the display portion, corresponding to the view.
- The routes directory contains code implementing the URLs recognized by the application and coordinates the data manipulation required to generate the response to each URL. 
- This corresponds to the controller.

The approach we'll use is to create a **models** directory as a sibling of the **views** and routes directories.
The **models** directory will hold modules to handle data storage and other code that we might call business logic.
The API of the modules in the **models** directory will provide functions to create, read, update, or delete data items-a **Create, Read, Update, and Delete/Destroy(CRUD)** model
