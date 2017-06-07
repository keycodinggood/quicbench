Introduction
================

Benchmark tool for HTTP/SPDY over QUIC protocol written in Go. Originally forked from cmpxchg16's [Gobench](https://github.com/cmpxchg16/gobench).


Getting Started
================

## Dependency

  * [quic-go](https://github.com/lucas-clemente/quic-go)

## Usage

1. run some quic supported server. You may use server implementation bundled in [quic-go](https://github.com/lucas-clemente/quic-go)
   or toy server implementation in Chromium [here](http://www.chromium.org/quic/playing-with-quic)
   
2. run quicbench for HTTPS GET

   ```$>go run quicbench.go -u https://localhost:6121/ -k=true -c 50 -r=10 -t 10```
   
3. run quicbench for HTTP POST

   ```$>go run quicbench.go -u https://localhost/ -k=true -c 50 -r=10 -t 10 -d /tmp/post```

Notes
================

1. build a binary: 

    ```$>go build gobench.go```
    
    Then you can run the command:
    
    ```bash
    $>./quicbench -u https://localhost:6121/ -k=true -c 50 -r=10 -t 10
    ```
    
2. Because it's a test tool, in HTTPS the ceritificate verification is insecure
3. use Go >= 1.7 (quci-go support Go 1.7+)
4. quicbench creates one QUIC connection for each client and just create new stream for every request.
   If you want to create QUIC connection for every request, use -qk=false option.

Help
================

```go run gobench.go --help```

License
================

Licensed under the New BSD License.

Author
================

Originally written by Uri Shamay (shamayuri@gmail.com)

QUIC protocol adopted by Brian Sung-Jin Hong (sungjinhong@devsisters.com) and Joonsung Lee (joonsung@devsisters.com)

Added QUIC protocol with [quic-go](https://github.com/lucas-clemente/quic-go) supported by yongboy@gmail.com :)) 
