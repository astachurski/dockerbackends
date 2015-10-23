# dockerbackends

First version.

Goals: 

Script created to make testing easier - when external backends are required.

Script is NOT universal. It's been created while working on MongooseIM testing automation and the backend handled
in this case is postgresql.

This is script allows a go-cd agent to reinitialize postgresql database from scratch so that any side effects on
backend side are avoided. 

Machine hosting docker instance of postgresql is accessed by application from agent machine trough SSH. 
Before agent can invoke remote commands trough SSH - public key should be planted first.

What scripts does is (roughly) :

- stop running instance of dockerized postgresql (if running)
- build new image from scratch using override dockerfile
- run new container
- create a new database role (user) using remote psql invocations
- create new schema the same way
- upload SQL script onto target machine
- run psql and create all the tables
- list created tables


