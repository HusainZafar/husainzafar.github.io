---
layout: post
---

Redis
-------

All text from this [Very good Intro](https://www.youtube.com/watch?v=qr4FVhBTq0I) + Notes from : [Crash Course](https://www.youtube.com/watch?v=Hbt56gFj998):

- NoSQL
- Key:Value based
- In Memory(Allows persistence inspite that)
- Datastructure Server: Binary safe strings, Lists, Sets, Sorted sets, Hashes, Bitmaps, HyperLogLogs, Geospatial Indexes	
- Open Source, Well Documented
- Fast, Not CPU Intensive, Scalable

Use cases:

- Cache(Expiring data)
- Analytics(Distributing locks)
- Leaderboard(High IO Workloads)
- Queues(Messaging)
- Cokie storage(Pub/Sub)

Persistence:

- Snapshot: SIngle file, **point in time**, suited for backups, maxmise performance, Needs to fork often, Not good when redis stops working, can lose around **5 minutes** of data
- Append Only File(AOF): contains **all operations** in parsable log, has many fsync policies(more controlled regarding how disk is persisted with read and write functions), no seeks or corruption(good for power outages), automatically writes itself when too big for disk, Much larger files(slower, buggier in worst case), but in worst case, lose data for only **2 sec**.

Built in replication: Async between master and slaves. Master continues to handle queries while slaves are sychronising

Notes:
- If key already exists, it gets re-written

Basic commands

```redis
> ping
PONG

> ECHO 'Hello'
"Hello"

> SET foo 100
OK

> GET foo
"100"

> SET bar "Hello"
OK

> GET bar
"Hello"

> INCR foo
(integer) 101

> GET foo
"101"

> DECR foo
(integer) 100

> EXISTS foo
(integer) 1

> DEL bar
(integer) 1

> EXISTS bar
(integer) 0

> GET bar
(nil)

> SET prefix:key value
OK

> SET greeting "Hello"
OK

> EXPIRE greeting 50
(integer) 1

> TTL greeting
(integer) 40

> TTL greeting
(integer) 30
```
