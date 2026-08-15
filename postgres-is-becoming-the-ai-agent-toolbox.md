---
layout: default
title: "Postgres for AI Agents: The Whole Backend Trick"
permalink: /postgres-is-becoming-the-ai-agent-toolbox/
date: 2026-08-15
---

# Postgres for AI Agents: The Whole Backend Trick

{% raw %}
Every mechanism, feature name, SQL clause and extension the finished shots put on screen,
chased to its primary source. Worked from the `TEXT:` lines in BEATS.md, so nothing that
appears on screen is missing from this list.

The shots draw schemas, queries and worked examples. Those are demonstrations of the
features cited below, not measurements: no throughput figure, price, benchmark or market
number appears anywhere in this video, and the only numbers on screen are counted from
what is already drawn in the same frame.

## Row locking, and using a table as a queue

`SELECT ... FOR UPDATE SKIP LOCKED`, drawn in beats 032 and 033 as two workers claiming
different rows of the same jobs table.

> With `SKIP LOCKED`, any selected rows that cannot be immediately locked are skipped.
> Skipping locked rows provides an inconsistent view of the data, so this is not suitable
> for general purpose work, but can be used to avoid lock contention with multiple
> consumers accessing a queue-like table.

PostgreSQL documentation, SELECT, The Locking Clause:
https://www.postgresql.org/docs/current/sql-select.html

`SKIP LOCKED` arrived in PostgreSQL 9.5, alongside row level security:

> Add SELECT option SKIP LOCKED to skip locked rows (Thomas Munro). This does not throw an
> error for locked rows like NOWAIT does.

PostgreSQL 9.5 release notes: https://www.postgresql.org/docs/release/9.5.0/

The row lock modes named on screen (`FOR UPDATE`, `FOR SHARE`) and their release at
transaction end: https://www.postgresql.org/docs/current/explicit-locking.html

## Advisory locks

Named in beat 005 as one of the sharp edges, and used in beat 012 as the locking tool.

> PostgreSQL provides a means for creating locks that have application-defined meanings.
> These are called advisory locks, because the system does not enforce their use, it is up
> to the application to use them correctly.

https://www.postgresql.org/docs/current/explicit-locking.html

## LISTEN and NOTIFY

Named in beat 005. The shot does not claim more than the docs do, and the commit boundary
matters to the argument the transactions chapter makes:

> The NOTIFY command sends a notification event together with an optional "payload" string
> to each client application that has previously executed LISTEN channel for the specified
> channel name in the current database.

> if a NOTIFY is executed inside a transaction, the notify events are not delivered until
> and unless the transaction is committed.

https://www.postgresql.org/docs/current/sql-notify.html

## JSONB, GIN indexes and containment

Beats 055, 056 and 060 build a jsonb column, index it and query it.

> The json data type stores an exact copy of the input text, which processing functions
> must reparse on each execution; while jsonb data is stored in a decomposed binary format
> that makes it slightly slower to input due to added conversion overhead, but
> significantly faster to process, since no reparsing is needed. jsonb also supports
> indexing, which can be a significant advantage.

> In general, most applications should prefer to store JSON data as jsonb, unless there
> are quite specialized needs, such as legacy assumptions about ordering of object keys.

> GIN indexes can be used to efficiently search for keys or key/value pairs occurring
> within a large number of jsonb documents (datums).

> The default GIN operator class for jsonb supports queries with the key-exists operators
> `?`, `?|` and `?&`, the containment operator `@>`, and the jsonpath match operators `@?`
> and `@@`.

https://www.postgresql.org/docs/current/datatype-json.html

The operators drawn in beat 062 (`->`, `->>`, `@>`, `jsonb_path_query`) are all from the
JSON functions and operators page:
https://www.postgresql.org/docs/current/functions-json.html

## Full text search

Beat 071 extracts lexemes with `to_tsvector` and matches with `@@`.

> Full text searching in PostgreSQL is based on the match operator `@@`, which returns
> true if a tsvector (document) matches a tsquery (query).

> There are functions to_tsquery, plainto_tsquery, and phraseto_tsquery that are helpful
> in converting user-written text into a proper tsquery, primarily by normalizing words
> appearing in the text. Similarly, to_tsvector is used to parse and normalize a document
> string.

https://www.postgresql.org/docs/current/textsearch-intro.html

## Trigram matching

The other half of beat 071: a misspelling scored against a real value.

> The pg_trgm module provides functions and operators for determining the similarity of
> alphanumeric text based on trigram matching, as well as index operator classes that
> support fast searching for similar strings.

> similarity ( text, text ) -> real: Returns a number that indicates how similar the two
> arguments are. The range of the result is zero (indicating that the two strings are
> completely dissimilar) to one (indicating that the two strings are identical).

> The pg_trgm module provides GiST and GIN index operator classes that allow you to create
> an index over a text column for the purpose of very fast similarity searches.

The similarity value shown on screen for a single-letter misspelling is the documented
worked example, `similarity('word', 'words')` returning `0.571429`, and is drawn as that
comparison rather than as a general claim.

https://www.postgresql.org/docs/current/pgtrgm.html

## Search filtered by the same permission rules as the app

Beat 072 draws the result set passing through a row security policy rather than through a
second authorization layer.

> tables can have row security policies that restrict, on a per-user basis, which rows can
> be returned by normal queries or inserted, updated, or deleted by data modification
> commands.

> To specify which rows are visible or modifiable according to a policy, an expression is
> required that returns a Boolean result. This expression will be evaluated for each row
> prior to any conditions or functions coming from the user's query.

> If no policy exists for the table, a default-deny policy is used, meaning that no rows
> are visible or can be modified.

https://www.postgresql.org/docs/current/ddl-rowsecurity.html

## Scheduling inside the database

Beat 047 draws a schedules table polled by a worker, and pg_cron alongside it as the
extension route.

> pg_cron is a simple cron-based job scheduler for PostgreSQL (10 or higher) that runs
> inside the database as an extension.

> The code in pg_cron that handles parsing and scheduling comes directly from the cron
> source code by Paul Vixie, hence the same options are supported.

https://github.com/citusdata/pg_cron

`REFRESH MATERIALIZED VIEW`, one of the six scheduled jobs listed in beat 041:
https://www.postgresql.org/docs/current/sql-refreshmaterializedview.html

## Where a schedule lives outside the repo

Beat 043 draws four real artefacts. The two whose syntax is shown on screen:

GitHub Actions `on: schedule`, with POSIX cron syntax:
https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#schedule

Kubernetes `CronJob`:
https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/

## The outbox pattern

Beats 089 to 091.

> The solution is for the service that sends the message to first store the message in the
> database as part of the transaction that updates the business entities.

> A separate process then sends the messages to the message broker.

> Messages are guaranteed to be sent if and only if the database transaction commits.

Chris Richardson, Transactional Outbox:
https://microservices.io/patterns/data/transactional-outbox.html

## Vacuum and dead tuples

Beat 105 draws dead tuples accumulating in a queue table while the live row count stays
flat, which is the documented consequence of high churn rather than an invented symptom.

> In PostgreSQL, an UPDATE or DELETE of a row does not immediately remove the old version
> of the row. This approach is necessary to gain the benefits of multiversion concurrency
> control. The row version must be reclaimed if it is no longer needed.

https://www.postgresql.org/docs/current/routine-vacuuming.html

## Transactions

The bracket drawn in beats 080, 086 and 087, and its all-or-nothing end state.

> A transaction is said to be atomic: from the point of view of other transactions, it
> either happens completely or not at all.

https://www.postgresql.org/docs/current/tutorial-transactions.html

## The marks on screen

Every logo drawn in this video is real geometry from the simple-icons package, by way of
`channels/codinghorizon/src/shorts-kit/logos.ts`. The marks used are PostgreSQL, Redis,
RabbitMQ, Apache Kafka, MongoDB, Elasticsearch, OpenSearch, Qdrant, Temporal, Docker,
GitHub Actions and Kubernetes. Two products the script names, BullMQ and Amazon SQS, have
no mark in that package, so they are set as named tiles rather than approximated.

https://github.com/simple-icons/simple-icons

## Not checked

- The script's central argument, that AI coding agents will move the default backend stack
  toward Postgres, is a prediction about how developers will build in future. It is the
  author's thesis and it is not something that can be sourced. It is presented as an
  argument on screen rather than as a measured trend, and no adoption figure, survey or
  usage statistic is shown anywhere in the video.
- Every schema, query result and table row drawn in this video is a worked example written
  for the shot. The jobs table, the schedules table, the outbox table and the search
  results are illustrations of the documented features above, not observations of a real
  system.
- The comparative statements about when a dedicated broker, search engine, document store
  or distributed scheduler is the better choice are engineering judgement, stated as such
  by the script. They are not benchmarked here and no throughput or scale threshold is put
  on screen.
{% endraw %}
