# LoopusBrowser

> LoopusBrowser is currently in Beta. Parts of the source code may be released progressively as the project evolves. At this stage, only released binary files are publicly available; the complete source code is not currently open source.

LoopusBrowser is a high-performance Windows fingerprint browser manager designed for creating, maintaining, and operating multiple isolated browser identities.

It is more than a multi-browser launcher. LoopusBrowser treats the browser Profile, fingerprint configuration, network route, extensions, browser engine, and runtime state as one unified identity system, helping users maintain multiple long-lived browser environments with greater consistency and control.

## Core Advantages

### Native Rust Architecture

LoopusBrowser uses Rust for its core application logic, browser runtime, process management, and data services, with Tauri providing the Windows desktop shell.

Rust's native compilation, low runtime overhead, memory safety, and efficient concurrency model provide:

- Lower memory usage for the management layer
- Faster application startup
- Efficient process and file operations
- Better long-running stability
- A stronger foundation for managing multiple environments in parallel

The Tauri shell uses the system WebView2 runtime instead of shipping another complete Chromium runtime for the application interface. This keeps the desktop manager smaller and reduces its baseline resource consumption.

The resource usage of individual browser environments still depends on web pages, extensions, proxy conditions, and browser engine versions. LoopusBrowser keeps the management layer lightweight and uses controlled concurrency to prevent resource usage from growing unpredictably.

### Persistent Browser Identities

Each browser environment has its own:

- Profile and browsing data
- Cookies, Local Storage, and IndexedDB
- Fingerprint configuration and revision history
- Network and proxy configuration
- Browser extensions
- Browser engine version

Environments can be preserved, duplicated, backed up, and restored, allowing users to continue using the same browser identity after application updates, engine upgrades, or system restarts.

### Consistent Fingerprint and Network Management

LoopusBrowser does not simply expose a large collection of fingerprint flags. It manages fingerprint, network, and browser data as a connected system.

Network-aware configuration can be used to determine or assist with:

- Locale and language
- Time zone
- Platform
- Viewport size
- WebRTC policy
- Browser launch parameters

After the first launch, LoopusBrowser can inspect the actual browser runtime and create an identity snapshot, making it possible to verify whether the requested configuration is actually active.

### Efficient and Controlled Multi-Environment Operation

LoopusBrowser uses an event-driven browser lifecycle and provides:

- Isolated browser processes
- OS-level Profile locks
- Windows Job Object ownership
- CDP readiness detection
- Crash and unexpected-exit synchronization
- Configurable parallel launch limits
- Bounded proxy health checks
- Shared engine download tasks

This architecture is designed for managing dozens or more long-lived browser environments while avoiding uncontrolled CPU, memory, and disk usage caused by unlimited process creation.

### Verifiable Browser Engine Management

LoopusBrowser supports Stable, Canary, and pinned browser engine versions with:

- Resumable downloads
- SHA-256 verification
- Startup smoke tests
- Safe extraction
- Atomic activation
- Version rollback
- Interrupted-operation recovery
- No forced engine switching for running environments

Engine updates become a verifiable and recoverable version-management process instead of an irreversible file replacement.

### Secure Isolation and Recovery

Different users and browser environments use physically separated data roots and local databases.

Proxy credentials, sessions, and sensitive data are protected using Windows Credential Manager, DPAPI, and encrypted backup mechanisms. Environment restoration is performed through staging and verification before being committed, preventing existing identities from being overwritten accidentally.

## Main Features

- Create, edit, duplicate, archive, and restore browser environments
- Stable, fixed-seed, and random-per-launch fingerprint modes
- HTTP, SOCKS5, and managed proxy pools
- Proxy authentication, batch import, exit-IP, and latency checks
- Extension import, permission review, hashing, and assignment
- Headed and headless browser modes
- Stable, Canary, and pinned browser engine versions
- Encrypted environment backup and restore
- Browser process lifecycle management
- Signed application updates and release verification
- Native Windows desktop experience

## Beta Status

LoopusBrowser is currently in Beta. Features, performance, and compatibility are still being actively improved.

The public repository currently provides:

- Windows installers
- Portable builds or other released binaries
- Release notes
- File hashes and signature information

Released versions are currently available for free. The source code is not publicly available at this time, and the scope of future source releases will be determined progressively as the project develops.

LoopusBrowser does not guarantee anonymity or bypassing any website's security, risk-control, or access policies. Users are responsible for complying with applicable laws and the terms of the websites and services they use.
