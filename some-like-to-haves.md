# Some missing peices I'd like to haves:

# Functional Databases

I like the idea of functional databases. Background: Derek Sivers posted a blog post. I posted a reply expressing support in the HN thread about it: https://news.ycombinator.com/item?id=21369967

After mulling it over a bit more I've realized that while PL/PGSQL is pretty good the reason I don't use it sometimes is because I want to support sqlite3 for easy data portability too. So it would be nice if there was an alternative "on database" scripting language that worked with both postgres & sqlite. One way to achieve that might be something like knex.js on top of node-postgres for postgres and knex.js on top of itself for sqlite3. I think it would have a decent shot at becoming a standard. Who should fund it: CockroachDb, CitusData, Yugabyte. In my opinion this database FAAS paradigm makes sense for their business models. You define a function header like `SELECT storeX(...)` and they come back to you and say we can make it span different geo regions, scale massively, run this fast, etc etc. That is something I would like to have.

# Flexible Configuration System

YAML is fashionable and ok but it's mostly just another object format and in my opinion not that great. Considering it's 2020, there should be better tools for writing a stateless service. It would be nice if there was a framework such that lets you define a json schema file, with a few conventions like ti,dd,eg,rq (for required vs optional) and va (for values):

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
Then you could probably autogenerate:

* a command line tool for configuring your service or validaitng your configuration json file.
* a web form / gui for configuring the service.
* Your service could have a route that listens on the localhost interface for updated configurations. 
* You could even autogenerate some docs if the preferred method of passing values to a container was via environmental variables like: `ENV_MAIN_VA="127.0.0.1:4800"`. 

Lots of flexibility and it could even become a standard way of configuring services. That is something that I would like to have. 
