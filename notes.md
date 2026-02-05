### The Accidental CTO

1. **Chapter 1** - ```htop```, monolith
2. **Chapter 2** - Django admin panel, ORM, PostgreSQL, Nginx (web server), Gunicorn (application server)
3. **Chapter 3** - Separate deployments of App and Database,
    - ```pg_dump -U postgres dukaan_prod > dukaan_backup.sql```
    - ```psql -U postgres -d dukaan_prod < dukaan_backup.sql```
    - Django, ```select_related, prefetch_relaated```
    - Connection pooling - ```pgbouncer```
4. **Chapter 4** - Load balancing
    - Round Robin
    - Least Connections
    - Nginx as LB,
    - ```nginx.conf``` - ```upstream``` block, ```least_conn```
5. **Chapter 5** - Read replicas
    - majority of the DB operations were reads (95%)
    - Streaming replication - replicas subscribe to the Master's Write-Ahead Log (WAL)
    - db router in Django to redirect writes to master and reads to replicas.
    - CAP theorem - Consistency, Availability, Partition tolerance
      - In a distributed system, we can guarantee at most two of the these properties at the same time.
      - when choosing replicas, we're choosing availability over strict consistency.
      - Strong consistency, Eventual consistency, Causal consistency
      - Read your own writes (temporarily read from Master after a write)
