# CVE-2023-44487 (HTTP/2 Rapid Reset)
There are some examples in this repo which are not tested completely to analyse the impact, but I just wanted to perform the concept of this attack `(starting many streams and immediately sending RST_STREAM frame to avoid reaching MAX_CONCURRENT_STREAMS)`.

# H2SpaceX
I use [H2SpaceX](https://github.com/nxenon/h2spacex) low level HTTP/2 library which I created for exploiting Single Packet Attack

# Examples

- There are 2 examples:
  - [Example 1](cve-2023-44487-example1.py)
    - Sending 10000 GET requests and sending RESET STREAM frames after each request immediately
  - [Example 2](cve-2023-44487-example2.py)
    - Sending 100000 POST requests (with single packet attack technique) which causes server to wait for last byte, and then sending RESET STREAM frame after each request
    - This Example also uses threading to open more H2 connections.

# Read & Do More

- Do More
  - You can read more about using [H2SpaceX](https://github.com/nxenon/h2spacex) to send raw frames.
  - [Quick Start Example for Single Packet Attack](https://github.com/nxenon/h2spacex/wiki/Quick-Start-Examples)
  - [H2Frames](https://github.com/nxenon/h2spacex/blob/main/src/h2spacex/h2_frames.py)
- Read More
  - [HTTP/2 Rapid Reset Attack by Cloudflare](https://blog.cloudflare.com/technical-breakdown-http2-rapid-reset-ddos-attack/)
  - [Lots of References at cve.org](https://www.cve.org/CVERecord?id=CVE-2023-44487)
