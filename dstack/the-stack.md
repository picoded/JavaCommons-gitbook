# The (Data) Stack

The data stack represents a common interface to access and mainpulate data information across a variety of backends.

**Pros:** 

Platform agnostic, simplified NO-SQL interface, that is easily usable by the application developers. Which does most setup steps automatically. Change from mysql to oracle with a single line configuration.

**Cons:** 

Compromises were made, not all features of a particular backend is made accessible to the developer (transactions, foreign keys for example), certain unsupprted feature set may have been polyfilled, to detrimental performance results.

There is also a theorectical race condition, where a cache can go out of sync. Though in practise, unless a single row record has high concurrent writes. This should not occur. And on the rare chance it did, with proper cache renewal or expirary, eventual consistency will kick in.

## Stack Ordering

While the general model is based on the [data levels concept](./CONCEPT-data-levels.md), where the lowest level is at the start of the stack, and the highest level last. This is not enforced.

For simplicity sake, we consider the backend at the end of the stack (assumingly the highest level), the 'source-of-truth'. 

In event of any data conflict is found, the results defer to the 'source-of-truth'.

Read operations is done from the start of the stack, where data is present, until it reaches the 'source-of-truth'

Write operations is done from the end of the stack, the 'source-of-truth', and up the stack till be beginning.

## Typical small deployment / development

A typical small deployment / development environment, is typically a 2 layer stack.

(@TODO : Insert pancake of 2 layers)
``` javascript
[
	"RequestCache",
	"SQL"
]
```

### (Level 0) : request data cache

At the first layer, is the `L0 : request data cache`, which helps cache various repeated read calls made within a single request. 

A common example would be user information, where it is used for authentication, routing logic, and application logic. Which rarely changes, and is read in a single SQL call, instead of 3.

However due to the lack of data in this layer, typically it does not have any query or aggregation capabilities, which is handled by the other stack layers.

### (Level 2~3) : SQL backend

At the second layer, is the `L2 / 3 : SQL backend`, this act as the 'source of truth', and facilitate all operations beyond simple read and write. Such as query or aggregations.

Development is typically an `L2` with SQLite as local backend, or a development shared mysql instance.

Deployment is typically an `L3` with mysql backend, with a failover read-replica.

## Large scale deployment

Once the `source-of-truth` backend starts to face performance issue, typically a cache is deployed. Typically this would be a multiple application node deployment.

(@TODO : Insert pancake of 2 layers)
``` javascript
[
	"RequestCache",
	"DistributedCache",
	"SQL"
]
```

### (level 0) : request data cache

Once again this provides read cache for a single API request

### (level 3) : distributed cache
Distributed data cache, that is shared across all instances and requests. Typically this would be a subset of the data, which is most typically used. Under the hot and cold data concept, this is typically hot data.