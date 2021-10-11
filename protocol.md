# REST

**REST**, as was mentioned before is a messaging protocol that was designed
to allow **stateless** communication between various services on the web,
stateless communication meaning that messages that a receiver receives
do not matter on previous messages. Services that adhere to the REST
principles allow modification of resources and entities through textual
representation in the request.

# HTTP Verbs

- **GET** - Get is probably the most common HTTP verb used today on
  the internet, being the default one that you use when you visit a website
  on your browser. All it does is, well, it gets a resource from the endpoint
  that is specified. If you’re developing and API that serves an endpoint with
  a GET verb, one of the expectations of you callee is going to be that the
  service acting as the endpoint does not modify the server side state of the
  application (such as writing to it’s database), meaning that a GET should
  always be idempotent. Here’s an example of what we’d like to avoid:

```bash
`$ curl -X GET localhost:8000/pizzas/1`
`{"id": 1, "title": "Pepperoni and Cheese", "description":`
`"Yumm"}`
`$ curl -X GET localhost:8000/pizzas/1`
`{"id": 1, "title": "Salami Picante", "description":`
`"Also YUMM"}`
```

What happened here? We called the endpoint twice and it didn’t
return the same response. Now, arguable in some cases, this might be the
expected result, such as returning a random response on the endpoint or
the resource being modified in-between requests, however, not if the GET

```python
from django.http import JsonResponse
from pizza.models import Pizza
def get_pizza(request, pid):
    if request.method == 'GET':
        pizza = Pizza.objects.get(id=pid)
        pizza.title = 'Salami Picante'
        pizza.description = 'Also YUMM'
        pizza.save()
        return JsonResponse(
            data={
                'id': pizza.id,
                'title': pizza.title,
                'description': pizza.description,
            }
        )
```

If we want to keep idempotency, we don’t do the above code.
Now, before we get into too many philosophical arguments over what
application state means, in the context of this book, we are going to call the
objects that are directly accessed through the APIs application state.
:notebook:**Note** *In the above curl, I’ve used the -X GET flags, normally this is*
*not required when you’re doing a GET request with curl.*

- **PUT** - One of the other important HTTP verbs. PUT represents the
  replacement or creation of an object that is sent in the payload of the
  request. The object identifier is often represented in the URI of the request
  itself, and the body contains the members that need to be overwritten in the
  system. PUT requests are supposed to be idempotent by nature. Meaning:

```bash
$ curl -i -X PUT localhost:8000/pizzas/1 -d '{"title":
"Diavola", "description": "Spicy!"}'
HTTP/1.1 201 Created
...
{"id": 1, "title": "Diavola", "description": "Spicy!"}
$ curl -i -X PUT localhost:8000/pizzas/1 -d '{"title":
"Pikante", "description": "Spicy!"}'
HTTP/1.1 200 OK
...
{"id": 1, "title": "Pikante", "description": "Spicy!"}
```

So, no matter what happened, we always got back the same object,
with the same identifier.

- **POST** - Oftentimes confused with PATCH, POST is the non-­idempotent
  counterpart. Meaning that every time you send a POST request to your
  resource’s endpoint, you should always expect a new resource to be
  created there.

```bash
$ curl -i -X POST localhost:8000/pizzas/ -d '{"title":
"Diavola", "description": "Spicy!"}'
HTTP/1.1 201 Created
...
{"id": 1, "title": "Diavola", "description": "Spicy!"}
$ curl -i -X POST localhost:8000/pizzas/ -d '{"title":
"Diavola", "description": "Spicy!"}'
HTTP/1.1 200 OK
...
{"id": 2, "title": "Diavola", "description": "Spicy!"}
```

You can also see that in the above curls that we are not specifying the
identifier of the object we’d like to be working with.

- **PATCH** - What the difference between PUT, POST and PATCH is a
  notoriously popular interview question on web developer interviews.
  Now that we know that PUT is supposed to create and replace the object
  specified in the URL and POST is there to create new objects in the
  remote system, we can deduct that PATCH requests are there to make
  modifications on an already existing resource. If the resource doesn’t exist,
  then the response should announce this to us. Meaning that PATCH is not
  an idempotent HTTP verb.

```bash
$ curl -i -X PATCH localhost:8000/pizzas/2 -d '{"title":
"Diavola", "description": "Spicy!"}'
HTTP/1.1 404 Not Found
...
$ curl -i -X POST localhost:8000/pizzas/1 -d '{"title":
"Diavola", "description": "Spicy!"}'
HTTP/1.1 200 OK
...

{"id": 1, "title": "Diavola", "description": "Spicy!"}
```

- **DELETE** - One of the easier verbs, it is there to note that we would like
  to eliminate a specific resource from the system.
  There are a couple of less-popular HTTP verbs that we will quickly take
  a glance at:
-  **HEAD** - This verb is used to get only the headers of a request before
    issuing a proper GET request. This might come in handy if you’re
    uncertain about the content type or the size of the response that you’d
    need to process and it can give your systems an educated decision to
    actually make the request or not.
    OPTIONS - With this HTTP verb, you can figure out what other HTTP
    verbs are accepted on the given resource.
