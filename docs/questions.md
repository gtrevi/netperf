# Questions

The high-level reason for this repo is to answer questions that various internal and external teams have about the performance of networking across various different scenarios.
The final output of this project is a dashboard that is meant to answer these questions.
Below is a list of all the questions we could come up with that might be interesting to answer.
Eventually, a subset of these questions will be prioritized and answered by the dashboard.

> **Note** - It should be noted that even the definition of **performance** is subjective, and highly dependent on the scenario and the user. In the questions below, we try to not use this word, but instead be specific about the metric of interest (e.g. throughput, latency, CPU utilization, etc.).

## Transports

> **Note** - Considering modern day network usage is generally always secured, we measure the performance of the secure variants of the protocols (e.g. TCP/TLS, QUIC, etc.) instead of the insecure variants (e.g. TCP, UDP, etc.).

- What is the **throughput** of a given protocol (e.g. TCP/TLS, QUIC, etc.) on Windows and Linux?
    - For single connection/stream scenarios?
    - For multi-connection/stream scenarios?
        - At large scale?
    - Upload? Download?
- What is the **latency** of a given protocol (e.g. TCP/TLS, QUIC, etc.) for a request/response type exchange on Windows and Linux?
    - For single connection/stream scenarios?
    - For multi-connection/stream scenarios?
        - At large scale?
    - For multiple request/response IO sizes?
    - What do the percentile curves look like?
        - What percentiles do we care about most?
- What is the **maximum requests/sec** of a given protocol (e.g. TCP/TLS, QUIC, etc.) for a request/response type exchange on Windows and Linux?
- What is the **maximum handshakes/sec** of a given protocol (e.g. TCP/TLS, QUIC, etc.) for a request/response type exchange on Windows and Linux?

## XDP

- How does AF_XDP {bulk, small} **throughput** compare to alternatives*?
- How does AF_XDP {bulk, small, bursty} **latency** compare to alternatives*?
- How does AF_XDP **throughput/latency** scale across RSS/CPUs compared to alternatives*?
- How much does offload X improve performance? **TODO: Define metric**
- What is the overhead of XDP inspection (e.g. always return PASS) compared to a plain stack? **TODO: Define metric**
- How many **packets/sec** can XDP inspect and drop for DDoS, and how does it compare to alternatives**?
- How many **packets/sec** can XDP inspect and forward, and how does it compare to alternatives**?

**AF_XDP Alternatives**
- Windows sockets w/ IOCP
- Windows RIO w/ IOCP and polling
- Linux traditional sockets
- Linux io_uring
- Linux XDP (native (w/ and w/o zerocopy) vs generic)
- DPDK?

**XDP+eBPF Alternatives**
- Linux XDP (native (w/ and w/o zerocopy) vs generic)
- DPDK?
