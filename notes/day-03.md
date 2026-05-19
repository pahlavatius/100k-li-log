# Day 3 — ELF, loader, process memory image

  **Date:** 2026-05-19

  ## Topics covered

  - ELF file format: sections (`.text`, `.rodata`, `.data`, `.bss`) vs segments
  - `exec()` syscall: how a file on disk becomes a living process
  - Process memory image: stack (RW, down) / heap (RW, up) / `.bss` / `.data` / `.rodata` / `.text`
  - Virtual memory basics (MMU, page tables, 256 TB virtual address space)
  - Lazy loading via page faults
  - Page sharing + Copy-on-Write (COW)

  ## Key insights

  - `.bss` takes 0 bytes on disk because zero-initialized data doesn't need to be stored — kernel allocates zero pages at load time.
  - Page faults are how lazy loading happens: virtual memory pretends pages are there until first access, then kernel loads them on demand.
  - Page sharing + COW: identical RO pages are shared across processes; RW pages are shared until first write triggers a private copy.

  ## Tools to try in WSL2

  - `readelf -h /bin/ls` — ELF header
  - `readelf -l /bin/ls` — program headers (segments for loader)
  - `readelf -S /bin/ls` — section headers
  - `cat /proc/<pid>/maps` — live memory map of running process
  - `/usr/bin/time -v ls /home` — page fault counters

  ## Stumbles to revisit

  - Cache line + prefetcher mechanism (sequential vs random array access)
  - General Protection Fault — the "CPU is the gatekeeper, not the program asking permission" model
  - `.bss` = 0 bytes on disk (caught again in quiz Q2 — needs reinforcement)

  ## Concepts to read on own later

  - TLB (Translation Lookaside Buffer) details
  - W^X principle / NX-bit / DEP — hardware enforcement of "no executable data"
  - Strip command and stripped binaries in production
