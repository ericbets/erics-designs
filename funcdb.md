#### Functional Databases

I like the idea of functional databases. For a bit of background, Derek Sivers posted a [blog post](https://sivers.org/pg2) last year about the merit of using alot of PL/PGSQL in database coding. For years I've did the same thing. Because I want my database to be loosely coupled to my code. I prefer something that looks more like an rpc api than something that needs to stay in sync with the app. 

After mulling it over a bit more I've realized that the reason I don't use PL/PGSQL 100% of the time is because I often want to support sqlite3 for easy data portability too. There is nothing quite like the ability to create or blow away a sqlite database with a simple `rm` command, especially when you are doing parallel distributed computation. It made think, what if there was a database local scripting language like PL/PGSQL that worked with both postgres & sqlite? SQLITE supports transactions so it shouldn't be too hard right? 

One way to achieve something like that could be knex.js on top of node-postgres for postgres and knex.js on top of itself for sqlite3. I think it would have a decent shot at becoming a standard, maybe even adopted by cloud vendors like CockroachDb, CitusData and Yugabyte. 

The storage customer defines a function header like `SELECT storeX(...)` or `SELECT queryZ(...)` and then they can come back to you and say we can make it span different geo regions, scale massively, run this fast, run on Mars etc etc. A service like this comports well with their business model, so perhaps they should consider funding this or something like it as a FAAS OLTP data storage standard. And if you as the customer don't have enterprise needs you just run it on your own infra, using your own database schemas and so on. A database portable local scripting PL/PGSQL alternative is something that I as a database user would like to have.

