# Asyncio Mastery

## Asyncio Fundamentals

- Event Loop – central dispatcher that runs coroutines, handles I/O, and schedules callbacks.
- Coroutines – defined with `async def` and awaited with `await`.
- Tasks – scheduled coroutines created via `asyncio.create_task()`; allow concurrent execution.
- Synchronization Primitives – `asyncio.Lock`, `Event`, `Queue`, `Semaphore` for safe shared‑state access.
- Running Code – `asyncio.run()` (Python 3.7+), `await` inside other coroutines, or low‑level loop methods.
- When to Use – high‑concurrency I/O‑bound workloads (web services, network clients, database access) where many connections are idle.

## Key Python 3.12 Improvements

- Socket write optimisation – avoids unnecessary copies and uses `sendmsg()` when available.
- Eager task factory – `asyncio.eager_task_factory()` / `asyncio.create_eager_task_factory()` gives 2×‑5× faster task start‑up.
- Per‑interpreter GIL (PEP 684) – sub‑interpreters with independent GILs.
- C implementation of `asyncio.current_task()` – 4×‑6× speed‑up.
- Default child watcher – `PidfdChildWatcher` on Linux when `os.pidfd_open()` is available.
- `asyncio.run()` loop factory – new `loop_factory` parameter.
- Performance benchmarks – up to **75 % speed‑up** for common async patterns vs Python 3.11.

## Guidelines

1. Keep the critical path I/O‑bound; off‑load CPU‑heavy work to threads or processes.
2. Prefer high‑level async APIs (`aiohttp`, `asyncpg`, etc.).
3. Use `asyncio.Queue` and locks to coordinate workers.
4. Profile with `python -X perf` or `sys.monitoring` (PEP 669).
5. For CPU‑bound sections, consider `asyncio.to_thread`.
