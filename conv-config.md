#### Flexible Configuration System

YAML is fashionable and ok but it's just another object format and in my opinion not a great solution. Considering it's 2020, there should be better tools for configuring a stateless service. It would be nice if there was a framework that lets you define a json schema file and used some extra string metadata to autogenerate:

* a command line tool for configuring your service or validating your configuration json file. eg. --title-header
* a web form / gui for configuring the service.
* Your service could have a route that listens on the localhost interface for updated configurations. 
* You could generate some docs if the preferred method of passing values to a container was via environmental variables like: `ENV_MAIN_VA="127.0.0.1:4800"`. 

Here's one design that uses a few self documenting conventions like ti (title),dd (description),eg (example), rq (for required vs optional) and va (for values) like this:


```json
{
  "main": {
    "ti": "Title Header",
    "dd": "Detailed Description",
    "eg": "127.0.0.1:4800",
    "rq": true,
    "va": [ "where the actual data goes" ]  
  }
}
```
Then the fact that you can easily generate a config file and these tools probably makes up for the pain of a few extra brackets. A system like this would have a lot of flexibility. Perhaps it could even become a standard way of configuring services. That is something that I would like to have. 

