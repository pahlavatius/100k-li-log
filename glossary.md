# Glossary — DevOps fundamentals

  > Personal glossary, growing daily. Terms in English (writing practice).

  ## Days 1-3 — Hardware, OS, Process

  ### Process
  A running instance of a program in RAM. Has its own PID (Process ID), virtual address space, and state. One program can produce many processes (e.g., several Chrome windows).

  ### Program
  A static file on disk containing instructions and metadata. Becomes a process only when loaded into memory by `exec()`.

  ### Kernel
  Privileged OS code running in CPU ring 0. The sole arbiter of all hardware access — user-space programs cannot touch RAM, disk, or network directly; they request services through syscalls.

  ### Syscall
  The interface user-space programs use to ask the kernel for privileged actions (read a file, allocate memory, open a network socket). Triggered by a special CPU instruction (`syscall` on x86_64).

  ### Ring 0 / Ring 3
  Hardware-enforced CPU privilege levels. Ring 0 = kernel mode (full access), Ring 3 = user mode (restricted). Attempting a privileged instruction in Ring 3 triggers a General Protection Fault → process killed.

  ### Cache line
  The fixed-size block (typically 64 bytes) that the CPU reads from RAM at once. Reading data sequentially is much faster than random access because each line brings 8-16 elements at no extra cost.

  ### Virtual memory
  Abstraction giving each process its own virtual address space (up to 256 TB on x86_64). Translated to physical RAM addresses by the MMU (Memory Management Unit) on every memory access. Provides isolation between processes and lazy allocation.

  ### ELF (Executable and Linkable Format)
  Linux executable file format. Contains an ELF header, section headers (for the linker), program headers (for the loader), and the actual code/data sections (`.text`, `.rodata`, `.data`, `.bss`).

  ### `.bss` segment
  Memory area for uninitialized global variables. Occupies 0 bytes in the executable file — only a metadata note "reserve N bytes of zeros at load time". Allocated as anonymous pages at process startup.

  ### Page fault
  CPU exception triggered when a process accesses a virtual address whose page isn't currently in physical RAM. The kernel handles it by loading the page from disk (file-backed) or allocating a fresh zero page (anonymous), then resuming the process.
