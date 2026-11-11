# Outline

## Steps

1. Understand functional and non-functional system requirements.
2. Understand load and storage requirements.

        1. MAU; DAU; READ / WRITE RATIO.
        2. The number of requests per month for read / write operations.
        3. RPS; QPS:

        Make sure you do it on a per-entity basis.
        For example, calculate RPS for accounts, photos,
        or other entities separetely.

        4. Storage Requirements.
        5. Network Requirements.
        6. Storage Requirements for 5 years of work.
        7. CAP Theorem Restrictions.

3. Outline a schema of the system and scale the system.

        1. Discuss load balancing.
        2. Use a message broker.
        3. Choose a database considering the CAP theorem restrictions.
        4. Consider a database backups, sharding, and replication.
        5. Perhaps use cache.

4. Add observability.
