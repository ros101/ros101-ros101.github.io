---
layout: notes
---
# Flask

The following code demonstrates how to create a simple webservice accepting REST calls.

```python
from flask import Flask
from flask_restful import Api, Resource, reqparse

# creates the app
app = Flask(__name__)
api = Api(app)

# creates some data
users = [
    {
        "name": "James",
        "age": 30,
        "occupation": "Network Engineer"
    },
    {
        "name": "Ann",
        "age": 32,
        "occupation": "Doctor"
    },
    {
        "name": "Jason",
        "age": 22,
        "occupation": "Web Developer"
    }
]

class User(Resource):
    """resource representing a user"""
    def get(self, name):
        """maps HTTP GET to retrieve a user"""
        for user in users:
            # returns the requested user
            if(name == user["name"]):
                return user, 200
        return "User not found", 404

    def post(self, name):
        """maps HTTP POST to create a new user"""
        # parses the input
        parser = reqparse.RequestParser()
        parser.add_argument("age")
        parser.add_argument("occupation")
        args = parser.parse_args()

        for user in users:
            # some validation
            if(name == user["name"]):
                return "User with name {} already exists".format(name), 400

        # builds the model
        user = {
            "name": name,
            "age": args["age"],
            "occupation": args["occupation"]
        }

        # adds it to the data
        users.append(user)
        return user, 201

    def put(self, name):
        """maps HTTP PUT to update a user"""
        # parses the input
        parser = reqparse.RequestParser()
        parser.add_argument("age")
        parser.add_argument("occupation")
        args = parser.parse_args()

        for user in users:
            # finds the user and updates it
            if(name == user["name"]):
                user["age"] = args["age"]
                user["occupation"] = args["occupation"]
                return user, 200

        # if the user is missing, it simply creates it
        user = {
            "name": name,
            "age": args["age"],
            "occupation": args["occupation"]
        }
        users.append(user)
        return user, 201

    def delete(self, name):
        """maps HTTP DELETE to delete a user"""
        global users
        # removes the user from the list
        users = [user for user in users if user["name"] != name]
        return "{} is deleted.".format(name), 200

# maps the class User to a specific url
api.add_resource(User, "/user/<string:name>")

app.run(debug=True)
```

To run it:

```bash
$ python3 flash_ex.py
 * Serving Flask app 'flash_ex' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 100-815-182
```

The command `w3m http://127.0.0.1:5000/user/Ann` calls the endpoint `/user` with the path-parameter `Ann`. The line `api.add_resource(User, "/user/<string:name>")` maps the call to the class `User`. Being a `HTTP GET`, the method `User.get` is being called.

The command `w3m http://127.0.0.1:5000/user/Adam` follows the same path, but returns an error message with status `404` because there is no `Adam` in `users`
