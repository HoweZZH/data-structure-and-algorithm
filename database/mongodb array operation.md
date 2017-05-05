http://www.javahotchocolate.com/notes/mongodb-crud.html
```json
// a json file instance
{
    "_id" : ObjectId("58fe900477c8d1afd3bdbf95"),
    "word" : "mvc",
    "urls" : [ 
          "http://stackoverflow.com/questions/43580834/creating-sms-gateway-using-asp-net-mvc", 
        "http://stackoverflow.com/questions/43580390/c-sharp-mvc-redirecttoaction-and-browser-navigation-buttons"
    ]
}
```
**push a element into array**
```java
//query obj that need update
DBObject oneQuery = occurence.findOne(new BasicDBObject("word", "mvc"));

//martch parameter
BasicDBObject match = new BasicDBObject();
match.put("_id", oneQuery.get("_id"));

//update parameter
BasicDBObject newUrl = new BasicDBObject();
newUrl.put("urls", url);
BasicDBObject update = new BasicDBObject();
update.put("$push", newUrl);  //use $push to push new url to url array

//update
collection.update(match, update);
```
