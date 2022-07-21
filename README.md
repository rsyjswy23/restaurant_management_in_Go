# restaurant_management_in_Go

This backend restaurant management system consists of 6 services:
* __User Service:__ user authentication & authorization using JWT.
* __Food Service:__ get, create, update food item.
* __Menu Service:__ get, create, update menu.
* __Order Service:__ get, create, update order.
* __Invoice Service:__ get, create, update invoice. 
* __Table Service:__ get, create, update table.

## Tech Stack & Tools:
* Go 
* Gin web framework
* MongoDB
* JWT 
* Postman

## Demo:
User Signup:

![Screen_Recording_2022-07-20_at_4_41_23_PM_AdobeExpress](https://user-images.githubusercontent.com/101481587/180126180-7dd43c96-ccf8-4b4a-b4e2-643ab5ae3dce.gif)

User Login, and generate JWT:

![Screen_Recording_2022-07-20_at_4_41_23_PM_AdobeExpress copy](https://user-images.githubusercontent.com/101481587/180126438-1a6a8489-b224-419b-a7bc-5735515c1509.gif)

With a valid JWT, user can create food item.

![Screen_Recording_2022-07-20_at_4_41_23_PM_AdobeExpress copy 2](https://user-images.githubusercontent.com/101481587/180127413-c9602305-3bac-4a46-8019-a0310be40eda.gif)

User can view all food items.

![Screen_Recording_2022-07-20_at_4_41_23_PM_AdobeExpress copy 3](https://user-images.githubusercontent.com/101481587/180127577-85e7862a-cc5c-4b8c-8210-18ba9a5f0cc3.gif)



## APIs
### User Service:
  #### User Signup: <http://localhost:8000/users/signup>
  POST request:
  ```
  {
    "first_name": "May",
    "last_name" : "May",
    "Password": "may455",
    "Email": "may455@gmail.com",
    "Phone": "45555",
    "User_type": "ADMIN"
  }
  ```
  response:
  ```
  {
    "InsertedID": "62d892b1b6521244067072cd"
  }
  ```
  #### User Login: <http://localhost:8000/users/login>
  POST request:
  ```
  {
    "Password": "may455",
    "Email": "may455@gmail.com"
  }
  ```
  response:
  ```
  {
    "ID": "62d892b1b6521244067072cd",
    "first_name": "May",
    "last_name": "May",
    "Password": "$2a$14$wl9skqJzUT4MiKR0KS6xPOFefL7hk6wBxBNVTanWxfxCXNnM5H8re",
    "email": "may455@gmail.com",
    "avatar": null,
    "phone": "45555",
    "token":  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJFbWFpbCI6Im1heTQ1NUBnbWFpbC5jb20iLCJGaXJzdF9uYW1lIjoiTWF5IiwiTGFzdF9uYW1lIjoiTWF5IiwiVWlkIjoiNjJkODkyYjFiNjUyMTI0NDA2NzA3MmNkIiwiZXhwIjoxNjU4NDQ2OTEwfQ.hgyHJwYlSu630Z0zEQ2C24EV7L2KHIN9vZ2fmm5FfkQ",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJFbWFpbCI6IiIsIkZpcnN0X25hbWUiOiIiLCJMYXN0X25hbWUiOiIiLCJVaWQiOiIiLCJleHAiOjE2NTg5NjUzMTB9.eSrEPnhz5ZkBx-mnzzRN0A02dkIGz7MkSMGA-0MPtxw",
    "created_at": "2022-07-20T23:41:37Z",
    "updated_at": "2022-07-20T23:41:50Z",
    "user_id": "62d892b1b6521244067072cd"
  }
  ```  
### Menu Service: 
#### Add Menu: <http://localhost:8000/menu>
  POST request:
  ```
  {
    "Name": "vegan menu",
    "Category": "food"
  }
  ```
  response:
  ```
  {
    "InsertedID": "62d88a460b4f17afd7defeb9"
  }
  ```
 #### Get Menu: <http://localhost:8000/menu>
   GET response:
  ```
  [
    {
        "_id": "62d87a150b4f17afd7defeb7",
        "category": "food",
        "created_at": "2022-07-20T14:56:37-07:00",
        "end_date": null,
        "menu_id": "62d87a150b4f17afd7defeb7",
        "name": "vegan menu",
        "start_date": null,
        "updated_at": "2022-07-20T14:56:37-07:00"
    },
    {
        "_id": "62d88a460b4f17afd7defeb9",
        "category": "food",
        "created_at": "2022-07-20T16:05:42-07:00",
        "end_date": null,
        "menu_id": "62d88a460b4f17afd7defeb9",
        "name": "meat menu",
        "start_date": null,
        "updated_at": "2022-07-20T16:05:42-07:00"
    }
  ]
  ``` 
### Food Service:
#### Add Food Item: <http://localhost:8000/food>
  POST request:
  ```
  {
    "Name" : "spicy beef",
    "Price": 25,
    "Food_image": "https://i0.wp.com/chefsavvy.com/wp-content/uploads/super-easy-sesame-beef.jpg?resize=665%2C876&ssl=1",
    "Menu_id": "62d88a460b4f17afd7defeb9"
  }
  ```
  response:
  ```
  {
    "InsertedID": "62d892fbb6521244067072ce"
  }
  ```
#### Get Food Item: <http://localhost:8000/food>
  GET response:
  ```
  {
    "food_items": [
        {
            "_id": "62d87b150b4f17afd7defeb8",
            "created_at": "2022-07-20T15:00:53-07:00",
            "food_id": "62d87b150b4f17afd7defeb8",
            "food_image": "https://saladswithanastasia.com/wp-content/uploads/2021/12/green-radish-salad-hero.webp",
            "menu_id": "62d87a150b4f17afd7defeb7",
            "name": "rainbow salad",
            "price": 18,
            "updated_at": "2022-07-20T15:00:53-07:00"
        },
        {
            "_id": "62d88aa30b4f17afd7defeba",
            "created_at": "2022-07-20T16:07:15-07:00",
            "food_id": "62d88aa30b4f17afd7defeba",
            "food_image": "https://www.modernhoney.com/wp-content/uploads/2018/01/Chinese-Orange-Chicken-2.jpg",
            "menu_id": "62d88a460b4f17afd7defeb9",
            "name": "orange chicken",
            "price": 25,
            "updated_at": "2022-07-20T16:07:15-07:00"
        },
        {
            "_id": "62d892fbb6521244067072ce",
            "created_at": "2022-07-20T16:42:51-07:00",
            "food_id": "62d892fbb6521244067072ce",
            "food_image": "https://i0.wp.com/chefsavvy.com/wp-content/uploads/super-easy-sesame-beef.jpg?resize=665%2C876&ssl=1",
            "menu_id": "62d88a460b4f17afd7defeb9",
            "name": "spicy beef",
            "price": 25,
            "updated_at": "2022-07-20T16:42:51-07:00"
        }
    ],
    "total_count": 3
  }
  ```

## MongoDB Schema & Data Models:



## Implementaton Details:
### About Gin:

### About MongoDB:

### About JWT:



