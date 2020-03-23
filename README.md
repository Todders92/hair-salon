# Hair Salon
#### March 20 2020

ASP.NET core MVC application using Entity Framework Core and MySQL for a Hair Salon Manager website. This appilication allows the user to fill out forms to keep track of stylists and clients associated with stylists

### Prerequisites

1. _Net Core SDK, install instructions can be found [here](https://www.learnhowtoprogram.com/c-and-net/getting-started-with-c/installing-c-and-net)_
2. _dotnet script, install instructions can be found [here](https://www.learnhowtoprogram.com/c-and-net/getting-started-with-c/installing-dotnet-script)_


### Installing

1. Clone the repository:
    ```
    git clone https://github.com/todders92/HairSalon
    ```
2. Change directories into the project working directory:
    ```
    cd HairSalon/HairSalon
    ```
3. Restore all dependencies:
    ```
    dotnet restore
    ```

#### Database Setup

4. Run the following commands in MySQL to setup this project Database
    ```
    CREATE DATABASE `todd_walraven`;
    USE `todd_walraven`;
    CREATE TABLE `stylists` (
        `StylistId` int NOT NULL AUTO_INCREMENT,
        `Name` varchar(255) DEFAULT NULL,
        `Specialty` varchar(255) DEFAULT NULL,
        PRIMARY KEY (`StylistId`)
    );
    CREATE TABLE `clients` (
        `ClientId` int NOT NULL AUTO_INCREMENT,
        `Name` varchar(255) DEFAULT NULL,
        `StylistId` int DEFAULT '0',
        PRIMARY KEY (`ClientId`)
    );
    ```
5. Compile and Run code:
    ```
    dotnet run
    ```
6. Open the locally hosted server in your preferred web browser:
    ```
    start http://localhost:5000
    ```


### BDD Specifications

|Behavior|Input|Output|
|:-:|:-:|:-:|
|User visits main page, user can click a link to stlylists page|visits '/'|Redirect to '/stylists'|
|User clicks 'Add stylist' button, redirect to New Stylist form|clicks 'Add stylist'|Redirect to '/stylists/new' and show New Stylist form|
|User clicks 'Submit' on New Stylist form, add new stylist to DB and redirect to Index route of Stylists|clicks 'submit' on New Stylist form|**Create new Stylist in DB**, Redirect to '/stylists'|
|User clicks on a stylist in the Index route of Stylists, show details of that stylist|clicks on 'Kris' (id = 2)|Redirect to '/stylists/2', show all details of Kris|
|User clicks 'Add Client' button, redirect to New Client form|clicks 'Add client'|Redirect to '/stylists/{id}/clients/new' and show New Client form|
|User clicks 'Submit' on New Client form, add new client to DB and redirect to Details route of Stylist|clicks 'submit' on New Client form|**Create new Client in DB**, Redirect to '/stylists/{id}'|
|User clicks on a client in the Details route of a specific stylist, show details of that client|clicks on 'Ross' (id = 4)|Redirec to '/stylists/{id}/clients/4', show all details of Ross|
|User clicks 'Delete' button on a Stylist in the Index page of Stylists, delete specific stylist and redirect to Index|clicks 'Delete'|**Delete stylist from DB**, redirect to '/stylists'|
|User clicks 'Edit' button on a Stylist in the Details page, Redirect to Edit form for specific Stylist.|clicks 'Edit'|Redirect to '/stylists/{id}/edit', show Stylist Edit form|
|User clicks 'Submit' button on Stylist edit form, Update details of Stylist in DB and redirect to Details of Stylist|clicks 'submit'|**Update Stylist in DB**, redirect to '/stylists/{id}'|


## Technologies Used

* C#
* ASP.NET core MVC 2.2
* Entity Framework Core
* MySQL/MySQL Workbench
* RESTful Routing
* CRUD Functionality
* Git

## Authors

* **Todd Walraven** - (https://github.com/todders92)

## License

Licensed under the MIT license.

&copy; 2020 - Todd Walraven