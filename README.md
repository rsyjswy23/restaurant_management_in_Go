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
* Gin web framework (routes-controllers-models)
* MongoDB (aggregaton pipeline)
* JWT (RSA signing method RS256)

## MongoDB Schema & Data Models:
![Untitled Diagram drawio](https://user-images.githubusercontent.com/101481587/180132592-9ea68fc6-bc53-4f32-aa32-27c0b1692b96.svg)

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

## Implementaton Details:
### About Gin: [docs] (https://gin-gonic.com/docs/quickstart/)
It's fast and has minimal memory allocation which can reduce the amount of runtime overhead from garbage collection. 
Example of creating Gin router in ```main.go```:
  ```
  func main() {
	  port := os.Getenv("PORT")
	  if port == "" {
		  port = "8000"
	  }
	  router := gin.New()
	  router.Use(gin.Logger())
	  routes.FoodRoutes(router)
	  router.Run(":" + port)
  }
  ```
Extract variables from route name & URL parameters in ```foodRouter.go``` & ```foodController.go```
  ```
  func FoodRoutes(incomingRoutes *gin.Engine) {
	  incomingRoutes.GET("/foods", controller.GetFoods()) 
	  incomingRoutes.GET("/foods/:food_id", controller.GetFood()) 
	  incomingRoutes.POST("/foods", controller.CreateFood())
	  incomingRoutes.PATCH("/foods/:food_id", controller.UpdateFood())
  }
  ```
  ```
  func GetFood() gin.HandlerFunc {
	return func(c *gin.Context) {
		var ctx, cancel = context.WithTimeout(context.Background(), 100*time.Second)
		foodId := c.Param("food_id")
		var food models.Food
		// need .Decode(&food) translate data from Mongodb to golang
		err := foodCollection.FindOne(ctx, bson.M{"food_id": foodId}).Decode(&food)
		defer cancel()
		if err != nil {
			c.JSON(http.StatusInternalServerError, gin.H{"error": "error occured while fetching the food item"})
		}
		c.JSON(http.StatusOK, food)
	}
}
  ```
### About MongoDB:
- [Aggregation Pipeline](https://www.mongodb.com/docs/manual/core/aggregation-pipeline/): 
![Screen Shot 2022-07-18 at 5 06 13 PM](https://user-images.githubusercontent.com/101481587/180132440-8692d631-5f39-4b9d-8838-40485f5d8f7b.jpg)
- [Aggregation Operator](https://www.mongodb.com/docs/manual/reference/operator/aggregation/): $sum, $push, $slice,
- In Mongodb, [$lookup](https://www.mongodb.com/docs/manual/reference/operator/aggregation/lookup/) is similar to join operation in SQL. On ```OrderItemController.go```, there are 3 $lookup & [$unwind](https://www.mongodb.com/docs/manual/reference/operator/aggregation/unwind/) to perform:
    1. join orderItem & food using food_id to lookup food record
    2. join orderItem & order using order_id to lookup order record
    3. join order & table using table_id to lookup table record
  ```
  func ItemsByOrder(id string) (OrderItems []primitive.M, err error) {
    var ctx, cancel = context.WithTimeout(context.Background(), 100*time.Second)
    // 1st lookup
    matchStage := bson.D{{"$match", bson.D{{"order_id", id}}}}
    lookupStage := bson.D{{"$lookup", bson.D{{"from", "food"}, {"localField", "food_id"}, {"foreignField", "food_id"}, {"as", "food"}}}}
    unwindStage := bson.D{{"$unwind", bson.D{{"path", "$food"}, {"preserveNullAndEmptyArrays", true}}}}
    // 2nd lookup
    lookupOrderStage := bson.D{{"$lookup", bson.D{{"from", "order"}, {"localField", "order_id"}, {"foreignField", "order_id"}, {"as", "order"}}}}
    unwindOrderStage := bson.D{{"$unwind", bson.D{{"path", "$order"}, {"preserveNullAndEmptyArrays", true}}}}
    // 3th lookup
    lookupTableStage := bson.D{{"$lookup", bson.D{{"from", "table"}, {"localField", "order.table_id"}, {"foreignField", "table_id"}, {"as", "table"}}}}
    unwindTableStage := bson.D{{"$unwind", bson.D{{"path", "$table"}, {"preserveNullAndEmptyArrays", true}}}}

    projectStage := bson.D{
      {"$project", bson.D{
        {"id", 0},
        {"amount", "$food.price"},
        {"total_count", 1},
        {"food_name", "$food.name"},
        {"food_image", "$food.food_image"},
        {"table_number", "$table.table_number"},
        {"table_id", "$table.table_id"},
        {"order_id", "$order.order_id"},
        {"price", "$food.price"},
        {"quantity", 1},
      }}}
    groupStage := bson.D{{"$group", bson.D{{"_id", bson.D{{"order_id", "$order_id"}, {"table_id", "$table_id"}, {"table_number", "$table_number"}}}, {"payment_due", bson.D{{"$sum", "$amount"}}}, {"total_count", bson.D{{"$sum", 1}}}, {"order_items", bson.D{{"$push", "$$ROOT"}}}}}}
    projectStage2 := bson.D{
      {"$project", bson.D{
        {"id", 0},
        {"payment_due", 1},
        {"total_count", 1},
        {"table_number", "$_id.table_number"},
        {"order_items", 1},
      }}}
    result, err := orderItemCollection.Aggregate(ctx, mongo.Pipeline{
      matchStage,
      lookupStage,
      unwindStage,
      lookupOrderStage,
      unwindOrderStage,
      lookupTableStage,
      unwindTableStage,
      projectStage,
      groupStage,
      projectStage2})
    if err != nil {
      panic(err)
    }
    if err = result.All(ctx, &OrderItems); err != nil {
      panic(err)
    }
    defer cancel()
    return OrderItems, err
  }
  ```
### About JWT: [docs](https://www.sohamkamani.com/golang/jwt-authentication/)
<img src="https://user-images.githubusercontent.com/101481587/180132516-8a55614a-7440-4b97-97dc-9b0f34f6f79a.svg" width="500" height="600">

