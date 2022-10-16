## php-signal

一款捕捉系统信号安全退出进程的任务

### usage

```php
$class = new class extends \HongXunPan\Signal\SignalJob {
//    protected $signals = [1];
    public function doJob()
    {
        sleep(3);
    }
};

$class->setStdLogStatus(true);
$class->loop();
```

输出

```bash
[root@7ee7e1d16bd9 php-signal]## php test.php 
pid = 11628
20221017 01:49:44 loop start...
20221017 01:49:47 loop end
20221017 01:49:47 loop start...
20221017 01:49:50 loop end
20221017 01:49:50 loop start...
20221017 01:49:53 loop end
20221017 01:49:53 loop start...
20221017 01:49:56 loop end
20221017 01:49:56 loop start...
20221017 01:49:59 loop end
20221017 01:49:59 loop start...
^C20221017 01:49:59 receive signal: 2     //when receive signal from linux
20221017 01:49:59 loop end
20221017 01:49:59 safe quit after job done
[root@7ee7e1d16bd9 php-signal]## 
```

* 其他结束进程方法 `kill -int pid`
详细见 `kill -l`

### extends

 - 重写 `protected $signals;` 以实现接收指定信号
 - 重写 `function doJob()` 实现常驻进程任务逻辑

### more 

实现守护进程的方法

- supervisor
- systemd

## update-log

## 参考资料

https://juejin.cn/post/6862458728675803150