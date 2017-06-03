# php 共享锁的实现

- `DatabaseLock` 数据库方式的共享锁
- `FileLock` 文件加锁的方式实现
- `SemaphoreLock` 基于信号量（是系统提供的一种原子操作）的方式实现。需php编译时 `--enable-sysvsem`
- `MemcacheLock` 基于memcache实现

> 参考自： http://www.jb51.net/article/94878.htm


## 安装

- composer

```json
{
    "require": {
        "inhere/lock": "dev-master"
    }
}
```

- 直接拉取

```bash
git clone https://git.oschina.net/inhere/php-lock.git // git@osc
git clone https://github.com/inhere/php-lock.git // github
```

## 使用

```php
use inhere\lock\Lock;

$locker = new Lock([
    'driver' => '', // allow: File Database Memcache Semaphore
    'tmpDir' => '/tmp', // tmp path, if use FileLock
]);

$key = 'op1';

if ($locker->lock($key)) {
    // do something ...
    
    $locker->unlock($key);
}

```

## License

MIT
