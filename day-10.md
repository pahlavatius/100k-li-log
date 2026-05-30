# Day 10

  ## DNS / HTTPS
  - Glue breaks the loop when a domain uses its own nameserver name inside the same zone.
  - DoH/DoT encrypt the channel to the resolver.
  - DNSSEC validates that the DNS answer was not tampered with.
  - A certificate binds a domain name to a public key.
  - A self-signed certificate can encrypt traffic but does not provide public browser trust.
  - 401 is an auth/application-level response after the request reached the server.
  - 502/503/504 are infrastructure/service-availability style errors.

  ## API vs ABI
  - API is the interface visible to code.
  - ABI is the compatibility contract between already built binaries.
  - API changes break how code calls something.
  - ABI problems show up when built software no longer fits the runtime/system.

  ## Git overview
  - Working tree = current file changes.
  - Staging area = selected changes for the next commit.
  - Repository = local git history.
  - Commit saves into local git history.
  - Push sends commits to GitHub/remote.

  ## Runtime / VM / bytecode
  - A program is the code/artifact on disk.
  - A process is a running instance of that program.
  - Runtime is the environment/interpreter that executes the code.
  - Java bytecode is executed by the JVM, not directly by the CPU.
  - Launching the same jar twice creates two separate processes.
