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

some more questions:
static vs classmethod
managers in django
objects
Destroy method why do we use queryset = Node.objects.all() we should not use this
migrations vs migrate
how django knows order of migration files
what will be first initialized in django
db calls for select related and prefetch related
adminstartive commands

In the serializers why do we use read_only and write only
why allowed hosts in django

we are using this 2 fields in all the models is there any way we can reuse this, i dont want to write in everymodel
    created_at = models.DateTimeField(auto_now=True)
    modified_at = models.DateTimeField(auto_now=True)


mutable vs immutable
is vs ==
dunder method
generator methods

django flow
why do we use middlewares in django

scenario where you have handled database optimization

a = Node.objects.filter(name__in=["a", "b"])

b = Node.objects.filter(name__in=["a", "b"])

print(b)

how many db calls

code1:
class ListCopy(list):
    def __init__(self, *args, **kwargs):
        self.values = args
        
    def __len__(self):
        return 1;

l = ListCopy([1, 2, 3, 4])
l.append(5)
print(len(l))

code2:
l1 = [1, 2, 3]
l2 = list(l1)
print(l2 is l1) # False
print(l2 == l1) # True

code3:
t1 = (1, 2, 3)
t2 = tuple(t1)
t3 = tuple(t1)
print(t3 is t2) # False
print(t3 == t2) # True

code4:
s1 = 'ABC'
s2 = 'ABC'
print(s1 is s2) # True

def extendList(val, list=[]):
    list.append(val)
    return list

code5:
list1 = extendList(10) # [10]
list2 = extendList(123,[]) #[123]
list3 = extendList('a') #["a"]

print("list1 = %s" % list1)
print("list2 = %s" % list2)
print("list3 = %s" % list3)

code6:
a = [1,2]
b = set()
c = {}

print(type(a))
print(type(b))
print(type(c))

c[a] = a
print(c) # Error, keys mutable

# Django questions
   Django Interview Questions

   prefetch_related and select_related
   memory management in django
   generics vs modelviewset
   Does middleware does preoperation and postoperation as well?
   what is middleware?
   You have one organization table and device table, device table is the foreign key of the organization table. based on device find all the organizations
   Organization.objects.all().filter(device__id="12")
   have you done admin page customization
   can we decode the password of the user table is it possible?
   
   select_related("desgin").values().first()
   .values().first()
    
   both of them gives same value the only difference is the optimization, it uses inner join, reduces queries hits
    
   DesignMaster.objects.select_related("project").filter(project__id="062383a7-c753-4d39-8d17-7ffee185d10f").values().first()
   DesignMaster.objects.filter(project__id="062383a7-c753-4d39-8d17-7ffee185d10f").values().first()
    
   Q) You have project id get design id and project content
   design = DesignMaster.objects.get(id="cc737589-18f4-4587-9d4a-d6ceaa2d76db")
   design.project.project_number
    
   Q) Many to many relation I have design id that is associated with multiple roof ids 
   design = DesignMaster.objects.get(id="cc737589-18f4-4587-9d4a-d6ceaa2d76db") 
   design.roof_details.all()
    
   Q) Queries
   Project.objects.filter(Q(project_number="D-0020") | Q(project_number="D-0021") & Q(is_deleted=True)).values()
   Project.objects.filter(Q(project_number="D-0020") | (Q(project_number="D-0021") & Q(is_deleted=True))).values() 
   Project.objects.filter((Q(project_number="D-0020") | Q(project_number="D-0021")) & Q(is_deleted=True)).values()
   
   difference between abstract user and base user
   	abstract user = extends User modal, Ideal for to add functionality without losing existing features, builtin functions, built in fields
   	AbstractBaseUser = completly customizable, gives only basic authentication
   
   postion : relative, absolute
   postion: fixed, static, sticky
   html : box properties, inline, block
   
   different class in python
   abstract, static, instance
   generators
   
   session storage and localstorage
   cookies 
   
   serverside and client side rendering
   
   Generator 
   from datetime import datetime
   
   def seq(n):
       
       for i in range(n):
           yield i
           
   a = seq(10000000000)
   #print(a)
   start = datetime.now()
   for i in a:
       print(i)
   end = datetime.now()

# Python coding snipets
   a = "190356"
   # 10012359
   
   
   # starting number can never be zero
   # find the least number from the remaining
   
   result = [0 for i in range(10)]
   
   # dict_res = dict([(i, 0) for i in range(10)])
   # mini = -1
   
   # print(dict_res)
   # temp = ""
   for i in a:
       result[int(i)] += 1
   
   temp = '0'*result[0]
   res = ""
   # print(result)
   for outer in range(1, len(result)):
       for i in range(result[outer]):
           res += str(outer)
   
   out = res[1] + temp + res[1:]
   print(out)
   
   # Longest substring without repeation
   # abcdaaabcded
   
   a = "GEEKSFORGEEKS"
   longestSubstr = ""
   current = ""
   
   for i in range(len(a)):
       if(a[i] not in current):
           current+=a[i]
       else:
           if(len(current)>len(longestSubstr)):
               longestSubstr = current
   
   if(len(current)>len(longestSubstr)):
       longestSubstr = current
   
   print(longestSubstr)
   
   # Longest substring without repeation
   # abcdaaabcded
   
   a = "pwwkew"
   
   longestSubstr = ""
   temp = ""
   for i in range(len(a)):
       if(a[i] not in temp):
           temp+=a[i]
       else:
           if(len(temp)>len(longestSubstr)):
               longestSubstr=temp
               if(temp[0]==a[i]):
                   temp = temp.replace(a[i], "")
                   temp+=a[i]
               else:
                   temp = ""
   if(len(temp)>len(longestSubstr)):
       longestSubstr=temp
       
   print(longestSubstr)
   
   
   print("TIME ----",start - end)



