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
