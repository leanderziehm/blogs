# Errors



## Application Code Errors:

#### 1. Reference and memory-related errors

These are the closest relatives to “null pointer errors.”

* **Null / None reference access**
  * Java: `NullPointerException`
  * Python: `AttributeError` when calling on `None`
  * TypeScript: often `Cannot read properties of undefined`
* **Use-after-free / dangling references** (less visible in managed languages, more in low-level systems languages)
* **Undefined / uninitialized variables**

These happen when code assumes an object exists but it doesn’t.

***

#### 2. Type and coercion errors

Each language enforces type rules differently, but all can fail here.

* Wrong type passed into function
* Unexpected implicit conversion
* Missing property on object

Examples:

* TypeScript catches many at compile time, but still allows runtime `any` escapes
* Python is dynamic, so errors appear at runtime
* Java enforces strict typing but can still fail with generics or casts

Typical result: “type mismatch”, “cannot cast”, or runtime attribute errors.

***

#### 3. Logic errors (silent failures)

These are the most dangerous because the program runs—but does the wrong thing.

* Incorrect conditions (`if`, `switch`)
* Off-by-one errors in loops
* Wrong assumptions about data
* Broken business rules

No crash is required; the system just produces incorrect results.

***

#### 4. Concurrency and timing errors

Very common in modern applications.

* Race conditions (two processes modify shared state)
* Deadlocks (threads waiting forever on each other)
* Data inconsistency due to timing
* Async misuse (especially in JavaScript/TypeScript systems)

These are hard to reproduce because they depend on timing.

***

#### 5. Resource exhaustion errors

System-level failures due to limits being reached:

* Memory leaks or out-of-memory crashes
* Stack overflow from deep recursion
* Too many open files / sockets
* CPU overload (infinite loops or heavy computation)

Java often throws `OutOfMemoryError`, Python raises `MemoryError`.

***

#### 6. I/O and external system failures

Your code is fine—but the world outside isn’t.

* File not found / permission denied
* Network timeout / DNS failure
* Database connection failure
* API returning unexpected format or status

These are especially common in distributed systems.

***

#### 7. Configuration and environment errors

Code depends heavily on setup:

* Missing environment variables
* Wrong config file values
* Dependency version mismatch
* Incorrect runtime settings (JVM options, Python env, Node version)

Often shows up only in production.

***

#### 8. Serialization and data format errors

When systems exchange data:

* Invalid JSON / malformed input
* Schema mismatch (old vs new API version)
* Deserialization failures
* Encoding issues (UTF-8 problems)

Common in microservices and APIs.

***

#### 9. Dependency and integration failures

Modern apps rely on many libraries:

* Broken third-party library updates
* Deprecated functions
* Conflicting dependency versions
* API changes in external services

These errors often appear after upgrades.

***

#### 10. Security and permission-related failures

Not always “crashes,” but still internal failures:

* Unauthorized access errors
* Permission denied
* Authentication token expiry
* Role-based access violations





***



### Internal-Software Errors:

* runtime erros, logic errors, failed exception handeling, memory leaks
* Incompatible versions of dependencies

### Network Errors:

* dns, firewall, proxy, vpn, routing issues, connection refused

### System Errors:

* incompatible version of dependencies, outdated os version, driver conflicts, permissions error.  (failed updates, corrupted system files)

### Hardware Errors:

failing hard drives, overheating CPUs, or faulty RAM, power supply failure



**Hardware failure**

**Software failure**

**Human fault error**

**`External/environmental impact on hardware failure or unavailability`**
