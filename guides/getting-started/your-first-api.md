---
layout: guides
title: "Getting Started: Your first API"
description: A quick guide on how to create a simple YAWP! API
---
# Your first API

To have your first API you just need to create an [Endpoint](/guides/api/models). It is done very
easily with a scaffold:

~~~ bash
mvn yawp:endpoint -Dmodel=person
~~~

Now we can change the __Person__ class to add the __name__ attribute:

~~~ java
@Endpoint(path = "/people")
public class Person {
    @Id
    IdRef<Person> id;
    
    String name;
}
~~~

Just start the development server:

~~~ bash
mvn yawp:devserver
~~~

After the development server starts, you can play with the __Person__ endpoint APIs with cURL. To create a person,
execute in a shell:

~~~ bash
curl -H "Content-type: application/json" -X POST \
     -d "{'name': 'John'}" http://localhost:8080/api/people
~~~

To list the created person:

~~~ bash
curl http://localhost:8080/api/people
~~~
