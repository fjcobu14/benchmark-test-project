# Redis Persistence Reference

## Overview

Redis is an in-memory data structure store that offers persistence mechanisms to ensure data durability. According to the Redis Wikipedia article, persistence can be achieved through two primary methods.

## Persistence Methods

### 1. RDB Snapshotting

The dataset is asynchronously transferred from memory to disk at regular intervals as a binary dump, using the Redis RDB Dump File Format. This method provides point-in-time snapshots.

### 2. AOF (Append Only File) Journaling

A record of each operation that modifies the dataset is added to an append-only file in a background process. Introduced in Redis version 1.1, this is generally considered the safer approach. Redis can rewrite the append-only file in the background to avoid indefinite growth of the journal.

## Default Behavior

By default, Redis writes data to a file system at least every two seconds. In the case of a complete system failure on default settings, only a few seconds of data will be lost.

## Source

- Wikipedia: Redis - Persistence section
- Redis official documentation: https://redis.io/about/
