#Commands

##Connect

`mongo [host:port]`

##DB

`db.stats()`

`use DATABASE_NAME` creates db if not existant

`db` shows current db

`show dbs` empty databases will not list!

##Query

`db.COLLECTION_NAME.find() {.pretty()}`

##Insert

`db.COLLECTION_NAME.insert({name: "aa"})`

##Export/Import

```
mongoexport --host {hostname} --port {port} --db {dbname} --collection {collection} --out {filename}
mongoimport --host {hostname} --port {port} --db {dbname} --collection {collection} --file {filename}
```


