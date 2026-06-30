# interview-questions

authentication and authorization
max salary of an employee of 2 employees
nonlocal variable
where and having clause
indexing on db
how memory is managed in python
difference between function and method
what is namespace
what is a dictionary?
put and patch?
check if you python application is down how do you trouble shoot?
groupby, joins in sql?
multithread and multiprocessing?


def outer():
   x = 10
   y = 5
 
   def inner():
       nonlocal x
       x = 20
       y = 15
 
   inner()
   print(x)
   print(y)
outer()

prime number code

d = {1:2,(2,):3,'3':4,[4]:5}
print(d)

difference between tuples and list

custom user and abstract user?

difference between abstract user and abstract base user?

### What is a middleware?
   Middleware is a framework of hooks into Django's request/response processing. It sits between the web server and the Django view, allowing you to process every request before it reaches the view and every response before it is sent back to the client.
   pipeline:
      Client
      │
      ▼
   Middleware 1
      │
   Middleware 2
      │
   Middleware 3
      │
      ▼
   View
      ▲
   Middleware 3
      ▲
   Middleware 2
      ▲
   Middleware 1
      ▲
   Client
   Every incoming request passes through the middleware chain, reaches the view, and the response travels back through the same chain in reverse order.
   
   Whenever we have logic that should apply to every request or every response, middleware is a good fit.
   Examples include:
   Authentication
   Logging
   Request timing
   Timezone conversion
   Rate limiting
   CORS
   Custom headers
   Request ID generation
   Audit logging

   Interview takeaway
      A concise answer you can give is:
      "Middleware is code that executes for every HTTP request before the view and for every HTTP response after the view. It's used for cross-cutting concerns like authentication, logging, request preprocessing, timezone conversion, and security. In one of my projects, I implemented middleware to normalize incoming datetime values to UTC, so all downstream views and serializers worked with a consistent datetime format without duplicating conversion logic."

### Difference between abstract user and abstract base user?
   abstract user:
      It extends Django's built-in User model.
   abstract base user:
      This gives you only the authentication basics:
         Password handling
         Last login
         Authentication methods
   You must create everything else yourself.

   Interview:
   Abstract user:
   I would generally choose AbstractUser because it provides Django's built-in authentication, permissions, groups, and admin support while allowing me to add custom fields. It's simpler and suitable for most applications.
   Abstract base user:
   If the project has custom authentication requirements, such as using email or phone as the primary login identifier with significantly different user behavior, I would consider AbstractBaseUser because it provides complete flexibility at the cost of additional implementation effort.

