<!-- TITLE: Database -->
<!-- SUBTITLE: How to configure MongoDB with Wiki.js -->
![Mongodb](/uploads/page-icons/mongodb.png "Mongodb"){.pagelogo}

# MongoDB
MongoDB is a free and open-source cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemas.

:information_source: **MongoDB** `3.2` **or later is required.**

- [Official Website](https://www.mongodb.com/)
- [Installation Guide](https://docs.mongodb.com/manual/administration/install-community/)

It can safely be installed on the same server as Wiki.js. MongoDB is mainly used for users and content metadata, which is very light on server resources usage.

Replica Set / Sharded Cluster installations are fully supported.

Should you prefer on having a cloud provider host the MongoDB instance for you, here's a few examples:

- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- [mLab](https://mlab.com/)
- [Compose (IBM)](https://www.compose.com/mongodb)
- [ObjectRocket (rackspace)](http://objectrocket.com/mongodb/)

> :warning: **Cloud Provider Considerations**
>
> Make sure the MongoDB instance runs in the same datacenter (preferrably) or the same region. Connecting to instances located in another location will result in latency and poor performances!
{.is-warning}

# Connection String
A MongoDB connection string is formatted as such:  
`mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]][/[database][?options]]`

Refer to the [official MongoDB documentation](https://docs.mongodb.com/manual/reference/connection-string/) for all the possible options.

You can also use an **environment variable** containing the MongoDB connection string, e.g:  
`$(MONGO_URI)`

# Examples
**Using a local MongoDB instance (on the same server as Wiki.js):**  
`mongodb://localhost:27017/wiki`

**A username/password protected instance on a single remote server:**  
`mongodb://username:password@remote.server.com:27017/wiki`

**A username/password protected instance on a remote cluster:**  
`mongodb://username:password@first.server.com:27017,second.server.com:27017,third.server.com:27017/wiki`