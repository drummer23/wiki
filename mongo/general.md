#Mongo DB

##Terminology

Terms in parenthesis are the corresponding name in RDBMS


- Database (Database)
Physical container. Typicly there are mutliple databases

- Collection (Table)
Collections do not enforce a schema.

- Document (Tubple/Row)
A document is a set of key-value pairs. Documents have dynamic schema. Dynamic schema means that documents in the same collection do not need to have the same set of fields or structure

- Field (column)

##Modeling

- Combine objects into one document if you will use them together. Otherwise separate them (but make sure there should not be need of joins).

- Do joins while write, not on read.

- Optimize your schema for most frequent use cases.