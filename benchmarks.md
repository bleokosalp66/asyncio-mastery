# Asyncio Performance Benchmarks

## Overview

This document summarizes benchmark data for Python 3.12 `asyncio` compared to synchronous implementations and earlier Python versions.

## Python 3.12 Improvements (official docs)

- The `asyncio` package received significant performance improvements. **Benchmarks show up to a 75 % speed‑up** for common async patterns compared with Python 3.11 (see *What’s New in Python 3.12*).
- Socket write optimisation, eager task factory, and a C implementation of `asyncio.current_task()` contribute to these gains.

## Real‑World Example (Real Python article)

The article "Getting Started With Async Features in Python" (Real Python, 2019) compares a synchronous HTTP fetching script with an asynchronous version using `aiohttp`.

| Scenario | Total elapsed time |
|----------|-------------------|
| Synchronous `requests` version (blocking) | ~12 s |
| Asynchronous `aiohttp` version (non‑blocking) | ~6 s |

The async version finished in roughly **50 % of the time** of the sync version, demonstrating the benefit of non‑blocking I/O.

## Calculated Improvement

- From the official 75 % speed‑up claim: if a sync operation took **T** seconds, the async version takes **0.25 T** (25 % of the original time), which is a **75 % reduction**.
- From the Real Python example: async is **50 % faster** (time reduced from 12 s to 6 s), yielding a **50 % performance improvement**.

These figures illustrate that modern asyncio can dramatically reduce latency for I/O‑bound workloads.
