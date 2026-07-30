---
layout: default
title: "Postgres Destroyed Neo4j. And It's Free"
permalink: /postgres-19-runs-graph-queries-cancel-the-neo4j/
date: 2026-07-30
---

# Postgres Destroyed Neo4j. And It's Free

Sources and workings for every figure, price and claim quoted in the video.

Checked on 30 July 2026. PostgreSQL 19 was in beta on that date, so anything described
here is beta behaviour and can still change before the final release.

---

## Release status and timing

**PostgreSQL 19 Beta 1 was released on 4 June 2026.**
PostgreSQL Global Development Group, "PostgreSQL 19 Beta 1 Released!"
https://www.postgresql.org/about/news/postgresql-19-beta-1-released-3313/

**PostgreSQL 19 Beta 2 was released on 16 July 2026**, and its announcement lists
"Several fixes for the new SQL/PGQ property graph feature."
https://www.postgresql.org/about/news/postgresql-19-beta-2-released-3350/

**The final release is targeted at around September or October 2026.** Both announcements
carry the same sentence: "The PostgreSQL Project will release additional betas as required
for testing, followed by one or more release candidates, until the final release around
September/October 2026."

**Beta behaviour is explicitly not final.** Beta 1: "As this is a Beta, minor changes to
database behaviors, feature details, and APIs are still possible." Beta 2: "While we do
not advise you to run beta versions in production environments, we encourage you to find
ways to run your typical application workloads against this beta release."

**Beta 1 is available in the Amazon RDS Database Preview Environment.**
https://aws.amazon.com/about-aws/whats-new/2026/06/postgresql-19-beta-1-amazon-rds-database-preview-environment/

## The size of the release

**The draft release notes contain 204 entries.** Counted from the release notes page for
version 19, which at the time of checking was headed "Release date: 2026-??-??, AS OF
2026-06-17". The count is 187 items under "E.1.3. Changes" plus 17 items under
"E.1.2. Migration to Version 19", each carrying its own commit link.
https://www.postgresql.org/docs/19/release-19.html

The other features named in the video all appear in the Beta 1 announcement: the `REPACK`
command for reclaiming storage without downtime, parallel autovacuum, online data
checksums, and `GROUP BY ALL`.

## What SQL/PGQ is

**SQL/PGQ is part of the SQL standard, and PostgreSQL 19 is the first PostgreSQL release
to implement it.** Beta 1 announcement: "PostgreSQL 19 introduces support for SQL/PGQ,
letting users execute property graph queries using SQL standard syntax."

**The release note entry credits Peter Eisentraut and Ashutosh Bapat**: "Add support for
SQL Property Graph Queries (SQL/PGQ) (Peter Eisentraut, Ashutosh Bapat)".

**The syntax shown on screen is from the documentation.** A property graph is defined over
existing tables with `CREATE PROPERTY GRAPH ... VERTEX TABLES (...) EDGE TABLES (... SOURCE
... DESTINATION ...)`, tables may carry one or more `LABEL`s, and the graph is queried with
`SELECT ... FROM GRAPH_TABLE (graph MATCH (a)-[e]->(b) COLUMNS (...))`. Predicates may be
written inside the pattern, as in the documentation's own example
`(o IS "order" WHERE o.ordered_when = current_date)`.
https://www.postgresql.org/docs/19/ddl-property-graphs.html

**Defining a property graph copies no data.** It is a schema object over the existing
tables, closer to a view than to a storage engine.

## Why it performs like ordinary SQL

**A graph pattern is rewritten into relational joins.** PostgreSQL 19 implements SQL/PGQ as
a rewriter rather than a graph storage engine: the pattern becomes ordinary joins, existing
indexes are used, and the standard planner costs the result. A traversal of depth N becomes
N joins.
Christophe Pettus, "SQL/PGQ in PostgreSQL 19: Graph Queries Without the Graph Database"
https://thebuild.com/blog/sqlpgq-in-postgresql-19-graph-queries-without-the-graph-database/

**The rest of the database still applies.** Because a property graph is a schema object
over the same tables, and the query it produces is an ordinary one, the graph data is
covered by the same transactions, the same permissions, the same backups and the same
connection pooling as everything else in that database. This follows from the design
described above rather than from a separate feature announcement.

## The limitation

**Quantified patterns are not in this release.** The `*`, `+` and `{m,n}` quantifiers are
not supported, so a pattern such as `-[:Knows*1..5]->` cannot be written and each hop must
be spelled out. Queries that need unbounded traversal, such as shortest path or transitive
closure, still require recursive CTEs. Quantified patterns are described as planned for a
follow up patch.
Source as above, and
https://neon.com/postgresql/postgresql-19/sql-pgq-graph-queries

## Where a dedicated graph database still wins

**Index free adjacency.** Neo4j stores direct pointers from every node to its incident
edges, so traversal cost is proportional to the size of the result rather than the size of
the graph. A relational join returns to an index on every hop, and the gap widens with
depth and graph size.
Source: thebuild.com article above.

**The algorithm library.** Neo4j's Graph Data Science library provides graph algorithms
including PageRank, community detection, centrality measures and node embeddings, exposed
as Cypher procedures. PostgreSQL ships no equivalent.
https://neo4j.com/docs/graph-data-science/current/algorithms/

**Those algorithms run on a projected graph.** The same documentation notes that GDS uses a
specialised in memory graph format, and that the data must be loaded from the database into
that format before the algorithms run.
https://neo4j.com/docs/graph-data-science/current/introduction/

## The prices

All figures are the public list prices shown on Neo4j's pricing page on 30 July 2026, in US
dollars.
https://neo4j.com/pricing/

| Plan | List price |
| --- | --- |
| AuraDB Free | $0 |
| AuraDB Professional | $65 per GB per month |
| AuraDB Business Critical | $146 per GB per month, minimum 2 GB cluster |
| Aura Graph Analytics | $0.40 per GB per hour |

The published Business Critical size table gives $2,336 per month for a 16 GB instance,
which is the figure used on screen.

**The $28,032 annual figure is that monthly price multiplied by twelve:**
$2,336 x 12 = $28,032. It is rounded to "$28,000" when spoken.

The same page states that an instance can be paused and resumed, and that the free tier
requires no payment method.

---

## Caveats

- The prices are public list prices for one vendor's managed plans, captured on one day.
  They exclude tax, committed use discounts, negotiated enterprise terms and any cloud
  marketplace pricing, and they can change without notice.
- $28,032 is one worked example at one instance size on one plan. It is not an average
  bill, and no survey of what teams actually pay was carried out.
- The count of 204 release note entries is a snapshot of a draft document taken at the
  17 June 2026 revision. Release notes are edited throughout the beta period, so the final
  count will differ.
- The September or October target is the project's stated aim in its own announcements, not
  a commitment, and no release date had been fixed at the time of checking.
- No benchmarks were run for this video. The statements about how SQL/PGQ performs describe
  its implementation as a rewriter over ordinary joins, and the comparison against index
  free adjacency is taken from the cited write up rather than from a measurement made here.
- Everything about PostgreSQL 19 here describes a beta. The feature set, syntax and
  behaviour can still change before general availability.
- Neo4j is used throughout as the example of a dedicated graph database because its pricing
  is published. Other graph databases exist and are priced differently.
