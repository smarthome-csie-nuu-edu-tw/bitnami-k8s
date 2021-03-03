### Harbor 
目前部屬仍以官方chart部屬為數

### 採用外部資料庫+redis
```yaml
database:
  # if external database is used, set "type" to "external"
  # and fill the connection informations in "external" section
  type: external
  external:
    host: "devops-db-postgresql"
    port: "5432"
    username: "postgres"
    password: "IIIdevops123!"
    coreDatabase: "registry"
    notaryServerDatabase: "notary_server"
    notarySignerDatabase: "notary_signer"
    # "disable" - No SSL
    # "require" - Always SSL (skip verification)
    # "verify-ca" - Always SSL (verify that the certificate presented by the
    # server was signed by a trusted CA)
    # "verify-full" - Always SSL (verify that the certification presented by the
    # server was signed by a trusted CA and the server host name matches the one
    # in the certificate)
    sslmode: "disable"
  # The maximum number of connections in the idle connection pool.
  # If it <=0, no idle connections are retained.
  maxIdleConns: 50
  # The maximum number of open connections to the database.
  # If it <= 0, then there is no limit on the number of open connections.
  # Note: the default number of connections is 1024 for postgre of harbor.
  maxOpenConns: 1000

redis:
  # if external Redis is used, set "type" to "external"
  # and fill the connection informations in "external" section
  type: external
  external:
    # support redis, redis+sentinel
    # addr for redis: <host_redis>:<port_redis>
    # addr for redis+sentinel: <host_sentinel1>:<port_sentinel1>,<host_sentinel2>:<port_sentinel2>,<host_sentinel3>:<port_sentinel3>
    addr: "devops-redis-master:6379"
    # The "coreDatabaseIndex" must be "0" as the library Harbor
    # used doesn't support configuring it
    coreDatabaseIndex: "0"
    jobserviceDatabaseIndex: "1"
    registryDatabaseIndex: "2"
    chartmuseumDatabaseIndex: "3"
    trivyAdapterIndex: "5"
    password: "IIIdevops123!"
```