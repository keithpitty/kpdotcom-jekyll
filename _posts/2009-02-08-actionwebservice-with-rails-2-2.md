---
layout: post
title: ActionWebService with Rails 2.2
date: 2009-02-08
permalink: /blog/archives/2009-02-08-actionwebservice-with-rails-2-2
---

I encountered a trick for young players the other day when providing
XML-RPC web service support within a Rails application.

Since Rails 2.0 was introduced, RESTful web services via ActiveResource
have been supported in preference to SOAP or XML-RPC web services.
Indeed, ActionWebService was dropped from Rails when version 2.0 was
released.

However, there are times when the need to provide an interface to
another application mandates the use of SOAP or XML-RPC. Recently I had
a need to provide an XML-RPC web service server within a Rails
application. Fortunately, [a version of ActionWebService has been kept
up to date](http://github.com/datanoise/actionwebservice/tree/master) on
GitHub [together with
instructions](http://www.datanoise.com/articles/2008/7/2/actionwebservice-is-back)
for implementing it.

As I was developing my support for XML-RPC calls, I found chapter 25 of
Thomas and Hansson’s “Agile Web Development with Rails” (second edition)
invaluable.

For simplicity’s sake, let’s say my controller was:

<code lang='ruby'>  
class BackendController \< ApplicationController  
wsdl_service_name ‘Backend’  
web_service_api BackendApi  
web_service_scaffold :invoke if Rails.env == ‘development’

def foo_bar(args)  
\# method code goes here  
end  
end  
</code>

And here is an XML-RPC test client:

<code lang='ruby'>  
require ‘xmlrpc/client’  
require ‘pp’

server = XMLRPC::Client.new2(“http://example.com/backend/api”)  
result = server.call(“FooBar”, \[“arg1”, “arg2”, “arg3”\])

pp result  
</code>

Notice that the call is to a method called “FooBar” whereas the method
within the Rails controller is called “foo_bar”. If you’re like me you
will have originally fallen into the trap of assuming that the remote
call will have the same name as the controller method rather than the
camel case equivalent.
