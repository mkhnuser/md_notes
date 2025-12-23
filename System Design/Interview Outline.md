# Outline

Here is a rough outline of how a system design interview should go:

1. Understand Functional and Non-Functional System Requirements.
2. Understand Load and Storage Requirements.

        1. MAU; DAU; READ / WRITE RATIO.
        2. The number of requests per month for read / write operations.
        3. RPS; QPS.
        4. Storage Requirements.
        5. Network Requirements.
        6. Storage Requirements for 5 years of work.
        7. CAP Theorem Restrictions.

3. Conduct the design.

        1. Draw a basic schema of the system.
        2. Choose a DB considering CAP restrictions.
        3. Conduct a modular design considering Functional Requirements.

                 Consider the usage of a message broker or a message bus.
                 This achieves decoupling and enables scalability.

        4. Add scaling to the system.

                  Discuss Load Balancing.
                  Consider Database Shards and Replicas.
