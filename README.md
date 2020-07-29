# In-memory Distributed key-value store

### In-memory distributed key-value store design consists of 3 parts  Client, Server(Flask) and database(Redis)

### Client: Client is just a user who sends requests to set the key-values, fetch all the key-values in database. 

### The data stored it's persisted so that restarts of the application doesn't clear it , that one of the most power of redis.

### curl commands are used to send respective requests. Below are few examples.


## Dependencies:

* Python > 3.6
* Flask
* Redis
* platform tested on: **Ubuntu 20.04**


## To install dependencies run:

```
pip3 install flask
pip3 install redis
```

## To run the tests run:

```
python3 app_tests.py
```

## To run the application:

```
cd key-value-store-application/
export FLASK_APP=app.py
flask run
```

## API usage

* Set a value  
```
curl -H "Content-Type: application/json" -X PUT -d '{"value":"key","value2":500}' http://127.0.0.1:5000/keys
```
* Set a value with expire time
```
curl -H "Content-Type: application/json" -X PUT -d '{"value3":"key3","value5":100}' http://127.0.0.1:5000/keys?expire_in=50
```

* Get all values  
```
curl --request GET  http://127.0.0.1:5000/keys
```
* Get specific value
```
curl --request GET  http://127.0.0.1:5000/keys/<id>/
```

* Getting all values with filter
```
curl --request GET  http://127.0.0.1:5000/keys?filter=value$
```

* Check if a value exists
```
curl -I http://127.0.0.1:5000/keys/<id>/
```

* Delete specific key
```
curl --request DELETE http://127.0.0.1:5000/keys/<id>/
```
* Delete all keys
```
curl --request DELETE http://127.0.0.1:5000/keys
```