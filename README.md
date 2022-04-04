# tour-project

##Backend
backend App for tourists

## Clone this repo
Please close this repo by running

``git clone https://github.com/Rosecollet1/Tour-Me.git ``

cd into the newly created project directory.

``cd Tour-Me``
## App system requirements
You need to install `node`, `npm` and `mysql` server to be able to run and use this app locally on your system.
Please refer to the official installation guides from the respective websites.
## Running the App
create a local `ormconfig.json` following the guide in `ormconfig.example.json`. This ensures your database connection configuration is set before the app can start.
### Then run the following in the current terminal
```
npm install
npm run start
```

### To create an admin user:
create a regular user with no role/permission through the frontend. Then run the code below that does the following:
 - to create a permission
 - to create a role
 - to make the created user with Id of 1 an admin
 
 ```
    create database if not exists tour;
    use tour;
    insert into role (id, name) VALUES (1, 'admin');
    insert into permission (id, name, roleId) VALUES (1, 'User:Delete', 1);
    INSERT INTO user_roles_role (userId, roleId) VALUES ( 1, 1 );
```

This will give the user with Id of 1 a permission to delete a user. The operation to delete a user is exposed on the API through an endpoint called 
`router.delete('/api/users', DeleteUser)`

##Frontend
### Installation
``
npm install
npm run dev
``
### Object Definitions
A sample user looks like the following

```angular2
{
    email: "conyia@gmail.com"
    firstName: "chidera"
    id: 1
    lastName: "onyia"
    roles: [{
        id: 1, 
        name: "admin", 
        permissions: [{
            id: 1, name: "User:Delete"
        }]
    }]
}
```