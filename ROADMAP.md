# Roadmap

## Phase 1: Stability Improvements (Completed)
- [x] **Flow Control Implementation**: Introduced a backpressure mechanism in the C++ server to prevent OOM crashes during high-speed downloads.
    - Added high/low water marks (2MB/512KB) for send buffers.
    - Implemented pausing/resuming of socket reads based on buffer usage.
    - Added feedback loop from named pipe sender to SOCKS proxy.

## Phase 2: Protocol & Performance Tuning (Planned)
- [ ] **SMB Pipe Optimization**: Implement Nagle's algorithm or batching for SMB writes to reduce RTT overhead.
- [ ] **Client-Side Optimization**: Review and optimize Python client's buffer handling and threading model.

## Phase 3: Modernization & Portability (Planned)
- [ ] **Golang Client Rewrite**: Replace the Python client with a single, static binary written in Go.
    - **Goal**: Eliminate Python/Impacket dependencies for easier deployment in restricted environments.
    - **Key Libraries**: `go-smb2` (SMB/Named Pipes), `go-msrpc` (RPC/WMI), `go-socks5` (Proxy), `cobra` (CLI).
    - **Benefit**: Cross-platform (Windows/Linux/macOS), single binary, high concurrency performance.

## Phase 4: Long-term Architecture
- [ ] **Application-Layer Flow Control**: Implement a sliding window mechanism in the custom `rpc2socks` protocol.
- [ ] **Async I/O (IOCP)**: Migrate C++ server to use I/O Completion Ports for better scalability on Windows.
