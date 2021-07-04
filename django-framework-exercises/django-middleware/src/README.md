# Django middleware 

## Tasks
1. The  MIDDLEWARE setting contains the middleware for your project. We can think of it as a low-level plugin system, allowing to implement hooks that get executed in the request/response process. 

* Each middleware is responsible for some specific action that will be executed for all HTTP requests or responses.

* In [documentation](https://docs.djangoproject.com/en/3.1/ref/middleware/#available-middleware) you can find information about specific middleware.

* When an HTTP request is received, middleware are executed in order of appearance 
in the MIDDLEWARE setting. When an HTTP response has been generated by Django, 
the response passes through all middleware back in reverse order.

* Avoid adding expensive processing to middleware, since they are executed in every single request!

* **Don't forget to activate you virtualenv!**  

2. Creating a custom middleware
*  **for now the only idea I have for this exercise is to create custom middleware, and I'm looking for a good concepts**

* When adding a new middleware to the MIDDLEWARE setting, make sure to place it in the right position. Middleware are executed in 
order of appearance in the setting during the request phase, and in reverse order for responses.

* Middleware is a regular Python class that hooks into Django’s request/response life cycle. Those classes holds pieces of code that are processed upon every request/response your Django application handles.

* The Middleware classes doesn’t have to subclass anything and it can live anywhere in your Python path. The only thing Django cares about is the path you register in the project settings MIDDLEWARE_CLASSES.

* Your Middleware class should define at least one of the following methods:

    * Called during request:
        * process_request(request)
        * process_view(request, view_func, view_args, view_kwargs)
    * Called during response:
        * process_exception(request, exception) (only if the view raised an exception)
        * process_template_response(request, response) (only for template responses)
        process_response(request, response)


## Input/Output:
```
Working custom middleware.
```