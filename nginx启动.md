#nginx 启动

`main 函数`

首先main 函数在`src/core/nginx.c` 上面

然后, 看main 函数

```c
int ngx_cdecl
main(int argc, char *const *argv)
{
    ...
    cycle = ngx_init_cycle(&init_cycle);
    ...
    ngx_master_process_cycle(cycle);
    return 0;
}
```
main 函数主要是初始化一些线程池 log 等等,然后最后调用`ngx_master_process_cycle`
