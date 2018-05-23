```
ngx_worker_process_cycle
```

```
(gdb) bt
#0  ngx_epoll_process_events (cycle=0x735480, timer=18446744073709551615, 
    flags=1) at src/event/modules/ngx_epoll_module.c:802
#1  0x0000000000443095 in ngx_process_events_and_timers (cycle=0x735480)
    at src/event/ngx_event.c:242
#2  0x000000000045283f in ngx_worker_process_cycle (cycle=0x735480, data=0x0)
    at src/os/unix/ngx_process_cycle.c:750
#3  0x000000000044ee2c in ngx_spawn_process (cycle=0x735480, 
    proc=0x452758 <ngx_worker_process_cycle>, data=0x0, 
    name=0x4e3a93 "worker process", respawn=-3)
    at src/os/unix/ngx_process.c:199
#4  0x00000000004515f3 in ngx_start_worker_processes (cycle=0x735480, n=1, 
    type=-3) at src/os/unix/ngx_process_cycle.c:359
#5  0x0000000000450b99 in ngx_master_process_cycle (cycle=0x735480)
    at src/os/unix/ngx_process_cycle.c:131
#6  0x000000000040bae2 in main (argc=1, argv=0x7fffffffe558)
    at src/core/nginx.c:382


```

```
(gdb) bt
#0  ngx_http_init_connection (c=0x7ffff7f9e1d0)
    at src/http/ngx_http_request.c:220
#1  0x00000000004466b6 in ngx_event_accept (ev=0x75b8b0)
    at src/event/ngx_event_accept.c:313
#2  0x00000000004553a0 in ngx_epoll_process_events (cycle=0x735480, 
    timer=18446744073709551615, flags=1)
    at src/event/modules/ngx_epoll_module.c:902
#3  0x0000000000443095 in ngx_process_events_and_timers (cycle=0x735480)
    at src/event/ngx_event.c:242
#4  0x000000000045283f in ngx_worker_process_cycle (cycle=0x735480, data=0x0)
    at src/os/unix/ngx_process_cycle.c:750
#5  0x000000000044ee2c in ngx_spawn_process (cycle=0x735480, 
    proc=0x452758 <ngx_worker_process_cycle>, data=0x0, 
    name=0x4e3a93 "worker process", respawn=-3)
    at src/os/unix/ngx_process.c:199
#6  0x00000000004515f3 in ngx_start_worker_processes (cycle=0x735480, n=1, 
    type=-3) at src/os/unix/ngx_process_cycle.c:359
#7  0x0000000000450b99 in ngx_master_process_cycle (cycle=0x735480)
    at src/os/unix/ngx_process_cycle.c:131
#8  0x000000000040bae2 in main (argc=1, argv=0x7fffffffe558)
    at src/core/nginx.c:382

```

```
(gdb) bt
#0  write () at ../sysdeps/unix/syscall-template.S:84
#1  0x00000000004707c5 in ngx_write_fd (fd=4, buf=0x739820, n=178)
    at src/os/unix/ngx_files.h:147
#2  0x00000000004712c3 in ngx_http_log_write (r=0x744500, log=0x753210, 
    buf=0x739820 "127.0.0.1 - - [24/May/2018:00:43:07 +0800] \"GET / HTTP/1.1\" 304 0 \"-\" \"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.167 Safari/537.36\"\n", len=178)
    at src/http/modules/ngx_http_log_module.c:427
#3  0x00000000004711cb in ngx_http_log_handler (r=0x744500)
    at src/http/modules/ngx_http_log_module.c:398
#4  0x000000000046ce48 in ngx_http_log_request (r=0x744500)
    at src/http/ngx_http_request.c:3566
#5  0x000000000046cc9e in ngx_http_free_request (r=0x744500, rc=0)
    at src/http/ngx_http_request.c:3513
#6  0x000000000046b964 in ngx_http_set_keepalive (r=0x744500)
    at src/http/ngx_http_request.c:2967
#7  0x000000000046ae35 in ngx_http_finalize_connection (r=0x744500)
    at src/http/ngx_http_request.c:2618
#8  0x000000000046a2e5 in ngx_http_finalize_request (r=0x744500, rc=-4)
    at src/http/ngx_http_request.c:2325
#9  0x000000000045bc67 in ngx_http_core_content_phase (r=0x744500, ph=0x757420)
    at src/http/ngx_http_core_module.c:1179
#10 0x000000000045afb6 in ngx_http_core_run_phases (r=0x744500)
---Type <return> to continue, or q <return> to quit---
    at src/http/ngx_http_core_module.c:858
#11 0x000000000045af23 in ngx_http_handler (r=0x744500)
    at src/http/ngx_http_core_module.c:841
#12 0x0000000000469a6e in ngx_http_process_request (r=0x744500)
    at src/http/ngx_http_request.c:1952
#13 0x000000000046864e in ngx_http_process_request_headers (rev=0x75b970)
    at src/http/ngx_http_request.c:1379
#14 0x00000000004679f9 in ngx_http_process_request_line (rev=0x75b970)
    at src/http/ngx_http_request.c:1052
#15 0x00000000004670fb in ngx_http_wait_request_handler (rev=0x75b970)
    at src/http/ngx_http_request.c:510
#16 0x00000000004553a0 in ngx_epoll_process_events (cycle=0x735480, 
    timer=60000, flags=1) at src/event/modules/ngx_epoll_module.c:902
#17 0x0000000000443095 in ngx_process_events_and_timers (cycle=0x735480)
    at src/event/ngx_event.c:242
#18 0x000000000045283f in ngx_worker_process_cycle (cycle=0x735480, data=0x0)
    at src/os/unix/ngx_process_cycle.c:750
#19 0x000000000044ee2c in ngx_spawn_process (cycle=0x735480, 
    proc=0x452758 <ngx_worker_process_cycle>, data=0x0, 
    name=0x4e3a93 "worker process", respawn=-3)
    at src/os/unix/ngx_process.c:199
#20 0x00000000004515f3 in ngx_start_worker_processes (cycle=0x735480, n=1, 
    type=-3) at src/os/unix/ngx_process_cycle.c:359
---Type <return> to continue, or q <return> to quit---
#21 0x0000000000450b99 in ngx_master_process_cycle (cycle=0x735480)
    at src/os/unix/ngx_process_cycle.c:131
#22 0x000000000040bae2 in main (argc=1, argv=0x7fffffffe558)
    at src/core/nginx.c:382

```
