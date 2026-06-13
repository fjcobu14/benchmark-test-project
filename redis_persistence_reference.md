# Redis Persistence Reference

## Overview

Redis typically holds the entire dataset in memory. Persistence in Redis can be achieved through two different methods, as described in the Persistence section of the Redis Wikipedia article.

## Persistence Approaches

### 1. Snapshotting (RDB)

The dataset is asynchronously transferred from memory to disk at regular intervals as a binary dump, using the Redis RDB Dump File Format. This method provides point-in-time snapshots of the dataset.

### 2. Journaling (AOF — Append Only File)

A record of each operation that modifies the dataset is added to an append-only file (AOF) in a background process. Redis can rewrite the append-only file in the background to avoid indefinite growth of the journal. Journaling is generally considered the safer approach.

**Journaling was introduced in Redis version 1.1.**

## Default Write Interval

By default, Redis writes data to a file system **at least every two seconds**. More or less robust options are available if needed. In the case of a complete system failure on default settings, only a few seconds of data will be lost.

## Source

- Wikipedia: Redis — Persistence section (https://en.wikipedia.org/wiki/Redis#Persistence)
