# docker-compose-mongodb
## MongoDB with Docker and Docker Compose

**Usage (start server)**
'''
On folder that contains docker-compose.yml type one of this
'''

// non detach mode

'''
docker-compose up
'''

or

// detach mode

'''
docker-compose up -d
'''
**It will spin the MongoDB latest version (currently 4.x.x version), expose port to host at 27017.**

**Usage (stop server)**
To shutdown database without remove the container.
'''
docker-compose stop
'''

**To shutdown database and remove the container.**
'''
docker-compose down
'''

Is data or user that already created will gone? No, since in the Docker Compose file you can see that we utilize data container named mongodb_data_container to store the MongoDB data.

**MongoDB credential (for database admin)**
'''
Username: root
Password: rootpassword
'''


How to connect to MongoDB
Via mongo Shell inside docker container
Type this.
'''
docker exec -it <container_name> mongosh
It will connect to localhost port 27017.
'''

In Unix ==> Note that mongo command should be installed on the computer. On Linux this should be install mongodb-org-shell only. Refer to this for more detail https://docs.mongodb.com/manual/installation/

**check the db name on prompt**
if it is > test then create a user using following command
'''
db.createUser(
  {
    user: "user",
    pwd: "password",
    roles: [ { role: "userAdminAnyDatabase", db: "test" } ]
  }
)
'''
** switch to admin db **
'''
use admin
'''

**authenticate the db with user name and password given in docker-compose file**
'''
db.auth("root", "rootpassword")
'''

**Some quick tips after logged-in**
**Show databases:**
'''
show dbs
'''

**Create new non-existant database:**
'''
use mydatabase
'''

**Show collections:**
'''
show collections
'''

**Show contents of a collection:**
'''
db.your_collection_name.find()
'''

**Save a data to a collection:**
'''
db.your_collection_name.save({"name":"Sony AK"})
'''
**Show database version:**
'''
db.version()
'''

**Enjoy your local MongoDB database server for any purpose you want, for me this setup is fine for testing purpose.**